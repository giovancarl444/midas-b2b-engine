# Midas B2B Engine

## Midas Commercial Signal Terminal

Midas is the operating system for turning commercially meaningful market signals into ranked, actionable transaction opportunities.

The initial thesis is simple:

> **Signal → evidence → account → contact → conversation → qualified opportunity → trusted transaction.**

The repository is the canonical workspace for the business. It holds the strategy, operating model, data schema, workflow definitions, experiments, decisions, dashboard specifications, backups, and eventually the implementation.

## Current direction

We are beginning with a **system-builder stack** rather than a narrow tool stack. The orchestration layer is the first priority because it should connect signals, enrichment, CRM records, outreach, human handling, notifications, reporting, and future channels. Make is the leading candidate for the connective-tissue layer, subject to validation of cost, integrations, reliability, and data ownership.

The first signal modules under consideration are:

1. **Expansion signals:** new facilities, geographic expansion, production growth, investment, and related operational events.
2. **Hiring-friction signals:** persistent vacancies, repeated job postings, scarce-skill hiring, and staffing pressure.

These are starting modules, not permanent limits. The long-term product may evolve into a commercial signal terminal, proprietary intelligence layer, referral network, marketplace, or workflow platform.

## Operating principles

**Start with a transaction, not a dataset.** Information is valuable only when it changes who should be contacted, what should be offered, when action should occur, or how work should be routed.

**Own the schema before owning the software.** Tools can change. Our durable asset is the model of signals, accounts, contacts, evidence, scores, messages, conversations, opportunities, outcomes, and economics.

**Automate repetition; preserve judgment.** Machines and operators may collect, enrich, classify, notify, and route. Strategic positioning, quality standards, exceptions, trust, and important relationships remain human-controlled.

**Treat quality and compliance as product features.** Every opportunity should have evidence, an owner, a next action, and a clear suppression or opt-out path where outreach is involved.

**Build the service as a laboratory.** Early client work should teach us which signals predict real transactions. Repeated learning should become owned infrastructure.

## Repository map

| Path | Purpose |
|---|---|
| `docs/architecture/` | System diagrams, component decisions, data flows, and integration boundaries. |
| `docs/operations/` | SOPs, qualification rules, campaign procedures, QA, and handoff workflows. |
| `docs/decisions/` | Decision records explaining why the stack and business direction changed. |
| `data/templates/` | Import templates, schemas, scoring sheets, and sample non-sensitive records. |
| `backups/` | Export manifests and recovery documentation. Never commit secrets or private credentials. |

## Immediate objective

Build a visible first operating system that can answer, at any moment:

- What new signals entered the system?
- Which signals have been verified and ranked?
- Which accounts and contacts require action?
- Which conversations are waiting for human handling?
- What opportunities are booked, held, advancing, or stuck?
- Which clients, providers, channels, and signal types are producing value?
- Where are quality, compliance, or delivery risks accumulating?

## Status

The repository is newly initialized. The next work is to finalize the schema and workflow, compare the first candidate tools, create the implementation checklist, and build the smallest useful signal-to-transaction loop before adding complexity.
