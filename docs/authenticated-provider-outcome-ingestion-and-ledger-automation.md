# Authenticated Provider Outcome Ingestion and Ledger Automation

Fetches an original Instantly event by ID and validates it before recording the outcome and any pending follow-up tasks.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Provider readback:** Uses an event ID to retrieve the original authenticated provider event.
- **Workspace and event checks:** Validates the returned event against the configured workspace and expected reference.
- **Durable ingestion:** Claims and saves the verified outcome in the native store.
- **Separate effects queue:** Reports pending outcome tasks rather than treating them as already applied.

## Workflow

1. Receive the internal event reference.
2. Read operating state and validate availability.
3. Fetch and validate the original provider event.
4. Claim and save the accepted outcome.
5. Return its saved receipt and pending effect count.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Instantly API | Campaign, recipient, verification or outcome operations as specified. |

## Repository contents

- [`workflows/authenticated-provider-outcome-ingestion-and-ledger.json`](../workflows/authenticated-provider-outcome-ingestion-and-ledger.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authenticated-provider-outcome-ingestion-and-ledger.json` | 10 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `httpHeaderAuth`.

## Export limitations and configuration notes

- Inactive in the export. The workflow validates and records outcomes; subsequent campaign or block-list actions belong to the effects worker.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
