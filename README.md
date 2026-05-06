# Financial Close Automation

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An open-source, AI-native financial close platform that automates month-end reconciliations, checklists, and SOX evidence for the 70%+ of companies still closing the books with spreadsheets and email.

Financial Close Automation is a candidate open-source platform for controllers, CFOs, and finance transformation leaders who need to shrink the close cycle, reduce SOX compliance risk, and produce auditor-ready evidence without paying enterprise licence fees. It targets the gap between expensive incumbents like BlackLine ($50K–$300K+/year) and basic ERP period-close primitives in tools like ERPNext, by combining checklist management, automated reconciliation, and LLM-driven flux commentary in a single self-hostable system.

---

## Why Financial Close Automation?

- **Incumbent pricing locks out the mid-market.** BlackLine runs $50,000–$300,000+ per year with implementation costs that match software costs; FloQast charges roughly $125/user/month plus AutoRec add-ons. Most companies under $1B revenue cannot justify either.
- **No mature open-source alternative exists.** ERPNext (GPL-3.0) provides only basic period-end primitives — closing vouchers, manual bank reconciliation, depreciation — with no checklist management, no automated matching, and no AI assistance.
- **Legacy AI is bolted on, not built in.** BlackLine's Verity suite sits atop a 15-year-old platform; Trintech's agentic AI was announced only in April 2026. An AI-native architecture from day one can deliver continuous close monitoring and exception judgment that retrofitted platforms struggle to match.
- **Vendor uncertainty at the top of the market.** BlackLine's stock declined 35% YoY by 2026 with an activist investor on the board, signalling that product investment priorities may shift away from customer needs.
- **SOX evidence assembly is still manual.** Collecting reconciliation sign-offs, journal entry approvals, and segregation-of-duty logs into auditor-ready packages remains error-prone across the category — a clear automation target.

---

## Key Features

### Close Management & Workflow

- Close checklist with task ownership, due dates, dependency tracking, and status across the accounting team
- Multi-level review and approval workflow for reconciliations and journal entries with electronic sign-off
- Period locking via closing voucher to prevent posting to closed accounting periods
- Close calendar view showing all tasks, owners, and dependencies across the cycle
- Manager review dashboard with completion percentage by account type and team member

### Reconciliation & Journal Entries

- Account reconciliation with GL balances auto-populated from the connected ERP
- Configurable transaction matching with auto-certify rules for low-risk items
- Journal entry preparation, approval, and posting with full audit trail
- Side-by-side GL balance vs. subledger/bank balance workspace with matched and unmatched items
- Variance / flux analysis: automated period-over-period comparison with exception highlighting

### SOX Compliance & Audit Trail

- Timestamped audit log of every action with user attribution and before/after values
- SOX-ready control evidence log capturing reconciliation sign-offs and journal entry approvals
- Segregation-of-duties enforcement within the review and approval workflow
- Document attachment for supporting evidence on each reconciliation and journal entry

### AI-Assisted Close

- LLM-generated draft flux commentary using GL detail, budget, and prior-period data
- ML-based journal entry anomaly detection that flags unusual entries before they pass review
- Continuous close monitoring: real-time anomaly detection on GL transactions throughout the month
- AI agent that organises control evidence into auditor-ready packages from existing audit trails
- Agentic exception handling for common reconciliation cases (timing differences, rounding, recurring items) with documented rationale

### ERP Integration

- Connectors for ERPNext, NetSuite, and QuickBooks for real-time GL data
- REST APIs for custom data feeds, reporting extracts, and workflow embedding
- Supporting document storage integration for reconciliation evidence

---

## AI-Native Advantage

Unlike incumbents whose AI features are layered onto rules-based engines architected over a decade ago, this project treats AI as a core component of the matching, monitoring, and evidence-assembly layers. An LLM with access to GL detail, budget, and prior-period data can draft defensible flux commentary in seconds — eliminating one of the most time-consuming manual close tasks. Agentic exception handling can apply contextual judgment to timing differences, rounding, and known recurring items to push touchless reconciliation rates well beyond what rules-based matching achieves. Continuous monitoring during the month, rather than batch processing at month-end, enables the daily continuous close that defines the 2026 finance operating model.

---

## Tech Stack & Deployment

The project targets self-hosted deployment as the primary mode, with optional managed hosting, mirroring the ERPNext / Frappe Cloud pattern. Integration is API-first via REST for ERP data feeds and workflow embedding, with native connectors planned for ERPNext, NetSuite, QuickBooks, Sage Intacct, and Dynamics 365. Outputs map to established standards including SOX (Section 302/404), PCAOB AS 2201 evidence requirements, GAAP / IFRS reconciliation conventions, the COSO control framework, and XBRL / iXBRL tagging for downstream disclosure management.

---

## Market Context

The financial close automation market is valued at approximately $5.8B in 2026 with a 12% CAGR (PMR Press Release, 2026). BlackLine and FloQast together account for roughly 30–40% of the addressed market with 4,400+ and 2,800+ customers respectively, while pricing ranges from $50,000/year at the entry tier to $300,000+ for first-year enterprise deployments. Primary buyers are Controllers and Assistant Controllers in mid-market companies ($50M–$1B revenue), CFOs concerned with SOX risk and reporting speed, and finance transformation leaders in larger enterprises driving multi-entity standardisation.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
