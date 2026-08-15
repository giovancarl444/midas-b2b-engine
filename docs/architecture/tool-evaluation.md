# Midas Commercial Signal Terminal — Initial Tool Evaluation

## Scope

This is an initial capability comparison, not a final procurement decision. Vendor capabilities, pricing, limits, integrations, and terms change. Before production use, we will test the actual workflows and confirm current commercial and data-processing terms.

## Current recommendation

Use **Make as the orchestration candidate**, a flexible CRM or database as the canonical record, one signal/enrichment platform for the first module, and a visual command center that exposes operational movement. Do not let the signal platform or outreach tool become the only place where the business history exists.

## Candidate comparison

| Layer | Candidate | What the official material indicates | Initial role in Midas | Main concern |
|---|---|---|---|---|
| Orchestration | Make | Visual workflows, app/data/AI connections, 3,000+ integrations, monitoring and management of automations, and sales/operations use cases are presented on its official site [1]. | Connect signal intake, enrichment, record updates, tasks, notifications, CRM sync, and error handling. | Usage costs, scenario complexity, rate limits, vendor dependence, and the need for disciplined logging. |
| System of record | HubSpot CRM | Official material describes contact management, communication history, deals, tasks, pipeline management, reporting dashboards, and a free CRM tier [2]. | Possible canonical CRM for accounts, contacts, interactions, opportunities, and client relationships. | May be more platform than needed early; data model and export/API limits must be tested. |
| Flexible operating database / command center | Airtable | Official material positions Airtable as a structured, collaborative data and workflow platform with integrations, real-time shared data, and app-building capabilities [3]. | Possible first command center or canonical operating database for signals, queues, SOP views, and dashboards. | Must decide whether CRM functions belong here or in a dedicated CRM; avoid two competing sources of truth. |
| Internal application layer | Retool | Official material describes internal software connected to databases, APIs, and LLMs, with workflows and governance capabilities [4]. | Later command center when the workflow has proven itself and requires custom operator screens. | Premature complexity before the schema and transaction loop are validated. |
| Signals and enrichment | Clay | Official material describes signal tracking, data-provider marketplace access, waterfall enrichment, AI research agents, workflows, CRM enrichment, and outbound use cases [5]. | Strong candidate for the intelligence layer when we need multiple sources and repeatable signal research. | Cost, data-provider dependence, credit usage, data rights, and the need to preserve source evidence outside the platform. |
| B2B data and engagement | Apollo | Official material describes a combined B2B database, enrichment, AI/multichannel campaigns, workflow automation, CRM integrations, and deal execution features [6]. | Possible lean alternative that reduces the number of separate tools for the first outreach experiment. | May encourage a generic sales workflow rather than the deeper signal-to-transaction model; verify coverage and data quality for the chosen vertical. |

## Architecture options

### Option A: Lean system-builder pilot

Use Make for orchestration, Airtable or HubSpot for the first canonical record, one signal source, and CRM or approved engagement tooling for controlled outreach. This is the fastest way to produce a visible board and test one signal loop.

### Option B: Intelligence-first pilot

Use Make for orchestration, Clay for signal and enrichment workflows, HubSpot for relationship and opportunity records, and Airtable or a later internal application for the command center. This gives more intelligence-layer power but adds cost and configuration before the signal hypothesis is proven.

### Option C: All-in-one prospecting pilot

Use Apollo for database, enrichment, outreach, and initial pipeline functions, with Make for notifications and external synchronization. This may be the fastest route to campaign activity but risks making Apollo the de facto operating system before we know which data and workflow should be proprietary.

## Initial choice

For Midas, the current preference is **Option A with an intelligence-first schema**:

1. Define our own signal, account, contact, provider, opportunity, interaction, outcome, and suppression records.
2. Use Make as the connective layer and document every scenario.
3. Start with the most flexible low-friction system of record that supports the schema and exports it reliably.
4. Add Clay or Apollo only for the signal/enrichment capability the first module actually needs.
5. Add a richer custom dashboard only after the workflow creates enough activity to justify it.

This preserves speed without confusing a vendor’s product model with the Midas model.

## Evaluation tests before committing

| Test | Pass condition |
|---|---|
| Record creation | A verified signal creates or updates one canonical account and opportunity without duplicates. |
| Evidence preservation | Source URL, timestamp, summary, and confidence survive every sync. |
| Human queue | A researcher can see the next action, owner, and deadline without opening multiple systems. |
| Notification | A meaningful event triggers one useful notification, not a noisy stream. |
| Error handling | Failed enrichment or API calls create a visible exception and retry path. |
| Suppression | A do-not-contact or do-not-route state blocks downstream engagement and is auditable. |
| Outcome feedback | Meeting or transaction outcomes return to the canonical record and update reporting. |
| Export | Full records and workflow history can be exported in a usable format. |
| Cost visibility | We can estimate cost per verified signal, qualified opportunity, and transaction. |

## References

[1]: https://www.make.com/en "Make — Visual AI automation platform"

[2]: https://www.hubspot.com/products/crm "HubSpot — Free CRM Software"

[3]: https://www.airtable.com/ "Airtable — AI workflows, apps, and structured data"

[4]: https://retool.com/ "Retool — Internal software and workflows"

[5]: https://www.clay.com/ "Clay — Data infrastructure, signals, agents, and GTM workflows"

[6]: https://www.apollo.io/ "Apollo — AI sales platform, data, enrichment, and engagement"
