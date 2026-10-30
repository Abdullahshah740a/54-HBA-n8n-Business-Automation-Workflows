# Read Only AI Model Availability Evidence Automation

Reads the OpenAI model list through the configured credential and reports whether two named model identifiers are present.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Read-only request:** Uses the models listing endpoint rather than an inference request.
- **Presence report:** Returns the listed-model count and any matches for the two configured identifiers.
- **Bounded invocation:** Runs only inside the saved one-time read window.

## Workflow

1. Validate the one-time window.
2. Read the available-model response.
3. Check its response structure and report matching identifiers.

## Tools

| Tool | Purpose |
| --- | --- |
| n8n | Bounded scheduled request. |
| OpenAI API | Authenticated model-list endpoint. |
| JavaScript | Response validation and identifier matching. |

## Repository contents

- [`workflows/read-only-ai-model-availability-evidence.json`](../workflows/read-only-ai-model-availability-evidence.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `read-only-ai-model-availability-evidence.json` | 4 | Inactive | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `openAiApi`.

## Export limitations and configuration notes

- Inactive read-only proof. A listed identifier is not a successful inference test, a pricing confirmation or permission to change production models.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
