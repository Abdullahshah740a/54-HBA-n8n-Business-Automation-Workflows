# Initial Recipient Group No Send Readiness Evidence Automation

Collects read-only evidence for a fixed group of five prospects and a configured sender before any staging or release decision.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Exact group:** Uses the fixed first-five contact identities, aliases and campaign reference.
- **Fresh source reads:** Calls the exclusion reader and sender evidence workflow.
- **Evidence receipt:** Returns both evidence packets with explicit zero prospect sends and zero verification purchases in its scope.

## Workflow

1. Start the manual proof.
2. Prepare the exact five identities.
3. Read fresh identity and exclusion information.
4. Read current sender evidence and return the combined receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Manual orchestration and subworkflow calls. |
| Fresh Exclusion Reader | Current prospect and exclusion evidence. |
| Current Sender Evidence | Current account and sending-context evidence. |

## Repository contents

- [`workflows/initial-recipient-group-no-send-readiness-evidence.json`](../workflows/initial-recipient-group-no-send-readiness-evidence.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `initial-recipient-group-no-send-readiness-evidence.json` | 5 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Related workflow dependencies

- [email-sender-health-and-campaign-evidence-collection-automation](email-sender-health-and-campaign-evidence-collection-automation.md) — import and select its workflow in the caller node.
- [fresh-prospect-exclusion-and-campaign-membership-evidence-automation](fresh-prospect-exclusion-and-campaign-membership-evidence-automation.md) — import and select its workflow in the caller node.

## Export limitations and configuration notes

- Inactive no-send proof for a specific group. A readiness packet is not client approval, campaign activation or evidence of delivered email.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
