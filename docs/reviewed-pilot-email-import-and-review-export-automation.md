# Reviewed Pilot Email Import and Review Export Automation

Imports a fixed set of manually reviewed pilot emails into operating state and exports them for review without generating new model output.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Exact manual copy:** Prepares the supplied pilot content with its source provenance.
- **Controlled save:** Claims the state row, saves the import and verifies the receipt.
- **Review handoff:** Calls the verified review-sheet export after the saved import is confirmed.

## Workflow

1. Start the manual pilot import.
2. Read state and prepare the fixed reviewed copy.
3. Claim and save the pilot state.
4. Verify the import and export its review view.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Verified Review Sheet Export | Writes the imported pilot into the review view. |

## Repository contents

- [`workflows/reviewed-pilot-email-import-and-review-export.json`](../workflows/reviewed-pilot-email-import-and-review-export.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `reviewed-pilot-email-import-and-review-export.json` | 9 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [verified-outreach-review-sheet-publishing-automation](verified-outreach-review-sheet-publishing-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Inactive no-send import. The code explicitly distinguishes manually reviewed copy from fresh model-output proof and from client sending approval.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
