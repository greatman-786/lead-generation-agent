# 🎯 Lead Generation Agent

An n8n workflow that takes incoming lead data, qualifies and scores it with an LLM, and writes structured results straight to Google Sheets — ready for a sales pipeline.

## 🚀 What it does

- Receives lead data by webhook
- Qualifies and scores each lead with an LLM
- Writes structured rows to Google Sheets
- Runs unattended once activated
- Processes each lead as it arrives

## 🛠️ Tech stack

| Tool | Purpose |
|---|---|
| n8n | Workflow automation engine |
| Anthropic Claude / Gemini | Lead qualification and scoring |
| Google Sheets API | Lead storage |

## 🔄 How it works

```
Webhook receives lead data
        ↓
Sent to LLM for qualification
        ↓
LLM scores and structures the lead
        ↓
Row written to Google Sheets
```

## ⚙️ Setup

1. Have n8n running, local or cloud
2. Import `lead-generation-agent.json` into your n8n instance
3. Add your LLM API key (Anthropic or Gemini) in credentials
4. Connect your Google Sheets account via OAuth
5. Set your target Google Sheet ID in the workflow
6. Activate the workflow

This repo is the workflow export, not a hosted service — you run it in your own n8n instance.

## 📁 Files

```
lead-generation-agent/
├── lead-generation-agent.json   # the n8n workflow — import this
└── README.md
```

## 🧠 What the LLM layer does

- Qualifies leads against the criteria defined in the workflow
- Extracts name, company, role and contact details
- Scores each lead by relevance
- Formats the data before it reaches Google Sheets

## ⚡ Problems I hit, and what I did

**1. Ran out of Anthropic credits mid-build.** The qualification step stopped dead. Switched to Gemini's free tier as a drop-in replacement — which is the argument for keeping the LLM provider swappable from the start.

**2. Google Sheets OAuth token expired during testing.** Worse than a crash: leads were processed and then silently not saved. Fixed the credentials and now check the Sheets node shows green before activating anything.

**3. The workflow was called "My workflow 2".** Unmanageable once you have several. Set a naming convention and renamed everything before pushing.

**4. Gemini free-tier rate limits dropped leads under volume.** I've documented the limit rather than hidden it. A production run needs a paid tier or a request queue.

## 💡 Use cases

B2B prospecting · marketing campaign targeting · startup customer discovery · freelance client outreach

---

**Asad Ullah** — AI automation and QA engineer. [Portfolio](https://asad-portfolio-drab.vercel.app) · [GitHub](https://github.com/greatman-786)
