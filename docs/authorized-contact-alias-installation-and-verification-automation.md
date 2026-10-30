# Authorized Contact Alias Installation and Verification Automation

Performs a narrowly scoped repair that adds approved exclusion aliases to a dedicated input sheet and saved dispatch records without changing the staged copy.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Exact-row binding:** Checks the known input rows and staged dispatch identities.
- **Alias-only sheet write:** Expands and writes the additional_aliases column, leaving existing input columns unchanged.
- **Readback proof:** Reads the sheet and metadata again and checks that records and frozen message payloads remain unchanged.

## Workflow

1. Enter the bounded repair window.
2. Read sheet metadata, exact rows and the saved state.
3. Claim the repair and write only the alias column.
4. Read the data back and merge the approved aliases into state.
5. Save a verification receipt and release ownership.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Workflow routing, internal calls and execution context. |
| n8n Data Tables | Saved operating state, revisions, ownership and receipts. |
| JavaScript | Validation, state transitions and result shaping. |
| Google Sheets API | Dedicated Input and Review worksheet access. |

## Repository contents

- [`workflows/authorized-contact-alias-installation-and-verification.json`](../workflows/authorized-contact-alias-installation-and-verification.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `authorized-contact-alias-installation-and-verification.json` | 16 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `googleSheetsOAuth2Api`.

## Export limitations and configuration notes

- Inactive, one-time no-send repair with fixed rows and a short historical execution window. It is not a general-purpose contact importer or outreach workflow.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
