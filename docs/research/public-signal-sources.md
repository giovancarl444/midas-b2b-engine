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
