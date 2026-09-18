# AI Ticket Routing, SLA Escalation & Analytics System

An AI-powered support-operations system for an online confectionery.

## Business problem

Tickets were triaged manually, and SLA breaches could remain invisible until customers followed up.

## Workflow

Gmail messages are classified by category, priority, owner, SLA, sentiment, and reasoning. Non-spam tickets are logged in Google Sheets and routed to Slack. A scheduled watcher escalates overdue tickets through owner, team-lead, and director levels. Separate workflows provide quantitative and qualitative analytics.

## Stack

`n8n` · `Groq / Llama 3.3 70B` · `Gmail` · `Google Sheets API` · `Slack API`

## Outcome

Time to first classification is under one minute in the demonstrated setup. SLA thresholds and recipients are configurable.

## Modules

- `ai-ticket-routing-sla-escalation.json`
- `sla-escalation-watcher.json`
- `quantitative-ticket-analysis.json`
- `qualitative-ticket-analysis.json`
