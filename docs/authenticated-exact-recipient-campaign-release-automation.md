# Authenticated Exact Recipient Campaign Release Automation

Implements a separate confirmation and activation path for an exact reviewed recipient group in a paused Instantly campaign.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Release preview:** Reads current exclusions, campaign recipients and sender evidence.
- **Explicit confirmation:** Collects delivery review and client approval references and binds them to the selected group.
- **Reserved activation:** Saves a release checkpoint, rechecks the paused campaign and prepares one activation request.
- **Readback reconciliation:** Reads provider state after activation and retains an uncertain result for recovery rather than blindly repeating the action.

## Workflow

1. Select the batch and paused campaign in the authenticated form.
2. Preview current recipient, sender and exclusion evidence.
3. Confirm and recheck the exact group.
4. Persist the release checkpoint and apply the activation guard.
5. Activate only if enabled, then reconcile the provider readback.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Instantly API | Campaign, recipient, verification or outcome operations as specified. |
| GoHighLevel API | Current contact identity and exclusion information. |
| Instantly API | Campaign recipients, existing leads and block-list information. |

## Repository contents

- [`workflows/authenticated-exact-recipient-campaign-release.json`](../workflows/authenticated-exact-recipient-campaign-release.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-exact-recipient-campaign-release.json` | 27 | Inactive | Supplied export |

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

- [email-sender-health-and-campaign-evidence-collection-automation](email-sender-health-and-campaign-evidence-collection-automation.md) — import and select its workflow in the caller node.
- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- This export is inactive and release_enabled is false. It contains an activation path, but the saved configuration does not enable it. Activation would not prove delivery.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
