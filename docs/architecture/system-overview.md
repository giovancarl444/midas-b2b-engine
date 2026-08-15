# Midas Commercial Signal Terminal — System Overview

## 1. Purpose

Midas turns market events into ranked and actionable transaction opportunities. The system is designed to begin as an internal operating engine and later support client delivery, provider routing, intelligence products, and trusted workflow infrastructure.

## 2. Canonical flow

```text
Signal source
    ↓
Signal intake
    ↓
Evidence and freshness check
    ↓
Account enrichment
    ↓
Contact identification
    ↓
Fit / urgency / transaction scoring
    ↓
Human review
    ↓
Approved route and message
    ↓
Outreach or warm introduction
    ↓
Reply / response handling
    ↓
Qualification
    ↓
Meeting or transaction handoff
    ↓
Outcome capture
    ↓
Score and workflow improvement
```

## 3. Core records

| Record | Meaning | Required fields |
|---|---|---|
| Signal | A market event or condition that may predict a need | Type, source, source URL or evidence, observed date, freshness, geography, account, confidence, trigger description. |
| Account | The company, organization, facility, or buyer-side entity | Name, domain, industry, location, size band, fit score, status, owner, suppression state. |
| Contact | A person or role associated with an account | Name, role, business contact path, verification date, relationship status, consent/objection state where relevant. |
| Provider | The company or specialist capable of fulfilling a need | Offer, geography, capacity, minimum transaction size, proof, owner, quality rating. |
| Opportunity | A ranked potential transaction | Need, signal, buyer, provider, transaction type, value band, urgency, score, stage, owner, next action. |
| Interaction | Any outreach, reply, call, meeting, handoff, or decision | Time, channel, sender, recipient, summary, classification, next action, outcome. |
| Outcome | What happened after the opportunity was worked | Held, disqualified, proposal, won, lost, nurture, reason, value, attribution confidence. |
| Suppression | A record that must not be contacted or must be excluded | Entity, reason, source, effective date, review date, scope, owner. |

## 4. State machine

| Stage | Entry condition | Exit condition |
|---|---|---|
| New signal | A candidate event enters from a source | Evidence is reviewed or the signal is rejected. |
| Verified signal | Evidence and freshness pass the minimum standard | Account and transaction hypothesis are created. |
| Account qualified | Account fits the chosen market and geography | Contact or responsible role is identified. |
| Contact identified | Plausible current business contact path exists | Message or introduction is approved. |
| Active | Outreach or introduction is underway | Reply, rejection, silence, or opt-out occurs. |
| Human triage | Response requires classification or judgment | Qualified, escalated, suppressed, or closed. |
| Qualified opportunity | Need and relevance meet the defined standard | Meeting, proposal, referral, or transaction handoff occurs. |
| Meeting / handoff | Buyer and provider or relevant parties are connected | Outcome is recorded. |
| Outcome | Commercial result is known or a nurture decision is made | Feedback updates scoring, provider quality, and workflow rules. |

## 5. Stack philosophy

The first architecture should be modular:

| Component | Role | Design principle |
|---|---|---|
| Orchestration | Move records, trigger actions, notify owners, and handle routine workflows | Make is the leading candidate; workflows must be exportable and documented. |
| System of record | Store canonical records and history | Select a flexible CRM or database with reliable export and API access. |
| Signal and enrichment layer | Discover, enrich, verify, and score opportunities | Start with one signal module and preserve source evidence. |
| Engagement layer | Send approved outreach or manage introductions | Use controlled volume, honest messaging, reply handling, and suppression logic. |
| Human operations | Research, review, triage, qualify, and escalate | Human judgment is explicit, trained, and auditable. |
| Command center | Make activity, bottlenecks, exceptions, and economics visible | Build views around decisions, not vanity metrics. |
| Backup and governance | Preserve data, configuration, decisions, and recovery instructions | No secrets in Git; export critical data and maintain an inventory. |

## 6. First command-center views

### Signal Radar

Shows new signals by type, freshness, source quality, geography, score, and assigned owner. Its job is to answer: **what entered the system and what deserves attention first?**

### Live Pipeline

Shows accounts and opportunities by stage, owner, next action, age, and estimated value. Its job is to answer: **what is moving, stuck, or neglected?**

### Activity and Exceptions

Shows reply queues, stale records, failed automations, unverified contacts, opt-outs, complaints, and unresolved handoffs. Its job is to answer: **where can quality or trust break?**

### Economics

Shows activity cost, labor allocation, conversion by signal type, qualified opportunities, provider/client value, and contribution. Its job is to answer: **which parts of the machine deserve more investment?**

## 7. Initial integration boundaries

The system should not make every tool a source of truth. External tools may generate events or perform actions, but canonical records and outcomes must be synchronized back to the selected system of record.

Every automation should have:

- A clear trigger.
- A defined input and output schema.
- An idempotency or duplicate-handling rule.
- An error path and human owner.
- A log or audit trail.
- A suppression and opt-out check where outreach is involved.
- A documented export or recovery path.

## 8. First implementation principle

Do not build the entire terminal before proving one loop. The first useful slice is:

> **One signal module → verified records → ranked queue → human review → one controlled route to a buyer or provider → outcome captured.**

Expansion and hiring-friction signals are the initial candidates. The first module should be chosen by evidence quality, transaction clarity, speed of validation, and ability to delegate the workflow—not by the apparent size of the market alone.
