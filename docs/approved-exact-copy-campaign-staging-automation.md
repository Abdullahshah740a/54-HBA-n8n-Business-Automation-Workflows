# Approved Exact Copy Campaign Staging Automation

Adds one specifically approved prospect and email payload to a paused Instantly campaign, then verifies the remote staging result.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Saved authorization:** Checks the exact person, copy version, campaign and grant expiry.
- **Pre-action rechecks:** Refreshes exclusions and verifies that the campaign remains paused and unchanged.
- **Durable staging intent:** Persists and acknowledges a reservation before the lead POST.
- **Readback reconciliation:** Reads campaign leads and saves the confirmed remote lead or an unresolved result.

## Workflow

1. Load the saved stage authorization and person.
2. Refresh exclusion and campaign evidence.
3. Save and verify the staging reservation.
4. Recheck the paused campaign and submit the exact lead payload.
5. Read back campaign leads and reconcile the staged receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Instantly API | Campaign, recipient, verification or outcome operations as specified. |
| Fresh Exclusion Reader | Provides identity and campaign-recipient evidence. |

## Repository contents

- [`workflows/approved-exact-copy-campaign-staging.json`](../workflows/approved-exact-copy-campaign-staging.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `approved-exact-copy-campaign-staging.json` | 17 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `httpHeaderAuth`.

## Related workflow dependencies

- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Staging is enabled in the export, but this component does not activate the campaign. Ambiguous provider results retain a reconciliation hold.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
