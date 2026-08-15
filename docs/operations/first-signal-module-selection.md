# First Signal Module Selection

## Decision to make

The first Midas module should prove that a verified signal can become a ranked opportunity and then a real conversation or transaction. We are comparing **Expansion Radar** with **Hiring-Friction Radar**.

## Summary comparison

| Criterion | Expansion Radar | Hiring-Friction Radar |
|---|---|---|
| Signal definition | New site, facility, production capacity, acquisition, geographic entry, investment, or related corporate event. | Persistent vacancy, repeated posting, scarce-skill hiring, hiring acceleration, or a role that implies operational pressure. |
| Buyer or recipient | Contractors, equipment suppliers, logistics providers, recruiters, implementation firms, facilities providers, and other specialists. | Specialist recruiters, staffing firms, outsourced operators, training providers, consultants, and workforce platforms. |
| Evidence quality | Strong when sourced from filings, official announcements, permits, procurement notices, or company statements. | Stronger at company level when job-posting history is available; public macro data is not sufficient by itself. |
| Transaction clarity | Moderate to high, but the next need may vary by expansion type. | High for recruiting and staffing; moderate for adjacent services. |
| Initial data friction | Moderate. Public-company filings and company announcements are accessible, but coverage is uneven. | Low to moderate if using a permitted job-posting or sales-intelligence source; higher if building historical persistence from scratch. |
| Breadth of future modules | Very broad: facilities, logistics, equipment, contractors, IT, recruiting, and finance. | Broad within workforce and adjacent operational services, but narrower outside them. |
| Human interpretation required | High: expansion does not always reveal the exact purchase. | Moderate: role, persistence, seniority, and department can create a clearer need hypothesis. |
| Delegation potential | Good after evidence rules and industry playbooks exist. | Very good for research and first-pass qualification. |
| Speed to first test | Moderate. A small set can be manually assembled from public events. | Potentially faster if a compliant data source is available. |
| Long-term asset potential | High: an event-to-need intelligence layer can serve many provider categories. | High within talent and workforce markets; could evolve into a hiring-friction index or specialist routing network. |

## Important evidence distinction

The BLS Job Openings and Labor Turnover Survey produces monthly and annual estimates of job openings, hires, and separations for the nation and state-level estimates at the total nonfarm industry level [1]. That makes JOLTS useful for macro context, but not sufficient by itself for identifying a particular company with a persistent vacancy.

By contrast, SEC EDGAR provides company filing histories and extracted XBRL data through public APIs, with filing data updated as submissions are disseminated [2]. That makes EDGAR a credible evidence source for public-company expansion events, although the universe is limited to disclosed public-company activity.

The implication is practical: **hiring-friction radar needs a company-level job-posting source or a carefully bounded manual research process; expansion radar can begin from public filings and company-event evidence without requiring a specialized labor-market data license.**

## Recommendation

Start with **Expansion Radar as the first core module**, but design the schema so Hiring-Friction Radar can be added as the second module without changing the engine.

The reason is not that expansion is automatically easier. Hiring friction may produce a cleaner first transaction for a specialist recruiter. The reason is that Expansion Radar better tests the long-term Midas thesis: one signal can route into many categories of provider, allowing us to learn the information-to-transaction architecture rather than locking the company into one staffing niche immediately.

## First expansion module scope

The first module should not attempt to detect every expansion event. It should focus on a constrained wedge:

> **Publicly evidenced expansion or facility-investment events involving companies in one selected geography and one selected industry, routed to one or two provider categories.**

Candidate event types:

- New facility or site announcement.
- Acquisition or geographic entry.
- Capacity expansion or major capital investment.
- New production line or operating footprint.
- Publicly announced logistics, technology, or infrastructure project.

Candidate provider categories:

- Industrial contractors and maintenance providers.
- Specialized equipment or automation suppliers.
- Logistics and warehousing providers.
- Recruiting and staffing firms for expansion-related hiring.
- Implementation or compliance providers connected to the new operation.

## Minimum viable signal record

A signal cannot enter the working queue unless it contains:

1. The company and relevant entity or site.
2. A source URL or evidence reference.
3. The observed date and freshness state.
4. A factual description of the event.
5. A clearly stated transaction hypothesis.
6. A geographic and industry fit assessment.
7. A human owner and next action.

## First validation experiment

Create a small manually verified set of expansion events, rank them using the Midas score, and route them to one provider category. The experiment should measure whether the event produces a credible conversation, not merely whether the record can be collected.

Success should be judged by:

| Test | Evidence of success |
|---|---|
| Signal accuracy | A second reviewer agrees the event is real, current, and relevant. |
| Need hypothesis | A provider can explain why the event plausibly creates a need. |
| Routing quality | At least one provider is a credible fit and has capacity or interest. |
| Conversation quality | The buyer-side or provider-side conversation is relevant enough to produce a next step. |
| Workflow quality | Another operator can execute the process from source to routed opportunity. |
| Learning value | Outcomes reveal which event types, industries, and provider categories deserve more attention. |

## Second module path

Once the expansion loop works, add Hiring-Friction Radar as a plug-in module with the same core objects: signal, evidence, account, contact, score, owner, interaction, opportunity, and outcome. The only changes should be signal-specific evidence fields such as role family, posting date, repost count, department, seniority, and persistence.

## References

[1]: https://www.bls.gov/jlt/ "U.S. Bureau of Labor Statistics — Job Openings and Labor Turnover Survey"

[2]: https://www.sec.gov/search-filings/edgar-application-programming-interfaces "U.S. Securities and Exchange Commission — EDGAR Application Programming Interfaces"
