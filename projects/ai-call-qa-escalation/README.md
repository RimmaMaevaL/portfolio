<div align="center">

# 🧾 AI Call QA & Escalation System

### AI-powered quality assurance for support calls, without drowning managers in manual review

<p>
  <a href="../../">← Back to portfolio</a>
  ·
  <a href="https://github.com/RimmaMaevaL/portfolio/tree/main/projects/ai-call-qa-escalation">Browse project files</a>
</p>

<img src="https://img.shields.io/badge/n8n-automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />
<img src="https://img.shields.io/badge/Groq-Llama%203.3%2070B-7C3AED?style=for-the-badge" alt="Groq Llama 3.3 70B" />
<img src="https://img.shields.io/badge/Whisper-transcription-0F766E?style=for-the-badge" alt="Whisper" />
<img src="https://img.shields.io/badge/Google%20Drive%20%2B%20Sheets-4285F4?style=for-the-badge&logo=google-drive&logoColor=white" alt="Google Drive and Sheets" />

</div>

---

## ✨ What this project does

This workflow reviews customer-support calls with AI, scores them against critical QA criteria, and escalates weak results before issues become bigger operational problems.

The goal is simple: reduce review time, keep quality consistent, and make only the truly risky calls require human intervention.

## 🎯 The business challenge

Manual call reviews consumed hours every week, while serious service issues could be discovered too late. Managers needed a faster, structured way to detect weak conversations and respond early.

## 🔄 Workflow at a glance

```mermaid
flowchart LR
    A[📁 New Google Drive recording] --> B[🎧 Download & transcribe]
    B --> C[🧠 Evaluate against 8 QA criteria]
    C --> D[📊 Save structured scores to Sheets]
    D --> E{Low score?}
    E -->|Yes| F[🚨 Notify manager in Telegram]
    E -->|No| G[✅ Continue]
    F --> H[✉️ Generate customer reply]
    H --> I{Manager approval}
    I -->|Approved| J[📨 Send email]
    I -->|Rejected| K[🛑 Hold]
```

## 🧠 QA dimensions evaluated

The AI scores the transcript across:

- greetings
- active listening
- needs discovery
- empathy
- expertise
- solution clarity
- next steps
- closing quality

This makes the signal measurable and easier to act on compared with a vague “good / bad” verdict.

## 🛠️ Technology stack

| Component | Role |
|---|---|
| **n8n** | Workflow orchestration and automation |
| **Groq / Llama 3.3 70B** | call evaluation and reasoning |
| **Whisper-compatible transcription** | transcript generation |
| **Google Drive** | source audio files |
| **Google Sheets** | structured QA logs |
| **Telegram** | manager escalation |
| **Gmail** | customer follow-up |

## 📦 Included workflow modules

| File | Purpose |
|---|---|
| [`main-call-qa-workflow.json`](main-call-qa-workflow.json) | main QA evaluation workflow |
| [`notify-manager-on-bad-ticket.json`](notify-manager-on-bad-ticket.json) | escalation logic for weak calls |
| [`get-client-email-by-recording-url.json`](get-client-email-by-recording-url.json) | fetch customer contact details |
| [`manager-decision-send-email.json`](manager-decision-send-email.json) | human-approved response path |

## ✅ Outcome

The case targets a 90% reduction in QA review time, saving roughly 8–12 hours per week. In production, this kind of workflow is strongest when paired with real review baselines and manager feedback loops.

---

<div align="center">

**Faster review. Better quality control. More time for real customer recovery.**

</div>
