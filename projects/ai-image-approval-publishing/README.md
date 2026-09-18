# AI Image Generation & Approval-Gated Publishing

A content pipeline that generates an image from a content plan, sends it for review, and publishes it to a Telegram channel only after explicit approval.

## Intended workflow

Content plan → image generation → Telegram preview → approve/reject callback → publish approved content → log decision.

## Stack

`n8n` · `Gemini / DALL·E / Leonardo` · `Telegram Bot API`

## Outcome

A human approval gate preserves editorial control while keeping content generation fast.

> The JSON export was not included in the current upload. Add it as `ai-image-approval-publishing.json` when available.
