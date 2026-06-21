# 🎯 Lead Generation Agent

An AI-powered lead generation agent built with **n8n** that automatically finds potential customers, qualifies them using AI, and saves structured lead data directly to **Google Sheets** — ready for your sales pipeline.

---

## 🚀 Features

- 🔍 **Automatically discovers** potential leads
- 🧠 **AI qualifies and scores** each lead based on relevance
- 📊 **Saves structured data** directly to Google Sheets
- 🔄 **Fully automated** — runs without manual input
- ⚡ **Real-time processing** — leads captured instantly
- 📁 **Organized output** — clean, structured data ready for outreach

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation engine |
| Anthropic Claude / Gemini | AI lead qualification & scoring |
| Google Sheets API | Lead storage and organization |

---

## 🔄 How It Works
Trigger Fires

↓

Lead Source Data Collected

↓

Sent to AI Model for Qualification

↓

AI Scores & Structures Lead Info

↓

Data Written to Google Sheets

↓

Sales Pipeline Ready

---

## ⚙️ Setup & Installation

1. Make sure you have **n8n** running (local or cloud)
2. Import the `lead-generation-agent.json` file into your n8n instance
3. Add your **LLM API key** (Anthropic or Gemini) in credentials
4. Connect your **Google Sheets account** via OAuth
5. Set your target **Google Sheet ID** in the workflow
6. **Activate** the workflow
7. Done — leads start flowing in automatically!

---

## 📁 Project Structure
lead-generation-agent/

│

├── lead-generation-agent.json   # n8n workflow file (import this)

└── README.md                    # Project documentation

---

## 🧠 AI Integration

The AI layer does the heavy lifting:
- **Qualifies leads** based on predefined criteria
- **Extracts key information** like name, company, role, contact details
- **Scores each lead** by relevance and potential value
- **Formats data cleanly** before writing to Google Sheets

---

## ⚡ Challenges & How I Solved Them

### 1. 🔑 API Credit Exhaustion Mid-Development
**Problem:** Anthropic API credits ran out during testing, completely blocking the AI qualification step.  
**Solution:** Switched to Google Gemini (free tier) as a drop-in replacement. This reinforced building workflows to be **LLM provider-agnostic** from day one.

### 2. 📊 Google Sheets Connection Issues
**Problem:** OAuth token for Google Sheets expired mid-workflow during testing, causing silent failures where leads were processed but never saved.  
**Solution:** Added proper credential management in n8n and verified the Sheets node showed a green connection status before activating the workflow.

### 3. 🔄 Workflow Naming & Organisation
**Problem:** The workflow was initially saved with a generic default name ("My workflow 2"), making it hard to manage alongside other agents.  
**Solution:** Established a clear naming convention for all agents upfront and renamed everything consistently before pushing to GitHub.

### 4. ⚠️ Rate Limiting on Free Tier
**Problem:** High-volume lead processing triggered Gemini's free-tier rate limits, causing some leads to be dropped.  
**Solution:** Documented the limitation and designed the workflow with throttling in mind. Production deployment would use a paid API tier or a request queue.

---

## 💡 Use Cases

- B2B sales prospecting
- Marketing campaign targeting
- Startup customer discovery
- Freelance client outreach

---

## 🙋‍♂️ Author

**Asad** — Software Engineer  
Building AI-powered automation tools for real-world use cases.# lead-generation-agent
AI-powered lead generation agent built with n8n that finds potential customers and saves them to Google Sheets
