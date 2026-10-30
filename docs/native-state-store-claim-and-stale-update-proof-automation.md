# Native State Store Claim and Stale Update Proof Automation

Tests ownership and revision handling in an isolated native n8n data table using a synthetic record.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Isolated test data:** Creates and seeds a dedicated proof table.
- **First-claim check:** Attempts a revision-based claim and verifies the resulting owner and revision.
- **Stale-claim check:** Attempts a competing stale update and expects it to return no claimed row.
- **Readback receipt:** Checks final row identity and payload preservation.

## Workflow

1. Create the isolated proof table and synthetic state.
2. Save the original row identity.
3. Apply and verify the first claim.
4. Attempt a stale claim and inspect the resulting row.
5. Return the assertions in a proof receipt.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Manual proof workflow. |
| n8n Data Tables | Synthetic record and conditional updates. |
| JavaScript | Assertions and readback checks. |

## Repository contents

- [`workflows/native-state-store-claim-and-stale-update-proof.json`](../workflows/native-state-store-claim-and-stale-update-proof.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `native-state-store-claim-and-stale-update-proof.json` | 10 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

## Export limitations and configuration notes

- Inactive and synthetic only. The receipt explicitly states that true parallel execution has not been proven; this is not a live concurrency certification.
- Historical proof receipts, identity anchors, hashes and time windows were sanitized. Regenerate evidence in an isolated environment; these files do not constitute live production proof.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
