# AI Call QA & Escalation System

An AI-assisted quality-assurance pipeline for customer-support calls.

## Business problem

Manual call reviews consumed hours every week, while serious service issues could be discovered too late.

## Workflow

1. Detect a new Google Drive recording.
2. Filter and download audio for transcription.
3. Evaluate the transcript against eight QA criteria: greetings, active listening, needs discovery, empathy, expertise, solution clarity, next steps, and closing.
4. Store structured scores and feedback in Google Sheets.
5. Escalate low-scoring calls to a manager in Telegram.
6. Generate a customer email and send it only after manager approval.

## Stack

`n8n` · `Groq / Llama 3.3 70B` · `Whisper-compatible transcription` · `Google Drive` · `Google Sheets` · `Telegram` · `Gmail`

## Outcome

The case targets a 90% reduction in QA review time, saving approximately 8–12 hours per week. This result should be validated with production execution metrics.

## Modules

- `main-call-qa-workflow.json`
- `notify-manager-on-bad-ticket.json`
- `get-client-email-by-recording-url.json`
- `manager-decision-send-email.json`
