# AI Lead Qualification & Marketing Automation

A beauty-salon lead pipeline that receives Wix submissions, stores and enriches them, creates a Zoho CRM lead, notifies the team, classifies intent, and synchronizes contacts with Klaviyo.

## Workflow

Wix webhook → normalized lead object → Google Sheets and Zoho CRM → Telegram notification → Hot/Warm/Cold classification → Klaviyo list segmentation.

## Stack

`n8n` · `Wix` · `Zoho CRM` · `Klaviyo API` · `Google Sheets` · `Telegram` · `OpenRouter`

## Outcome

The supplied project estimate is an approximately 80% reduction in manual data handling, with processing reduced from minutes to seconds. These figures should be validated with production metrics.

## Workflow file

- `wix-lead-marketing-automation.json`
