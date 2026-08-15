# Public Signal Source Findings

## SEC EDGAR APIs

Source: https://www.sec.gov/search-filings/edgar-application-programming-interfaces

The SEC states that `data.sec.gov` provides RESTful JSON APIs for EDGAR submissions by company and extracted XBRL data. The APIs do not require authentication or API keys for access. The submissions history and XBRL data include current filing information and are updated throughout the day as filings are disseminated. The SEC also provides nightly bulk archives.

Potential Midas use:
- Detect public-company expansion language in 8-K, 10-Q, 10-K, and related filings.
- Detect new facilities, acquisitions, geographic expansion, capital expenditure, restructuring, and other corporate-event clues.
- Preserve the filing URL, filing date, form type, company identifier, and extracted evidence in the Signal record.

Constraints:
- The signal universe is biased toward public filers and their disclosed events.
- Text interpretation still requires evidence review and should not be treated as a transaction conclusion without human validation.
- Automated access must follow the SEC's developer and privacy/security requirements.

## SAM.gov Get Opportunities Public API

Source: https://open.gsa.gov/api/get-opportunities-public-api/

The GSA documentation states that the Get Opportunities API provides published opportunity details based on request parameters. The API supports search by dates and fields such as procurement type, title, organization, place of performance, NAICS code, classification code, response deadline, set-aside, and status. Responses include fields such as title, solicitation number, posted date, type, response deadline, NAICS code, award information where available, point of contact, place of performance, and links.

The public API requires an API key, has request limits, uses pagination, and restricts the date range for certain searches. Active notices are updated daily and archived notices weekly according to the documentation.

Potential Midas use:
- Build a procurement-signal module for vendors serving government buyers.
- Identify newly posted opportunities and route them to qualified providers by NAICS, geography, set-aside, response deadline, and capability.
- Treat the response deadline as a natural urgency score.

Constraints:
- This is a narrower government-procurement wedge, not a universal expansion signal.
- The source requires credentials and has quotas, so it is not the lowest-friction first public-data experiment.
- Opportunity quality and provider qualification still require human review.

## Initial implication

Public corporate filings provide a broad, evidence-backed expansion-event source. SAM.gov provides a highly structured but narrower transaction source. For the first Midas module, expansion radar can begin with public filings and other openly accessible company-event sources; procurement radar may later become a more direct signal-to-transaction module because the opportunity and deadline are explicit.

## BLS context for food and beverage manufacturing

Source: https://www.bls.gov/opub/mlr/2026/article/feeding-the-economy-employment-growth-in-food-and-beverage-manufacturing-expected-to-continue-through-the-2024-34-decade.htm

A June 2026 BLS Monthly Labor Review article states that food and beverage manufacturing is projected to add the most jobs of any manufacturing sector from 2024 to 2034, with projected growth linked to output, population, consumer demand, and technology adoption. The article reports a projected addition of 130,000 jobs and identifies food and beverage manufacturing as the largest manufacturing sector by 2024 employment share.

This is context rather than a company-level signal. It supports the industry as a durable operating category, but Midas still needs event-level evidence such as a facility announcement, production expansion, investment, acquisition, new site, or company-specific hiring pattern before creating an opportunity.

## BLS JOLTS limitation

Source: https://www.bls.gov/jlt/

The BLS JOLTS program produces monthly and annual estimates of job openings, hires, and separations for the nation, plus state estimates at the total nonfarm industry level. This is useful for market context and later scoring calibration, but it does not identify a specific company with a persistent vacancy. Company-level Hiring-Friction Radar would require a separate permitted job-posting or company-research source.
