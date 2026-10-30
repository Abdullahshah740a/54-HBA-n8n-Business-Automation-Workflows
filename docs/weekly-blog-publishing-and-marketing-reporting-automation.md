# Weekly Blog Publishing and Marketing Reporting Automation

This workflow measures publishing output by counting published WordPress posts per week and updating the Blogs Published metric in Airtable Marketing Engine.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Published content intake:** Reads the public WordPress REST API for published posts and publication dates.
- **Weekly grouping:** Assigns each post to the Monday of its publication week.
- **Publishing volume:** Counts posts per week without creating or editing the blog content.
- **Focused reporting update:** Upserts Week, Week Key and Blogs Published rather than populating unrelated marketing metrics.

## Workflow

1. Run the weekly schedule or manual trigger.
2. Fetch published WordPress posts.
3. Group posts by their Monday-based publication week.
4. Calculate Blogs Published for each week.
5. Upsert Marketing Engine using Week Key.

## Tools

| Tool | Purpose |
| --- | --- |
| WordPress REST API | Published blog post dates. |
| n8n | Schedule and synchronization. |
| JavaScript | Weekly grouping and counts. |
| Airtable | Marketing Engine reporting table. |

## Repository contents

- [`workflows/weekly-blog-publishing-and-marketing-reporting.json`](../workflows/weekly-blog-publishing-and-marketing-reporting.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `weekly-blog-publishing-and-marketing-reporting.json` | 6 | Active | Supplied export |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`.

## Export limitations and configuration notes

- Marked active in the export. The request retrieves up to 100 posts and does not paginate, so counts can be incomplete once the published post list exceeds that limit.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
