# First Signal-to-Provider Workflow

## Objective

Turn one verified food-and-beverage manufacturing expansion event into a ranked, human-reviewed provider opportunity without overbuilding the system.

## 1. Minimum viable record

```yaml
signal_id: MIDAS-EXP-0001
signal_type: facility_expansion
signal_subtype: new_or_expanded_production_site
observed_at: YYYY-MM-DD
source_name: official_company_announcement
source_url: https://example.com/source
account_name: Example Foods Inc.
account_domain: https://example.com
facility_location: City, State
industry_subsector: beverage_manufacturing
geography_fit: true
evidence_summary: "Factual description of the announced event."
transaction_hypothesis: "Expansion may create industrial refrigeration, HVAC, or process-utility requirements."
provider_category: industrial_refrigeration_hvac_process_utilities
freshness_score: 0
confidence_score: 0
account_fit_score: 0
transaction_value_score: 0
urgency_score: 0
routing_confidence_score: 0
priority_score: 0
status: new
owner: unassigned
next_action: verify_source_and_account
next_action_due: YYYY-MM-DD
suppression_status: clear
outcome: unknown
```

## 2. Workflow states

| State | Responsible role | Required action | Exit criteria |
|---|---|---|---|
| New | Intake automation | Create record, deduplicate, preserve source and timestamp. | Record passes basic schema validation. |
| Evidence review | Research operator | Open source, summarize facts, confirm date and location, reject unsupported inference. | Signal marked verified or rejected. |
| Account resolution | Research operator | Resolve company, facility, industry, and geography. | Account is linked and fit is scored. |
| Provider hypothesis | Strategist | Identify the plausible facility need and provider category. | Transaction hypothesis is written in plain language. |
| Provider matching | Research operator | Find providers with geography, capability, proof, and capacity fit. | At least one provider is a credible candidate. |
| Human approval | Strategist or quality owner | Review evidence, score, and proposed route. | Opportunity is approved, held, or rejected. |
| Engagement | SDR or relationship owner | Use an approved message or introduction path; record every meaningful response. | Conversation, refusal, silence, or suppression is recorded. |
| Qualification | SDR or strategist | Confirm relevance, timing, fit, and appropriate next step. | Qualified opportunity, nurture, or closed record. |
| Handoff | Account owner | Route the opportunity with context, evidence, and expectations. | Receiving party acknowledges or meeting is booked. |
| Outcome | Account owner | Capture held, proposal, won, lost, nurture, or disqualified result. | Outcome is stored and feedback is available. |

## 3. Initial scoring

Use a transparent 0–10 score for each dimension:

| Dimension | Question |
|---|---|
| Evidence | Is the event supported by a clear, current, credible source? |
| Freshness | How recently was the event observed or updated? |
| Account fit | Does the company and facility match our chosen industry and geography? |
| Transaction value | Could this plausibly create a meaningful project or recurring service need? |
| Urgency | Is there a timeline, deadline, construction phase, production launch, or visible operational pressure? |
| Routing confidence | Can we identify at least one provider with relevant capability and coverage? |

Starting formula:

```text
Priority =
  Evidence × 0.25
+ Freshness × 0.20
+ Account fit × 0.20
+ Transaction value × 0.15
+ Urgency × 0.10
+ Routing confidence × 0.10
```

Do not treat the formula as objective truth. It is a decision aid that must be recalibrated against real outcomes.

## 4. Provider qualification standard

A provider enters the active routing pool only when the record shows:

- Industrial rather than residential capability.
- Service coverage for the relevant facility location.
- Relevant experience in food, beverage, manufacturing, cold chain, or process utilities where possible.
- A credible response owner.
- A defined minimum project or engagement size.
- No unresolved quality or trust issue.

The provider is not promised a job. The provider is offered a qualified opportunity or conversation subject to the buyer’s needs and procurement process.

## 5. Make-style automation scenarios

### Scenario A: Signal intake

```text
Trigger: new approved signal source record
→ validate required fields
→ normalize company and source fields
→ search for duplicate source/account/event
→ create or update signal
→ attach evidence metadata
→ assign research task
→ notify only if priority exceeds review threshold
→ log result
```

### Scenario B: Review completion

```text
Trigger: signal marked verified
→ resolve or create account
→ calculate initial score
→ create provider-hypothesis task
→ set due date
→ move record to evidence-reviewed queue
→ log result
```

### Scenario C: Provider routing

```text
Trigger: opportunity approved for routing
→ check suppression and relationship state
→ identify matching provider candidates
→ create provider review task
→ prepare evidence-backed context
→ require human approval before engagement
→ record route and owner
```

### Scenario D: Reply or response handling

```text
Trigger: reply or response received
→ attach to opportunity
→ classify response
→ suppress if objection or opt-out
→ escalate technical/legal/complaint cases
→ create qualification task for positive responses
→ notify owner only when action is needed
→ log result
```

### Scenario E: Outcome feedback

```text
Trigger: meeting, handoff, proposal, or close outcome entered
→ update opportunity and provider history
→ record outcome reason and value
→ recalculate signal/provider performance
→ identify stale or failed assumptions
→ produce weekly learning report
```

## 6. First pilot operating rules

The first pilot should be intentionally human-heavy:

- Manually verify every signal before it reaches the active queue.
- Manually approve every provider route and first message.
- Use a small sample rather than maximizing volume.
- Capture source evidence and reason for every decision.
- Record negative outcomes, not only wins.
- Keep provider and buyer-side identities distinct.
- Never let an automation silently overwrite a human decision.

## 7. First dashboard cards

The first command center should show:

| Card | Metric or queue |
|---|---|
| New signals | Count by type and age. |
| Verification queue | Unreviewed signals with owner and deadline. |
| Top opportunities | Highest priority records with next action. |
| Provider match queue | Signals awaiting a qualified provider. |
| Engagement queue | Replies, introductions, and follow-ups requiring action. |
| Suppression and exceptions | Opt-outs, complaints, failed automations, duplicates, and unresolved data issues. |
| Outcomes | Held conversations, proposals, won/lost, nurture, and disqualified. |
| Economics | Estimated value, realized value, labor, data, and orchestration cost. |

## 8. Pilot success criteria

The first loop is successful if:

1. Another operator can create and verify a signal using this template.
2. The system can preserve evidence and prevent duplicates.
3. A ranked record can be matched to a credible provider.
4. A human can review and approve the route without losing context.
5. The receiving party gives a commercially meaningful response or clear disqualification reason.
6. The result feeds back into the signal, provider, and workflow records.
7. We can explain the cost and time required for one verified, routed opportunity.
