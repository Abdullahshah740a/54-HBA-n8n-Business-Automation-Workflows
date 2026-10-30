# Fresh Prospect Exclusion and Campaign Membership Evidence Automation

Reads current prospect identity, existing outreach and block-list evidence for selected people and their known aliases.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Scoped identity reads:** Uses selected lead identities rather than claiming a complete CRM export.
- **Cross-system evidence:** Reads GoHighLevel contacts and Instantly lead, block-list and campaign information.
- **Complete snapshot:** Tracks read completion and uses the oldest read time for freshness checks.
- **Campaign-only mode:** Can return just the current recipient list for a selected campaign.

## Workflow

1. Initialize the selected identities and optional campaign scope.
2. Prepare each bounded provider request.
3. Read and consume the required pages.
4. Normalize the evidence and return a complete snapshot.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Internal request loop. |
| JavaScript | Identity matching, completion and freshness handling. |
| GoHighLevel API | Current contact identity and exclusion information. |
| Instantly API | Campaign recipients, existing leads and block-list information. |

## Repository contents

- [`workflows/fresh-prospect-exclusion-and-campaign-membership-evidence.json`](../workflows/fresh-prospect-exclusion-and-campaign-membership-evidence.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `fresh-prospect-exclusion-and-campaign-membership-evidence.json` | 11 | Active | Supplied export |

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

- Marked active in the export. Evidence is limited to selected identities and known aliases and does not itself authorize outreach.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
