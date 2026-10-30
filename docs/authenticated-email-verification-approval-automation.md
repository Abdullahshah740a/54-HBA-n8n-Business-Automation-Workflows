# Authenticated Email Verification Approval Automation

Gives an authorized operator a preview and confirmation process for selected address-verification jobs before a bounded verification queue is started.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Authenticated preview:** Reads the current batch state and fresh verification evidence.
- **Exact approval grant:** Binds confirmation to the saved state and records the approved verification actions.
- **Bounded queue:** Starts one verification action at a time and checks each returned run, job and grant reference.

## Workflow

1. Open the authenticated form with a batch reference.
2. Preview the address-check plan and confirm it.
3. Refresh state, claim the row and save the verification grant.
4. Run the approved queue and return a summary.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n Forms | Authenticated operator entry and confirmation pages. |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Checkpointed Address Verification | Executes the granted submit or poll action. |

## Repository contents

- [`workflows/authenticated-email-verification-approval.json`](../workflows/authenticated-email-verification-approval.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-email-verification-approval.json` | 17 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [checkpointed-email-address-verification-automation](checkpointed-email-address-verification-automation.md) — import and select its workflow in the caller node.
- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- The export has a zero verification-credit cap and zero maximum credits per address. Do not treat this configuration as permission to purchase new verification checks. This component does not authorize prospect email sending or campaign activation.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
