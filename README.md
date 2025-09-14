# QA Automation Tool - Public Artifacts

This repository hosts **public artifacts** from QA Automation Tool test runs, providing team-wide access to test results without requiring GitHub authentication.

[🔗 Live Dashboard](https://qa-automation-tool.vercel.app/) | [📊 View Test Results](https://github.com/rsmedstad/qat-artifacts/tree/main/runs)

---

## Purpose & Access

While the main QA automation code is private ([qa-automation-tool](https://github.com/rsmedstad/qa-automation-tool) - restricted access), this repository provides **public access** to:
- Test execution summaries (`summary.json`)
- Test results (Excel files)
- Run metadata and direct download links
- Historical test run data

**✅ No GitHub authentication required** - accessible by all team members and stakeholders.

---

## What is the QA Automation Tool?

A centralized platform for automating web-application quality assurance. Runs a predefined suite of end-to-end checks, aggregates results in real time, and presents trends on a clean dashboard.

### Key Capabilities

- **Executes** comprehensive UI and workflow checks across target URLs
- **Stores** results, progress and artifacts in Supabase and Vercel KV
- **Visualizes** outcomes and trends in an interactive dashboard
- **Enables** ad-hoc and scheduled runs, with AI-driven query support via Gemini

### Technology Stack

| Layer         | Framework / Service                    |
|---------------|----------------------------------------|
| Application   | Node.js, Next.js                       |
| Automation    | Playwright                             |
| Data Storage  | Supabase (Postgres) & Vercel KV        |
| CI / Delivery | GitHub Actions, Vercel                 |
| Reporting     | Chart.js, ExcelJS                      |
| AI Insights   | Gemini with LangChain                  |

---

## Test Suite Overview

### Automated Testing Schedule
- **Scheduled tests**: every 3 hours via GitHub Actions
- **Cleanup tasks**: every 3 days (60-day retention)
- **Coverage**: Playwright tests for page structure, functionality and performance

### Key Features

**Dashboard:**
- Recent runs with pass/fail/N-A counts and trend charts
- Ask Gemini: natural-language queries (passphrase-protected)
- Ad-hoc execution: trigger tests immediately with custom parameters

**Testing Methods:**
- Automated browser testing with Playwright
- Manual validation support via Excel input
- Screaming Frog compatibility for manual verification

---

## Test Definitions & Protocol

| ID      | Name                        | Description                                          |
|---------|-----------------------------|------------------------------------------------------|
| **TC-01** | Hero Overlay on Desktop    | Hero text visible at 1920×1080 for homepage, category, product and custom hero banners |
| **TC-02** | Hero Static on Mobile      | Hero text visible on 375×667 viewport for homepage, category, product and custom hero banners |
| **TC-03** | Header Presence            | `<header>` or class containing "header"              |
| **TC-04** | Navigation Presence        | `<nav>` or class containing "nav"                    |
| **TC-05** | Main Content               | `<main>` or class containing "main"                  |
| **TC-06** | Footer Presence            | `<footer>` or class containing "footer"              |
| **TC-07** | Main Video & Carousel      | `<video>` or Vidyard iframe; play button opens modal; carousel videos show no "Video Not Found" |
| **TC-08** | Contact Form Opens         | "Contact" button launches form overlay               |
| **TC-09** | Rendering Error Check      | No "A rendering error occurred" text                 |
| **TC-10** | Gatekeeper Redirect        | Incognito + "Yes" click yields 200 status            |
| **TC-11** | Insights Link Works        | First insights/newsroom link returns HTTP 200        |
| **TC-12** | DocCheck Login Route       | Incognito → URL includes `/account/doccheck-login`   |
| **TC-13** | DE Nav Redirect            | "Produkte → Ultraschall → Mehr erfahren" → target site |
| **TC-14** | HTTP Status Code Valid     | Status 200 or valid redirect (301/302)               |

### Technical Implementation Notes

**TC-01 & TC-02** use viewport-specific checks for hero text visibility:
- TC-01: Desktop viewport (1920×1080)
- TC-02: Mobile viewport (375×667)

**Supported hero components:**
- `div[id*="ge-homepage-hero"]`
- `.ge-homepage-hero-v2-component`
- `.ge-category-hero__container`
- `.hero-content-intro`
- `.product-heroV2-container`

---

## Repository Structure & Access

```
/runs
  /{run-id}/
    - summary.json      # Test execution summary
    - results-{id}.xlsx # Detailed test results
    - metadata.json     # Links to media files
    - README.md         # Run-specific documentation
```

### How the Architecture Works

1. **Private code** ([qa-automation-tool](https://github.com/rsmedstad/qa-automation-tool)) runs tests via GitHub Actions
2. **Results publish** automatically to this public repository after each test
3. **Dashboard links** point to artifacts here for easy team access
4. **No authentication required** for viewing test results or downloading files

### Accessing Media Files

Screenshots and videos are stored in Azure Blob Storage for efficiency.
Check the `metadata.json` file in each run directory for direct access URLs.

### Data Retention

- **Retention period**: 60 days
- **Cleanup schedule**: Every 3 days
- **Storage**: Lightweight JSON and Excel files only (media in Blob storage)

---

## Getting Started

1. **View recent results**: Browse the [/runs](https://github.com/rsmedstad/qat-artifacts/tree/main/runs) directory
2. **Access dashboard**: Visit [qa-automation-tool.vercel.app](https://qa-automation-tool.vercel.app/)
3. **Download artifacts**: Click direct download links in any run folder
4. **Ask questions**: Use the "Ask Gemini" feature on the dashboard (passphrase required)

For assistance or questions, reach out via company channels (Teams/Outlook).

---

## License

All rights reserved © Ryan Smedstad.
Unauthorized copying, modification or distribution is prohibited.

*Generated by [QA Automation Tool](https://qa-automation-tool.vercel.app/)*
