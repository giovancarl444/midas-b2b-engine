# Midas Commercial Signal Terminal — Canonical Data Schema

## Why this exists

Tools will change. The Midas schema is the durable layer. Every selected platform must either store or synchronize these fields, and every automation must preserve the relationships between them.

## 1. Signal

A **signal** is a time-bound, evidence-backed market event or condition that may predict a commercial need.

| Field | Type | Required | Meaning |
|---|---|---:|---|
| `signal_id` | ID | Yes | Stable internal identifier. |
| `signal_type` | Enum | Yes | Expansion, hiring_friction, procurement, technology_change, risk, capacity, transaction, or future type. |
| `signal_subtype` | Text | No | More precise classification, such as new facility or repeated vacancy. |
| `observed_at` | Date/time | Yes | When the event was observed. |
| `source_name` | Text | Yes | Source or provider that surfaced it. |
| `source_url` | URL | Yes | Evidence location where available. |
| `evidence_summary` | Text | Yes | Short factual description without unsupported inference. |
| `freshness_days` | Number | Yes | Days since observation. |
| `confidence_score` | Number | Yes | Confidence that the signal is genuine and current. |
| `transaction_hypothesis` | Text | Yes | What need or transaction this may predict. |
| `account_id` | Relation | No | Linked account after resolution. |
| `status` | Enum | Yes | New, verified, rejected, stale, or converted. |
| `owner_id` | Relation | No | Person responsible for the next action. |
| `next_action` | Text | No | Concrete next step. |
| `next_action_due` | Date/time | No | Deadline for the next step. |

## 2. Account

An **account** is the organization, facility, buyer-side entity, or provider-side entity connected to one or more signals.

| Field | Type | Required | Meaning |
|---|---|---:|---|
| `account_id` | ID | Yes | Stable internal identifier. |
| `account_name` | Text | Yes | Canonical organization name. |
| `domain` | URL/text | No | Primary website or domain. |
| `account_type` | Enum | Yes | Buyer, provider, partner, client, or other. |
| `industry` | Text | Yes | Working category. |
| `geography` | Text | Yes | Relevant operating region. |
| `size_band` | Enum | No | Working size category. |
| `fit_score` | Number | Yes | Fit against the current module or campaign. |
| `capacity_or_need` | Text | No | Known demand or supply context. |
| `verification_status` | Enum | Yes | Unverified, partially verified, verified, or rejected. |
| `suppression_status` | Enum | Yes | Clear, do_not_contact, do_not_route, or review. |
| `owner_id` | Relation | No | Internal owner. |
| `last_reviewed_at` | Date/time | No | Last human review. |

## 3. Contact or responsible role

A **contact** is a person or role associated with an account. The system should support role-level records where a named person is not yet verified.

Required operational fields include `contact_id`, `account_id`, `name_or_role`, `title`, `business_contact_path`, `verification_status`, `source`, `last_verified_at`, `relationship_status`, `suppression_status`, and `owner_id`.

Personal data must be handled according to the applicable jurisdiction, purpose, source, retention rule, and objection or opt-out state. The system should record the state and source rather than relying on memory.

## 4. Provider

A **provider** is a company or specialist capable of fulfilling a buyer-side need.

Required fields include `provider_id`, `account_id`, `offer_summary`, `service_area`, `minimum_transaction_size`, `capacity_status`, `proof_points`, `response_standard`, `quality_rating`, `owner_id`, and `relationship_status`.

The provider record is what lets Midas move from prospect identification to actual transaction routing. A signal is not commercially complete until the system can identify who may be able to act on it.

## 5. Opportunity

An **opportunity** is a ranked potential transaction created from one or more signals and connected to a buyer, provider, or client.

| Field | Type | Required | Meaning |
|---|---|---:|---|
| `opportunity_id` | ID | Yes | Stable internal identifier. |
| `signal_ids` | Relation list | Yes | Evidence chain behind the opportunity. |
| `buyer_account_id` | Relation | Yes | Entity with the need or demand. |
| `provider_account_id` | Relation | No | Potential solver or supplier. |
| `transaction_type` | Enum | Yes | Meeting, referral, project, recruitment, procurement, partnership, acquisition, or future type. |
| `need_summary` | Text | Yes | Plain-language description of the problem or opportunity. |
| `urgency` | Enum | Yes | Low, medium, high, or time-critical. |
| `value_band` | Enum | Yes | Working economic range, not a promise. |
| `fit_score` | Number | Yes | Buyer/provider fit. |
| `evidence_score` | Number | Yes | Strength and freshness of evidence. |
| `routing_score` | Number | Yes | Confidence that a suitable party can be routed. |
| `priority_score` | Number | Yes | Composite work priority. |
| `stage` | Enum | Yes | New, reviewed, routed, engaged, qualified, booked, held, proposal, won, lost, nurture, or suppressed. |
| `owner_id` | Relation | Yes | Single accountable owner. |
| `next_action` | Text | Yes | Concrete next step. |
| `next_action_due` | Date/time | Yes | Deadline. |
| `outcome_reason` | Text | No | Why the opportunity advanced, stalled, or closed. |
| `estimated_value` | Currency | No | Working estimate. |
| `realized_value` | Currency | No | Recorded value when known. |

## 6. Interaction

An **interaction** records any meaningful activity: email, call, reply, meeting, introduction, referral, proposal, or handoff.

Required fields include `interaction_id`, `opportunity_id`, `timestamp`, `channel`, `actor`, `counterparty`, `classification`, `summary`, `next_action`, `owner_id`, and `evidence_link` where available.

## 7. Suppression and trust record

A **suppression record** prevents further outreach, routing, or processing where required. It should include the affected entity, scope, reason, source, effective date, review date, and responsible owner.

This is not a secondary compliance table. It is part of the trust layer and must be checked before any automated engagement or routing action.

## 8. Scoring model

The first scoring model should remain interpretable:

```text
Priority score =
  evidence strength × 0.30
+ freshness × 0.20
+ account fit × 0.20
+ transaction value potential × 0.15
+ urgency × 0.10
+ routing confidence × 0.05
```

The weights are starting assumptions, not truths. They should be revised only after outcome data shows which factors predict held meetings, proposals, or completed transactions.

## 9. Required automation safeguards

Every automation touching these records must define duplicate handling, failure behavior, audit logging, and human ownership. A record should never silently disappear because a third-party API changed, an enrichment failed, or a webhook was delayed.

The minimum pattern is:

```text
Receive event
→ validate payload
→ resolve duplicate
→ attach evidence
→ update canonical record
→ calculate or queue score
→ assign owner
→ notify only if action is needed
→ log success or failure
```

## 10. First pilot schema

The first pilot does not need every field above. It must, however, capture enough information to test whether a signal predicts a transaction:

- Signal type and source.
- Evidence URL and observed date.
- Account and geography.
- Buyer or responsible role.
- Need or transaction hypothesis.
- Fit, evidence, freshness, and priority scores.
- Owner, stage, next action, and deadline.
- Outreach or introduction status.
- Outcome and estimated or realized value.

Anything not needed for that learning loop should be deferred until the workflow proves its value.
