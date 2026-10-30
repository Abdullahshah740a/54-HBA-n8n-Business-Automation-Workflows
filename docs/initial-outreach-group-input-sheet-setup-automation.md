# Initial Outreach Group Input Sheet Setup Automation

Populates the dedicated Input worksheet for a fixed first-group test using a predefined header row and five prospect rows.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Fixed target:** Writes a specific A1 to I6 worksheet range.
- **Prepared input rows:** Installs the initial group data used by dependent intake workflows.
- **No-send setup:** Contains no model, staging or campaign activation step.

## Workflow

1. Start the manual setup.
2. Write the predefined input values to the dedicated sheet.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Manual setup trigger and HTTP request. |
| Google Sheets API | Writes the dedicated Input range. |

## Repository contents

- [`workflows/initial-outreach-group-input-sheet-setup.json`](../workflows/initial-outreach-group-input-sheet-setup.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `initial-outreach-group-input-sheet-setup.json` | 2 | Inactive | Supplied export |

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

- Inactive and limited to a fixed worksheet and five-row setup. Running it writes those cells; it is not a general batch intake process.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
