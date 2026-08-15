# Midas Commercial Signal Terminal — Working Roadmap

This roadmap is intentionally changeable. The order is optimized for learning and visibility rather than for building the largest possible stack.

## Phase 0 — Establish the operating workspace

| Status | Task | Completion criterion |
|---|---|---|
| Done | Create the canonical GitHub repository workspace | Repository cloned and initialized locally. |
| Done | Add repository structure and README | Core folders and principles documented. |
| Next | Commit the initial operating documents | Main branch contains the first version of the workspace. |
| Next | Define backup and secret-handling rules | Recovery process exists; no credentials are committed. |

## Phase 1 — Define the business objects and state machine

| Status | Task | Completion criterion |
|---|---|---|
| Next | Define the signal schema | Every signal has source, timestamp, evidence, type, geography, account, confidence, and score. |
| Next | Define account and contact schema | Account, buyer, role, contact path, fit, and verification state are explicit. |
| Next | Define opportunity schema | Need, provider, transaction type, value range, urgency, owner, and next action are explicit. |
| Next | Define workflow stages | Signal-to-transaction stages and transition rules are documented. |
| Next | Define qualification standard | A qualified opportunity is measurable and auditable. |

## Phase 2 — Choose the first system-builder stack

| Status | Task | Completion criterion |
|---|---|---|
| Next | Validate Make as orchestration layer | Required triggers, actions, webhooks, notifications, and error handling are tested. |
| Next | Compare flexible database/CRM options | One system of record is selected for the first pilot. |
| Next | Compare signal and enrichment options | First signal source and enrichment method are selected. |
| Next | Compare outreach and reply-handling options | Controlled outreach and human triage path are selected. |
| Next | Select visual command-center approach | CRM dashboards, Airtable Interfaces, Retool, or a small custom view is chosen. |
| Next | Define data ownership and export paths | We can export the full operating history without vendor lock-in. |

## Phase 3 — Build the first signal loop

| Status | Task | Completion criterion |
|---|---|---|
| Next | Choose one initial signal module | Expansion or hiring-friction module has a written scope. |
| Next | Create a small verified signal set | Sample records contain evidence and can be reviewed by another operator. |
| Next | Score and rank signals | Ranking produces a prioritized work queue. |
| Next | Route qualified records to a human owner | Assignment and deadlines appear visibly in the workflow. |
| Next | Run a controlled outreach experiment | Messages, replies, opt-outs, and outcomes are tracked. |
| Next | Capture feedback from the receiving party | Meeting, opportunity, disqualification, and value data feed back into scoring. |

## Phase 4 — Make activity visible

| Status | Task | Completion criterion |
|---|---|---|
| Next | Build Signal Radar view | New, verified, ranked, and aging signals are visible. |
| Next | Build Live Pipeline view | Every active opportunity shows owner, stage, next action, and age. |
| Next | Build Activity and Exceptions view | Reply queues, failed automations, opt-outs, complaints, and stale records are visible. |
| Next | Build Economics view | Cost, activity, qualified opportunities, revenue potential, and contribution are visible. |
| Next | Add notifications | Important events reach the chosen internal channel without creating noise. |

## Phase 5 — Delegate and scale carefully

| Status | Task | Completion criterion |
|---|---|---|
| Next | Write research SOP | Another operator can verify and score a signal. |
| Next | Write reply-triage SOP | Another operator can classify, escalate, suppress, or book correctly. |
| Next | Write quality-control SOP | Meeting and opportunity quality are audited consistently. |
| Next | Create client/provider onboarding | A new relationship can enter the system without founder improvisation. |
| Next | Measure unit economics by signal and client | We know which parts deserve more capital and labor. |
| Next | Add warmer brand channels | Referral, content, partnerships, and inbound are layered onto the core system. |

## Priority rule

When in doubt, choose the task that most quickly answers one of these questions:

1. Does the signal predict a real commercial need?
2. Can the opportunity be routed to a capable provider or buyer?
3. Can another person operate the step without quality collapse?
4. Can the outcome be measured and fed back into the system?

A task that does not improve one of those four answers is secondary until the core loop works.
