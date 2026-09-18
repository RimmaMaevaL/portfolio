# AI Sales Assistant

A modular sales-assistance system combining a Qdrant knowledge base with Telegram interfaces for objection handling and lead-specific call scripts.

## Modules

- Knowledge-base loader: prepares objection and case records, creates Gemini embeddings, and loads Qdrant.
- Objection-handling bot: retrieves relevant knowledge and generates a response.
- Call-script generator: accepts a Zoho Lead ID and returns a status, recommendation, call script, and key question.

## Stack

`n8n` · `Qdrant` · `Google Gemini embeddings` · `Anthropic Claude` · `Zoho CRM` · `Telegram`

## Outcome

A call script can be delivered in Telegram in under 10 seconds after a valid lead ID is submitted. A race-condition bug found during development is a strong technical case study: dependent branches must be synchronized before consuming their output.

## Modules

- `qdrant-knowledge-base-loader.json`
- `telegram-objection-handling-bot.json`
- `lead-call-script-generator.json`
