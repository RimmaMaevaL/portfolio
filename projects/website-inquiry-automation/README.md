# Website Inquiry Automation

A website-inquiry pipeline with normalization, duplicate detection, priority flagging, team notifications, confirmation emails, follow-up reminders, and error alerts.

## Workflow

A webhook receives an inquiry, normalizes the data, checks duplicates by email or phone, prioritizes and stores new records, alerts the team, and confirms receipt to the customer. A daily workflow finds inquiries older than two business days and sends one reminder. An error workflow reports failed executions.

## Stack

`n8n` · `Webhooks` · `Google Sheets` · `Gmail` · `Telegram`

## Outcome

The system is designed so an inquiry is not silently lost or processed twice. Status updates prevent repeated reminder messages.

## Modules

- `website-inquiry-main.json`
- `website-inquiry-follow-up.json`
- `website-inquiry-error-handler.json`
