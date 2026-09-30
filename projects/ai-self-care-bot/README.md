<div align="center">

# 🧘 AI Self-Care Bot

### A personal wellness assistant that turns daily check-ins into structured actions

<p>
  <a href="../../">← Back to portfolio</a>
  ·
  <a href="https://github.com/RimmaMaevaL/portfolio/tree/main/projects/ai-self-care-bot">Browse project files</a>
</p>

<img src="https://img.shields.io/badge/n8n-workflow-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />
<img src="https://img.shields.io/badge/Groq%20%2F%20LLM-7C3AED?style=for-the-badge" alt="Groq LLM" />
<img src="https://img.shields.io/badge/Telegram-bot-28A7E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram" />
<img src="https://img.shields.io/badge/Google%20Sheets-logging-0F766E?style=for-the-badge" alt="Google Sheets" />

</div>

---

## ✨ What this project does

This personal Telegram bot checks mood and energy, chooses suitable self-care tasks, generates contextual AI suggestions, logs daily state, accepts notes, and provides weekly statistics.

It is a lightweight example of how AI can support daily wellbeing in a structured and consistent way.

## 🎯 The business challenge

People often know they need a reset, but they do not have a simple system for turning vague feelings into concrete, repeatable actions. This bot helps by turning a daily mood check into a guided, practical routine.

## 🔄 Workflow at a glance

```mermaid
flowchart LR
    A[📱 Telegram check-in] --> B[🧠 Evaluate mood + energy]
    B --> C[🧩 Select self-care task]
    C --> D[✨ Generate contextual AI suggestion]
    D --> E[📊 Save daily state in Sheets]
    E --> F[📈 Weekly summary]
```

## 🧠 Honest technical reflection

The workflow demonstrates context-aware suggestions rather than generic advice. It is a solid MVP, and the next logical improvement is adding a true history-based recommendation layer instead of relying only on a demo weekly dataset.

## 🛠️ Technology stack

| Component | Role |
|---|---|
| **n8n** | workflow orchestration |
| **Groq / LLM API** | contextual suggestions and reasoning |
| **Telegram** | user interaction layer |
| **Google Sheets** | daily state and statistics log |

## 📦 Included workflow modules

| File | Purpose |
|---|---|
| [`ai-self-care-bot.json`](ai-self-care-bot.json) | main self-care workflow |

## ✅ Outcome

The bot helps turn a vague feeling into a concrete, repeatable wellness action. It is a useful example of AI applied to personal routines, habit loops, and self-awareness.

---

<div align="center">

**Healthy routines start with simple, consistent check-ins.**

</div>
