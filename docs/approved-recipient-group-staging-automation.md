# Approved Recipient Group Staging Automation

Stages a specifically approved group into a paused outreach campaign by coordinating the single-person staging workflow.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Bounded group:** Requires run, campaign and grant references with one to five unique contact IDs.
- **Sequential staging:** Stages one approved person at a time and collects the returned receipts.
- **Receipt checks:** Stops if the person, run, staged status, remote lead ID or released-lock confirmation does not match.

## Workflow

1. Validate the approved group input.
2. Call the single-person staging workflow.
3. Check its receipt before moving to the next person.
4. Return the group count and individual staging receipts.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Exact Copy Staging workflow | Performs each approved recipient handoff to Instantly. |

## Repository contents

- [`workflows/approved-recipient-group-staging.json`](../workflows/approved-recipient-group-staging.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `approved-recipient-group-staging.json` | 7 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [approved-exact-copy-campaign-staging-automation](approved-exact-copy-campaign-staging-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- The final receipt explicitly states sending is unauthorized and the campaign has not been activated. This component does not authorize prospect email sending or campaign activation.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
