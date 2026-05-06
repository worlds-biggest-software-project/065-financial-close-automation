# Standards & API Reference

> Project: Financial Close Automation · Generated: 2026-05-06

## Industry Standards & Specifications

### Regulatory & Accounting Standards

**SOX — Sarbanes-Oxley Act (Sections 302 and 404)**
- Official: https://www.sarbanes-oxley-act.com/
- The primary driver of enterprise financial close automation spend. Section 302 requires CEO/CFO certification of quarterly and annual financial statements. Section 404 requires management's annual assessment of internal controls over financial reporting (ICFR). Any financial close platform targeting public companies must provide full audit trails, segregation of duties enforcement, multi-level approval workflows, and electronic sign-off capture to support SOX compliance.

**PCAOB AS 2201 — Audit of Internal Control Over Financial Reporting**
- Official: https://pcaobus.org/oversight/standards/auditing-standards/details/AS2201
- Amended standard effective December 15, 2026. Governs how external auditors audit internal controls. Close automation platforms must produce evidence packages (reconciliation sign-offs, journal entry approvals, segregation of duty logs) that satisfy Big 4 and mid-tier auditor requirements under this standard. The standard requires a top-down, risk-based assessment and mandates documented evidence of control design and operating effectiveness.

**COSO Internal Control — Integrated Framework (2013)**
- Official: https://www.coso.org/guidance-on-ic
- The recognised internal control framework required by both SEC regulations and PCAOB standards for SOX Section 404 compliance. Close automation checklists and workflow controls are typically mapped to the five COSO components: Control Environment, Risk Assessment, Control Activities, Information & Communication, and Monitoring. Any SOX-ready close platform should allow controls to be tagged against COSO components for audit evidence purposes.

**COSO ERM Framework (2017)**
- Official: https://www.coso.org/
- Enterprise Risk Management companion framework to the 2013 IC framework. Relevant for close automation platforms that extend into continuous monitoring and anomaly detection — these capabilities can be positioned as risk management controls within the COSO ERM taxonomy.

**IFRS (International Financial Reporting Standards)**
- Official: https://www.ifrs.org/
- The accounting standards followed by publicly listed companies in 140+ countries. Define what must be reconciled, how journal entries are documented, which disclosures are required, and what the financial statements must present. IFRS standards directly determine the functional requirements of close checklists for IFRS reporters.

**IFRS 18 — Presentation and Disclosure in Financial Statements**
- Official: https://www.ifrs.org/issued-standards/list-of-standards/ifrs-18-presentation-and-disclosure-in-financial-statements/
- Effective for annual periods beginning 1 January 2027 (early application permitted); replaces IAS 1. Requires new defined subtotals in the income statement (operating profit; profit before financing and income taxes) and mandates disclosures for Management-Defined Performance Measures (MPMs). Close automation systems that generate or feed into financial statement preparation will need to tag GL transactions by IFRS 18 category and capture MPMs for automated reconciliation. Retrospective restatement required.

**US GAAP — Generally Accepted Accounting Principles**
- Maintained by FASB: https://www.fasb.org/
- US accounting standards that define recording, measurement, and disclosure requirements for US domestic issuers. Close checklists for US public companies must align with GAAP recognition and disclosure obligations.

**IAS 10 / ASC 855 — Subsequent Events**
- IAS 10: https://www.ifrs.org/ · ASC 855: https://www.fasb.org/
- Standards requiring identification and disclosure of material events occurring between the balance sheet date and the date of financial statement authorisation (IFRS) or issuance (US GAAP). An AI-native close platform monitoring GL transactions post-close can flag potential subsequent events automatically, reducing a significant source of restatement risk.

---

### Data Reporting & Tagging Standards

**XBRL — eXtensible Business Reporting Language**
- Official: https://www.xbrl.org/the-standard/what/financial-statement-data/
- XML-based standard for tagging financial statement data. Required by the SEC for all domestic filer Form 10-Q and 10-K submissions since 2009. Financial close platforms that extend to disclosure management must support XBRL taxonomy tagging using the US GAAP taxonomy (FASB) or IFRS taxonomy (IFRS Foundation).

**iXBRL — Inline XBRL**
- SEC guidance: https://www.sec.gov/data-research/structured-data/inline-xbrl
- EDGAR XBRL Guide (April 2026): https://www.sec.gov/files/edgar/filer-information/specifications/xbrl-guide.pdf
- Inline XBRL embeds machine-readable XBRL tags directly within human-readable HTML financial statements, eliminating the need for separate HTML and XBRL filings. Required by the SEC for domestic filers since 2020. The EDGAR XBRL Guide (updated April 2026) provides current implementation requirements.

**ESEF — European Single Electronic Format**
- ESMA: https://www.esma.europa.eu/
- EU equivalent of iXBRL, required for consolidated IFRS financial statements of EU-listed companies. Governed by ESMA, which publishes annual taxonomy updates. The 2025 ESEF taxonomy was updated to reflect IFRS 18 and IFRS 19, supporting 2026 financial statement preparation.

**SEC EDGAR APIs**
- Data API: https://www.sec.gov/search-filings/edgar-application-programming-interfaces
- RESTful data APIs at data.sec.gov deliver JSON-formatted XBRL data from financial statements (10-Q, 10-K, 8-K, 20-F, etc.) without authentication. Useful for benchmarking, peer comparison, and validation of financial close outputs against filed data.

---

### Messaging & Bank Statement Standards

**ISO 20022 — Financial Services Universal Financial Industry Message Scheme**
- Official: https://www.iso20022.org/iso-20022
- SWIFT resources: https://www.swift.com/standards/iso-20022/iso-20022-standards
- Multi-part international standard for financial messaging, supporting XML and JSON syntaxes. The global standard for interbank payments and reporting messages. The coexistence period (supporting legacy MT messaging alongside ISO 20022) ended 22 November 2025 — ISO 20022 is now the sole standard for cross-border payments and reporting on the SWIFT network.

**ISO 20022 camt Messages — Cash Management Reporting**
- Clearstream reference: https://www.clearstream.com/resource/blob/3738792/fa564142233c781ec2c2126a54289561/swift-ug-cbpr-data.pdf
- Key messages for bank reconciliation: **camt.052** (intraday account report), **camt.053** (end-of-day statement), **camt.054** (credit/debit notification). The BankToCustomerStatement (camt.053) is the primary bank statement format for cash reconciliation in a financial close. Richer structured remittance data in ISO 20022 messages reduces unmatched items in nostro reconciliation compared to legacy MT940/MT942.

**SWIFT MT940 / MT942 (Legacy)**
- Modern Treasury reference: https://www.moderntreasury.com/learn/mt940-file
- Legacy SWIFT bank statement formats still in use by some banking systems for domestic reconciliation, though being replaced by ISO 20022 camt messages. Financial close platforms should support both formats during the multi-year transition period.

**SWIFT Instant Cash Reporting API**
- Official: https://www.swift.com/products/instant-cash-reporting-api
- Provides real-time access to corporate account balances and transactions via a secure network connection. Consolidates financial data from multiple banks into a unified ISO 20022 format, enabling continuous cash reconciliation rather than end-of-day batch processing. Highly relevant for continuous close approaches.

---

### API & Integration Specifications

**OpenAPI Specification (OAS) v3.1.1 / v3.2.0**
- Official: https://spec.openapis.org/oas/v3.1.1.html · https://spec.openapis.org/oas/v3.2.0.html
- OpenAPI Initiative: https://www.openapis.org/
- The de facto standard for documenting RESTful APIs in the financial SaaS space. OAS 3.1.0+ provides full JSON Schema Draft 2020-12 compatibility. OAS 3.2.0 (released September 2025) adds streaming media type support (SSE, JSON Lines), native QUERY HTTP method, and OAuth 2.0 Device Authorization Flow. All major financial close vendors expose REST APIs documented in OpenAPI format.

**JSON Schema Draft 2020-12**
- Official: https://json-schema.org/
- Standard for validating JSON data structures. Integrated into OpenAPI 3.1.0+. Relevant for defining and validating financial close data payloads (journal entries, reconciliations, task definitions, audit events) in API contracts.

**OAuth 2.0 / OpenID Connect**
- OAuth 2.0 RFC 6749: https://datatracker.ietf.org/doc/html/rfc6749
- OpenID Connect: https://openid.net/developers/how-connect-works/
- The universal authentication and authorisation standard for financial SaaS APIs. All major close platforms (BlackLine, FloQast, OneStream, NetSuite) use OAuth 2.0 with client credentials or authorization code flows for API access. Any open-source close automation platform must implement OAuth 2.0 to integrate with ERP systems and to serve as an identity provider for its own API.

**Model Context Protocol (MCP)**
- Official: https://modelcontextprotocol.io/docs/getting-started/intro
- Anthropic: https://www.anthropic.com/news/model-context-protocol
- Open standard connecting AI agents to external data systems and tools. Increasingly relevant to financial close as ERP vendors (Microsoft Dynamics 365, Zoho) publish MCP servers enabling AI agents to read from and write to ERP records with full audit trails. A financial close AI agent built on MCP could submit intercompany elimination workflows, trigger consolidation jobs, receive reconciliation failure summaries, and post journal entries — all through a standardised, auditable interface.

---

### Security & Compliance Frameworks

**SOC 2 Type II**
- AICPA: https://www.aicpa-cima.com/
- Reference (2026 guide): https://www.konfirmity.com/blog/soc-2-what-changed-in-2026
- Voluntary AICPA audit report that enterprise buyers require as proof of security controls. SOC 2 Type II audits evaluate whether security controls (availability, confidentiality, processing integrity, privacy) operated effectively over a 6–12 month period. Essential certification for any financial close SaaS. 2026 audits increasingly evaluate zero-trust security, continuous monitoring, and cloud-native architectures.

**GDPR — General Data Protection Regulation**
- Official: https://gdpr.eu/
- EU data protection law governing personal data of individuals in the EU. Financial close platforms processing employee data (journal entry preparers, approvers, reconciliation certifiers) must comply with GDPR. Key implications: data minimisation, right to erasure, data residency requirements for EU deployments, and documented lawful basis for processing.

**NIST Cybersecurity Framework 2.0**
- Official: https://www.nist.gov/cyberframework
- Voluntary framework for improving cybersecurity risk management. Relevant for financial close platforms targeting US government contractors or organizations with NIST compliance requirements. The 2024 update (v2.0) adds a "Govern" function addressing supply chain risk and AI governance.

---

## Similar Products — Developer Documentation & APIs

### BlackLine

- **Description:** Enterprise financial close and accounting automation platform covering reconciliations, journal entries, transaction matching, and intercompany. The market leader by customer count (4,400+ customers).
- **API Documentation:** https://developer.blackline.com/
- **Postman Guide:** https://developer.blackline.com/postman-guide
- **API Overview (Scribd):** https://www.scribd.com/document/743421081/Client-Deployment-of-the-BlackLine-Public-API-v1-7-002
- **Developer Community Reference:** https://apitracker.io/a/blackline/developers
- **Standards:** REST/JSON; OAuth 2.0 client credentials (access tokens at `https://api.blackline.com/auth/token`); TLS 1.2+ required; paginated responses using `nextLink`.
- **Authentication:** OAuth 2.0 (client credentials flow).
- **Notable:** BlackLine's SAP Core External API enables middleware integration for ERP-to-BlackLine data flows. User Management API is separately documented for SCIM-based provisioning.

---

### FloQast

- **Description:** Mid-market close management platform with checklist, automated reconciliation (AutoRec), and flux analysis. 2,800+ customers in the $50M–$1B revenue segment.
- **API Documentation:** https://developer.floqast.app/
- **External API Reference:** https://developer.floqast.app/content/api-reference/openapi
- **Controls API:** https://developer.floqast.app/content/api-reference/openapi/controls
- **Integration Ecosystem:** https://www.floqast.com/integrations
- **Tray.io automation connector:** https://tray.ai/connectors/floqast-integrations
- **Standards:** REST/JSON; API key authentication (x-api-key header); OpenAPI documented endpoints; webhooks for close status events.
- **Authentication:** API key (generated in-app, passed in `x-api-key` header).
- **Notable:** FloQast provides a sandbox environment for integration development. APIs cover GL trial balance submission, close task management, reconciliation workflow, and webhooks for event-driven integrations.

---

### Trintech Cadency

- **Description:** Enterprise financial close platform with strong workflow configurability, SOX compliance controls, and dual-platform coverage (Cadency for enterprise; Adra for mid-market). Irish-headquartered, strong EU presence.
- **Developer Portal:** https://developer.trintech.com/
- **IAM API Documentation:** https://developer.trintech.com/doc/iam-api/
- **Services API Documentation:** https://cadencyhelp.lower.trintech.com/v11.1.0/apidoc/index.html
- **Close Task API:** https://www.trintech.com/blog/simplifying-documentation-management-with-cadency-close-task-field-api/
- **Integration Overview:** https://www.trintech.com/cadency/smart-platform/smart-data/targeted-apis/
- **Workiva Connector:** https://marketplace.workiva.com/en-us/connectors/cadencyrcadencydirectr-trintech-connector
- **Standards:** REST/JSON; IAM API for SCIM-based user provisioning; Close Task Field API for bidirectional data flow.
- **Authentication:** Not publicly detailed; enterprise onboarding required for API credentials.
- **Notable:** The Close Task Field API enables data and status to flow between Cadency and external systems while maintaining configured SOX controls — useful for understanding how close task APIs should be designed.

---

### OneStream

- **Description:** Unified CPM platform combining financial close, consolidation, planning, and reporting in a single data model. Public company (NASDAQ: OS) targeting complex multi-entity enterprises.
- **API Overview Guide (PDF):** https://documentation.onestream.com/1384528/Content/PDFs/API_Overview_Guide.pdf
- **REST API Implementation Guide (PDF):** https://documentation.onestream.com/1384528/Content/PDFs/REST_API_Implementation_Guide.pdf
- **REST API Overview:** https://documentation.onestream.com/1375907/Content/REST%20API/REST%20API%20Overview.html
- **Web API Endpoints:** https://documentation.onestream.com/1375907/Content/REST%20API/OneStream%20Web%20API%20Endpoints.html
- **Financial Close Integration:** https://documentation.onestream.com/docs/Content/Financial%20Close/Integration.html
- **Standards:** REST/JSON; URL pattern `https://{Server}/OneStreamApi/api/{Service}/{Action}?api-version={version}`; OAuth 2.0; .NET/C# SDK available; platform-agnostic via JSON.
- **Authentication:** OAuth 2.0.
- **Notable:** Data Management endpoint executes Data Management Sequences for ETL/ELT workflows. Data Provider endpoint supports Cube View queries and SQL commands for financial data retrieval. Community forum provides supplemental implementation guidance.

---

### NetSuite (Oracle)

- **Description:** Cloud ERP widely used by mid-market companies ($50M–$500M revenue); primary source system for financial close data for FloQast, Numeric, and other close platforms.
- **API Integration Guide (2026):** https://satvasolutions.com/blog/netsuite-integration-guide
- **REST API Guide:** https://www.merge.dev/blog/netsuite-api
- **SuiteAnalytics Connect (JDBC/ODBC):** https://fivetran.com/docs/connectors/applications/netsuite-suiteanalytics
- **GitHub API repository:** https://github.com/api-evangelist/workday-financials
- **Standards:** SuiteTalk REST (primary modern API); SuiteQL (SQL-like query language via `/services/rest/query/v1/suiteql`); SuiteAnalytics Connect (ODBC/JDBC for bulk data); RESTlets (custom server-side scripts). The 2026.1 release expanded REST coverage toward parity with the older SOAP SuiteTalk API.
- **Authentication:** OAuth 2.0 (authorization code, client credentials, JWT grant types).
- **Notable:** SuiteQL is the preferred interface for reading trial balance, journal entry, and transaction data for close automation purposes. Financial statement close data can be extracted using SuiteQL queries over the REST endpoint for real-time GL balance population.

---

### SAP S/4HANA

- **Description:** SAP's flagship cloud and on-premise ERP; primary source system for journal entries and financial data in large enterprise financial close workflows.
- **Journal Entry Post API (SAP API Hub):** https://api.sap.com/api/JOURNALENTRYCREATEREQUESTCONFI/overview
- **SAP Help Portal — Journal Entries:** https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/3ab6e6fc510f4840a5508e126ef01e22/610d1f7204d94644950928f575782f22.html
- **Journal Entry APIs Collection (updated July 2025):** https://community.sap.com/t5/technology-blog-posts-by-sap/apis-for-journal-entries-the-collection-updated-july-2025/ba-p/13565258
- **Integration: Finance - Posting (SAP_COM_0002):** SAP Community blog reference
- **Standards:** OData (primary REST-based API for S/4HANA Cloud); BAPI/RFC (legacy on-premise integration via SAP Cloud Connector); IDoc (batch document exchange). The Journal Entry Post API is available in the Finance – Posting Integration communication scenario (SAP_COM_0002).
- **Authentication:** OAuth 2.0 (SAP Cloud); RFC/BAPI with SAP system credentials (on-premise via Cloud Connector).
- **Notable:** SAP Advanced Financial Close (AFC) is SAP's own close automation module. Third-party close platforms integrate via OData APIs to pull GL balances and post approved journal entries back to S/4HANA.

---

### Workday Financials

- **Description:** Cloud HCM and financials platform with integrated journal entry, ledger, and financial reporting; used by mid-market and large enterprise organizations.
- **API Overview:** https://www.apideck.com/blog/integrate-workday-finance-api
- **Integration Cloud Connect:** https://www.workday.com/content/dam/web/se/documents/datasheets/datasheet-integration-cloud-connect-se.pdf
- **API Guide:** https://www.getknit.dev/blog/workday-api-integration-in-depth
- **Standards:** Workday SOAP API (XML; preferred for complex financial transactions including journal entries); Workday REST API (JSON; preferred for modern integrations). Key journal entry APIs: `Import_Accounting_Journal`, `Submit_Accounting_Journal`.
- **Authentication:** Integration System User (ISU) for server-to-server; OAuth 2.0 for user-authorised access.
- **Notable:** Workday's SOAP API is the more complete interface for financial data operations (journal entries, ledger accounts, compliance reporting). REST API is available for lighter integrations. Full ERP context makes Workday a key GL data source for close automation platforms targeting enterprise deployments.

---

### Microsoft Dynamics 365 Finance

- **Description:** Cloud ERP for mid-market and enterprise with integrated financial close, journal entry management, and reporting.
- **MCP Server for Finance & Operations:** https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/copilot/copilot-mcp
- **General D365 integration:** https://www.putitforward.com/connectors/erp-finance-hr-systems/sap-s4hana-integration
- **Standards:** OData REST API; Power Platform connectors; MCP server (as of 2025/2026 — enables AI agents to perform data operations and access business logic directly).
- **Authentication:** OAuth 2.0 / Microsoft Entra ID (Azure AD).
- **Notable:** Microsoft has published a Model Context Protocol (MCP) server for Dynamics 365 Finance & Operations, enabling AI agents to query and write financial data with full audit trails. This is the most advanced ERP-to-AI-agent integration in the market as of 2026 and directly relevant to building MCP-compatible close automation agents.

---

## Notes

**Emerging standard — MCP for financial close agents**: Microsoft's Dynamics 365 MCP server (2025/2026) represents the leading edge of standardised AI-agent integration with ERP systems. As MCP adoption grows across ERP vendors (Zoho has published an MCP server; SAP and Oracle integration is anticipated), building close automation AI agents as MCP clients will become the lowest-friction integration path, replacing bespoke REST API integrations for each ERP. Open-source close automation built on MCP from the start would be architecturally differentiated from legacy close platforms.

**IFRS 18 system impact (2027)**: The introduction of IFRS 18 requires income statement restructuring and MPM disclosures. Financial close platforms will need to support IFRS 18 categorisation at the GL transaction level — a tagging requirement that currently sits outside most close automation tools and represents a near-term implementation requirement for any platform targeting IFRS reporters.

**ISO 20022 migration complete (November 2025)**: The SWIFT network coexistence period ended 22 November 2025. All cross-border payments and bank reporting on SWIFT now use ISO 20022 camt messages. Bank reconciliation modules must ingest camt.053 (end-of-day statement) natively; legacy MT940 support should be maintained only for domestic banking systems still using the older format.

**Gap — no open-source close platform with published API**: Neither ERPNext nor any other open-source project publishes a financial close automation API. An open-source platform with a well-documented OpenAPI specification would be uniquely positioned to drive integration with both existing ERP systems and the emerging MCP ecosystem.
