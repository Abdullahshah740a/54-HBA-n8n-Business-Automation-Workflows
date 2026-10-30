# Verified Outreach Review Sheet Publishing Automation

Publishes a generated Google Sheets review view from saved operating state and verifies the written result.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Authorized export:** Requires the correct run and an available state store.
- **Exact tab binding:** Reads spreadsheet metadata and binds the configured Review tab.
- **Change detection:** Returns an unchanged receipt if the generated view does not need rewriting.
- **Verified write:** Persists an export checkpoint, writes the view and reads it back before saving completion.

## Workflow

1. Read and authorize the saved run.
2. Bind the Review tab and inspect its current contents.
3. Prepare the generated view and detect changes.
4. Save the checkpoint before writing when required.
5. Read back, reconcile and save the export receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Google Sheets API | Dedicated Input and Review worksheet access. |

## Repository contents

- [`workflows/verified-outreach-review-sheet-publishing.json`](../workflows/verified-outreach-review-sheet-publishing.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `verified-outreach-review-sheet-publishing.json` | 18 | Active | Supplied export |

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

- Marked active in the export. A sheet export is an operator review view, not evidence that a draft was approved or an email was sent.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
