# Email Sender Health and Campaign Evidence Collection Automation

Collects current sender-account evidence from Instantly for later staging or release checks.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Account and mappings:** Reads the configured sender account and its campaign mappings.
- **Sending context:** Retrieves daily analytics and recent email records for the selected window.
- **Bounded evidence:** Follows read stages with request and freshness limits, returning a complete evidence packet only after all stages finish.

## Workflow

1. Receive the internal sender-read request.
2. Read the account and campaign mappings.
3. Read analytics and recent message pages.
4. Validate completion and return the sender evidence packet.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Internal request loop and response routing. |
| JavaScript | Read stages, freshness and completeness checks. |
| Instantly API | Sender account, mappings, analytics and email evidence. |

## Repository contents

- [`workflows/email-sender-health-and-campaign-evidence-collection.json`](../workflows/email-sender-health-and-campaign-evidence-collection.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `email-sender-health-and-campaign-evidence-collection.json` | 7 | Inactive | Supplied export |

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

- Inactive in the export. This workflow gathers evidence; it does not verify every authentication setting by itself or authorize campaign release.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
