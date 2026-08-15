# ADR 0001: Choose a System-Builder Stack as the Initial Direction

**Status:** Accepted for exploration

**Date:** 2026-08-15

## Context

The business is intended to turn commercial signals into transactions and eventually own information, distribution, talent deployment, and trust/workflow infrastructure. A narrow point solution or a single all-in-one sales platform may produce activity quickly, but it may not give us the flexibility, visibility, or data ownership required for a long-lived operating system.

The first priority is therefore a connective layer that can move signals, records, tasks, notifications, and outcomes across a modular stack. The system also needs a visible command center and a schema that remains ours even if vendors change.

## Decision

We will explore a **system-builder stack** with the following structure:

1. An orchestration layer as the connective tissue, with Make as the leading candidate.
2. A flexible CRM or database as the canonical system of record.
3. A signal and enrichment layer beginning with one narrow signal module.
4. A controlled engagement layer for outreach or introductions.
5. Human review for judgment-heavy steps such as verification, qualification, escalation, and trust-sensitive interactions.
6. A visual command center for Signal Radar, Live Pipeline, Activity and Exceptions, and Economics.
7. Repository-backed documentation, exports, and backup procedures.

## Alternatives considered

### All-in-one sales platform first
This may be faster to start, but it risks hiding the signal-to-transaction model inside a vendor workflow and may make the eventual intelligence asset less portable.

### Custom application immediately
This offers maximum control but would front-load development before the signal, transaction, and workflow hypotheses are validated.

### Spreadsheet-only operation
This is useful for a small exploratory sample but will not adequately express automation state, ownership, audit history, error handling, or live operating activity once the loop grows.

## Consequences

We accept more initial architecture work in exchange for modularity, visibility, and future ownership of the operating schema. We will avoid overbuilding by validating one signal-to-transaction loop before adding broad automation or many integrations.

## Review trigger

Revisit this decision if the first pilot shows that an integrated platform can support the required signal evidence, workflow states, human review, exports, and dashboard visibility without materially limiting our long-term asset strategy.
