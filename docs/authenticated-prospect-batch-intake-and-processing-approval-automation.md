# Authenticated Prospect Batch Intake and Processing Approval Automation

Creates a saved outreach batch from a specifically selected Google Sheets input range after an authorized operator reviews and confirms it.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Bound input read:** Reads spreadsheet metadata and the exact input range rather than trusting a supplied arbitrary sheet payload.
- **Confirmation and closeout:** Checks the new batch reference and any prior-batch disposition before saving.
- **Saved-state verification:** Claims the operating row, saves the batch and verifies the resulting receipt.
- **Conditional processing:** Invokes the batch driver only when the saved approval and readiness conditions allow it.

## Workflow

1. Open the authenticated batch intake form.
2. Read and parse the dedicated input tab.
3. Refresh exclusion evidence and show the exact intake confirmation.
4. Save the confirmed batch and verify it.
5. Process if permitted, otherwise return the saved batch status.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Google Sheets API | Dedicated Input and Review worksheet access. |
| GoHighLevel API | Current contact identity and exclusion information. |
| Instantly API | Campaign recipients, existing leads and block-list information. |

## Repository contents

- [`workflows/authenticated-prospect-batch-intake-and-processing-approval.json`](../workflows/authenticated-prospect-batch-intake-and-processing-approval.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-prospect-batch-intake-and-processing-approval.json` | 20 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `googleSheetsOAuth2Api`.

## Related workflow dependencies

- [bounded-outreach-batch-processing-driver-automation](bounded-outreach-batch-processing-driver-automation.md) — import and select its workflow in the caller node.
- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- The exported run configuration sets the provider cost cap to zero. Intake or batch processing is separate from permission to stage or send email.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
