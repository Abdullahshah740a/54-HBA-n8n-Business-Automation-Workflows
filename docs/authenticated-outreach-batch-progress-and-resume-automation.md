# Authenticated Outreach Batch Progress and Resume Automation

Provides an operator view for checking an existing batch and requesting a controlled continuation or delivery-monitor refresh.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Progress view:** Reads the stored batch summary through an authenticated form.
- **Controlled continuation:** Rechecks state before saving an operator action and calling the batch driver or monitor.
- **Safe review export:** Exports the current review view only when no ownership lock or unresolved effect prevents it.

## Workflow

1. Open the progress form and choose the batch action.
2. Refresh and validate the batch state.
3. Persist the confirmed action.
4. Run processing or monitoring when requested.
5. Read the final status and export the review view when safe.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Batch Driver and Reply Monitor | Dependent processing and monitoring workflows. |
| Review Sheet Export | Dependent operator-review view generator. |

## Repository contents

- [`workflows/authenticated-outreach-batch-progress-and-resume.json`](../workflows/authenticated-outreach-batch-progress-and-resume.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-outreach-batch-progress-and-resume.json` | 20 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [automatic-email-reply-and-bounce-monitoring-automation](automatic-email-reply-and-bounce-monitoring-automation.md) — import and select its workflow in the caller node.
- [bounded-outreach-batch-processing-driver-automation](bounded-outreach-batch-processing-driver-automation.md) — import and select its workflow in the caller node.
- [verified-outreach-review-sheet-publishing-automation](verified-outreach-review-sheet-publishing-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- A progress action is not itself an exact-copy or campaign-release approval. Busy or unresolved state can prevent continuation or export.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
