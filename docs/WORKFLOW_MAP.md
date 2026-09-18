# Workflow Map

## AI Call QA & Escalation

- `main-call-qa-workflow.json` — detects recordings, transcribes, scores calls, logs results, and escalates low scores.
- `notify-manager-on-bad-ticket.json` — creates a customer-email draft and sends it to a manager for approval.
- `get-client-email-by-recording-url.json` — resolves client email; the current export uses a mock lookup.
- `manager-decision-send-email.json` — processes Telegram approval/rejection, sends approved email, and updates status.

## AI Ticket Routing, SLA & Analytics

- `ai-ticket-routing-sla-escalation.json` — classifies incoming tickets and assigns owner, priority, sentiment, and SLA.
- `sla-escalation-watcher.json` — escalates overdue tickets from owner to team lead to director.
- `quantitative-ticket-analysis.json` — calculates distributions for category, priority, status, SLA, owner, and sentiment.
- `qualitative-ticket-analysis.json` — generates hypotheses and an action plan from ticket data.

## AI Sales Intelligence

- `deal-health-alerts.json` — enriches Zoho deals with activities, scores deal health, and alerts management.
- `get-zoho-lead-activities.json` — retrieves CRM calls, tasks, and notes.
- `ai-sales-reporting.json` — generates scheduled portfolio-level deal reports.

## Other systems

- `lead-conversation-analysis.json` — extracts BANT-oriented lead information using CRM data and PostgreSQL memory.
- `qdrant-knowledge-base-loader.json`, `telegram-objection-handling-bot.json`, `lead-call-script-generator.json` — AI Sales Assistant modules.
- `wix-lead-marketing-automation.json` — Wix → CRM → Sheets → Telegram → Klaviyo pipeline.
- `website-inquiry-main.json`, `website-inquiry-follow-up.json`, `website-inquiry-error-handler.json` — website inquiry intake, reminders, and error monitoring.
- `ai-self-care-bot.json` — Telegram self-care MVP.
- `ai-image-approval-publishing.json` — reserved filename for the image-generation project; its JSON export was not included in this upload.

## Security checklist

Replace API keys, authorization headers, chat IDs, email addresses, private URLs, spreadsheet IDs, webhook URLs, signed download links, and credential IDs before making workflow exports public. Use placeholders such as `YOUR_API_KEY`, `YOUR_SPREADSHEET_ID`, and `YOUR_TELEGRAM_CHAT_ID`.
