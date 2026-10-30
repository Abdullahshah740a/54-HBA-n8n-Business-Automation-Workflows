# Executive KPI and Sales Performance Dashboard Refresh Automation

This workflow refreshes selected executive KPIs and weekly sales activity from Airtable and GA4. It reports the last completed week and keeps the pooled close-rate calculation separate from weekly activity.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Reporting windows:** Calculates the last completed Monday-to-Sunday week and the current month-to-date window.
- **Executive actuals:** Updates weekly new leads and alignment-call activity, with GA4 active users written to the configured monthly lead-generation tile.
- **Weekly sales activity:** Computes booked and conducted alignment calls plus representative counts and weekly new leads.
- **Find then write:** Looks up the Sales Engine week and chooses create or update, rather than relying on a date-field upsert.
- **Pooled close rate:** Divides cumulative paid members by cumulative opportunities at alignment-call-conducted or later defined stages, then writes the ratio to one fixed anchor row.
- **Limited metric scope:** Leaves paid-member and membership-revenue actuals untouched and does not populate unsupported close-by-tier totals.

## Workflow

1. Start a manual or weekly run and calculate the reporting windows.
2. Read the relevant opportunities and appointment records.
3. Request month-to-date GA4 active users and update the selected executive rows.
4. Compute weekly sales activity, find the week record and create or update it.
5. Read cumulative alignment-or-beyond opportunities and the latest paid-member count.
6. Write the pooled close-rate ratio to its configured anchor record.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Schedules and coordinates the three reporting branches. |
| Airtable API | Reads reporting sources and writes executive and Sales Engine fields. |
| Google Analytics 4 | Month-to-date sitewide active-user metric. |
| JavaScript | Date windows, activity counts and pooled ratio calculation. |

## Repository contents

- [`workflows/executive-kpi-and-sales-performance-dashboard-refresh.json`](../workflows/executive-kpi-and-sales-performance-dashboard-refresh.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `executive-kpi-and-sales-performance-dashboard-refresh.json` | 17 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`, `googleAnalyticsOAuth2`.

## Export limitations and configuration notes

- Marked active in the export. GA4 active users are a website audience measure, not verified leads. The paid-member source is described as provisional, and several reads are limited to the first 100 records without pagination.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
