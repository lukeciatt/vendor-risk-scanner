# Vendor Risk Scanner

A Claude Skill that automates third-party vendor risk assessments using free open-source intelligence and Model Context Protocol (MCP) connectors. It extracts data from vendor status APIs, trust centers, news feeds, and vulnerability databases to generate structured JSON findings for your risk dashboard.

## Requirements

You need Claude configured with the following free MCP servers:
* `@modelcontextprotocol/server-fetch` to pull raw JSON feeds and RSS data directly into context.
* `@modelcontextprotocol/server-brave-search` to execute targeted executive, legal, and background searches[cite: 2].
* `@modelcontextprotocol/server-puppeteer` to render and read JavaScript-heavy compliance portals like Vanta or Drata[cite: 2].

## Monitored Sources

* **Availability:** Vendor status page APIs (e.g., `/api/v2/summary.json`).
* **Compliance:** SOC 2 and ISO 27001 validations among others via vendor trust centers.
* **Security Incidents:** CISA Known Exploited Vulnerabilities catalog and RansomWatch leak site postings.
* **Reputation & Governance:** Google News RSS parameters for regulatory actions, lawsuits, and executive turnover.
* **Background:** OpenCorporates and SEC EDGAR filings for financial and ownership data.

## Installation

1. Copy the `SKILL.md` file into your local Claude environment or upload it directly to your Claude Enterprise/Team skills library.
2. Ensure your `claude_desktop_config.json` is configured to run the required Fetch, Brave Search, and Puppeteer MCP servers.

## Usage

Prompt Claude with your target list and any internal context (like PII exposure):
> "Run the vendor-risk-scanner on VendorA (vendora.com) and VendorB (vendorb.com). Note that VendorA processes our customer PII."

Claude will autonomously route the queries through the appropriate MCPs, evaluate the severity of any discovered incidents against your internal dependencies, and output a standardized JSON array of findings ready for dashboard ingestion.
