# Dedicated Outreach Input and Review Workbook Setup Automation

Creates a dedicated Google spreadsheet containing separate Input and Review tabs for the email operating process.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **One-time creation:** Requests a new operating spreadsheet rather than reading an existing batch.
- **Separated views:** Creates two tabs so input and generated review material have separate destinations.
- **Setup receipt:** Checks the returned spreadsheet ID and two-tab result and reports the new spreadsheet information.

## Workflow

1. Start the manual setup.
2. Create the dedicated spreadsheet through the Sheets API.
3. Validate the two-tab response and return its location.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Manual request and receipt handling. |
| Google Sheets API | Spreadsheet and worksheet creation. |
| JavaScript | Setup response validation. |

## Repository contents

- [`workflows/dedicated-outreach-input-and-review-workbook-setup.json`](../workflows/dedicated-outreach-input-and-review-workbook-setup.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `dedicated-outreach-input-and-review-workbook-setup.json` | 3 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `googleSheetsOAuth2Api`.

## Export limitations and configuration notes

- Inactive one-time setup. It creates the workbook structure but does not import, research, verify or send to prospects.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
