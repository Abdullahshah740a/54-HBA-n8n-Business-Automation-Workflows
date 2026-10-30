# Department Task Tracking and Weekly Reporting Automation

This version summarizes Asana task progress across six configured departments and writes a weekly Airtable snapshot for each. A department loop keeps paginated task results separate.

> Sanitized workflow export. Deployment testing has not been performed.

## Functionalities

- **Department coverage:** Includes Human Resources, Marketing, Offers, Sales, Client Relations and Business Partnerships.
- **Sequential department processing:** Processes one department per loop pass, then returns for the next department.
- **Paginated task collection:** Follows Asana next-page URLs with a configured maximum of 20 requests per department.
- **Task buckets:** Counts recently completed tasks, overdue open tasks, tasks due in the next seven days and total open tasks.
- **Repeatable snapshots:** Uses Monday-based Week Of plus Department to construct the Snapshot Key for Airtable updates.

## Workflow

1. Start the weekly schedule and load the department project IDs.
2. Loop through one department at a time.
3. Retrieve its available task pages and combine them.
4. Calculate task-status buckets and the weekly snapshot key.
5. Upsert Department Weekly Snapshot, then continue the department loop.

## Tools

| Tool | Purpose |
| --- | --- |
| Asana API | Project tasks, completion dates and due dates. |
| n8n | Weekly schedule, department loop and pagination. |
| JavaScript | Task aggregation and weekly keys. |
| Airtable | Department Weekly Snapshot table. |

## Repository contents

- [`workflows/department-task-tracking-and-weekly-reporting-version-01.json`](../workflows/department-task-tracking-and-weekly-reporting-version-01.json)
- [`workflows/department-task-tracking-and-weekly-reporting-version-02.json`](../workflows/department-task-tracking-and-weekly-reporting-version-02.json)

| Export | Nodes | Original export status | Version notes |
| --- | ---: | --- | --- |
| `department-task-tracking-and-weekly-reporting-version-01.json` | 7 | Active | Scalable version from the future-proof export, with department isolation and pagination. |
| `department-task-tracking-and-weekly-reporting-version-02.json` | 7 | Inactive | Original version without the department pagination loop. |

## Setup

1. Import the selected JSON file into a compatible n8n instance. All published exports are inactive.
2. Open each node and reconnect the required n8n credentials. Original credential bindings were removed.
3. Replace `EXAMPLE_*` resource identifiers, `example.com` endpoints, synthetic contacts and deployment-specific settings with your own configuration.
4. Create the required destination sheets/tables, field mappings, views and state-store schemas before writing any records.
5. Rebind Execute Workflow nodes to the corresponding workflows imported into your instance. Original workflow IDs are not portable.
6. Review prompts, scoring criteria, approval rules, spending caps and historical time windows. Keep the existing approval and no-send controls in place.
7. Use synthetic input to verify branches and destination mappings, then enable the appropriate trigger when the configuration is complete.

Credential types referenced by the original export: `airtableTokenApi`, `asanaApi`.

## Export limitations and configuration notes

- Marked active in the export. Pagination is capped at 20 requests. Tasks without due dates contribute to Total Open but cannot be classified as overdue or upcoming.
- Inactive original version. Project IDs remain placeholders, task requests have no pagination, and the upsert matches record id rather than the computed Snapshot Key. Configuration needs completion before use.
- Alternate supplied versions are retained together. Review differences before selecting a version; filenames do not imply production maturity.
- Workflow export state describes the supplied file only; successful live execution has not been verified.
- Embedded client/prospect examples were replaced. Cached execution data, pinned data and credential bindings were removed.
- Resource IDs, URLs and evidence hashes were replaced for publication. Some fixtures and historical recovery scenarios require new test data and regenerated evidence.
- API credentials belong in n8n credential storage or the configured secret store. Do not commit live keys, contact lists or execution receipts.

## Validation

The preparation checks parse the JSON, preserve node counts and check connection targets. Code-node syntax is checked separately without executing the workflow. These checks do not verify provider access, business results or production readiness.
