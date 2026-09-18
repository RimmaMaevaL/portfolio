# AI Sales Intelligence — Deal Health & Reporting

A Zoho CRM intelligence layer that retrieves deal activity, evaluates deal health with Claude, stores structured risks, and sends Telegram reports.

## Business problem

Management lacked a consistent view of deal status without manually inspecting CRM records, activities, dates, and notes.

## Workflow

A scheduled process selects relevant deals, retrieves calls/tasks/notes through a sub-workflow, scores deal health from 1 to 10, identifies evidence-based risks, upserts results into Google Sheets, and alerts management about critical deals. A separate report aggregates delivery, feedback, overdue, and open-deal signals.

## Stack

`n8n` · `Zoho CRM` · `Claude Opus / Sonnet` · `Google Sheets` · `Telegram`

## Outcome

Regular deal-health reporting runs without a manual CRM review step.

## Modules

- `deal-health-alerts.json`
- `get-zoho-lead-activities.json`
- `ai-sales-reporting.json`
