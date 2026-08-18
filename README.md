#🎯 Complete 100% Autonomous Lead Gen & AI Outreach Agent

An end-to-end n8n automation that finds leads, enriches them with AI, sends personalized cold outreach, tracks replies, and alerts you the moment a lead shows interest — all without manual intervention.

### ⚠️ Security note: Before importing or sharing this workflow, remove/rotate any hardcoded API keys found in the JSON (e.g. in the HTTP Request node's headers). Never commit real API keys, OAuth credential IDs, or webhook secrets to a public repo — use n8n's credential store or environment variables instead.

🧠 What This Workflow Does

This is a single n8n workflow made up of three connected pipelines:

## 1️⃣ Lead Generation & Enrichment
A form collects your target niche/industry, location, and offer/value proposition.
Searches Google (via Serper API) for matching LinkedIn profiles.
An AI agent (GPT-4.1-mini) parses each result to extract and clean the lead's name, job title, company, predicts a likely business email, summarizes their role, and drafts a personalized cold outreach message.
All enriched leads are saved to a Google Sheet with a pending status.
## 2️⃣ Automated Daily Outreach
A scheduled trigger runs once a day, pulling all pending leads from the sheet.
Loops through each lead:
Validates the email format.
Generates a human-sounding cold pitch via AI.
Sends the email through Gmail.
Updates the lead's status in the sheet.
Waits a few minutes between sends to mimic natural, human-paced outreach (and avoid spam flags).
Leads with invalid emails are marked and skipped automatically.
## 3️⃣ Reply Monitoring & Live Alerts
Watches your Gmail inbox for replies.
An AI sentiment classifier reads each reply and determines if the lead is genuinely interested.
If interested, you get an instant Telegram alert with the lead's info and reply content, prompting you to jump in and close the conversation while it's hot.
🔧 Tech Stack / Integrations
Purpose	Service
Lead search	Serper (Google Search API)
AI enrichment & copywriting	OpenAI (GPT-4.1-mini) via LangChain nodes
Lead storage/tracking	Google Sheets
Outreach delivery	Gmail
Reply monitoring	Gmail Trigger
Sentiment classification	OpenAI
Live notifications	Telegram Bot
⚙️ Setup Instructions
Import the workflow into your n8n instance (Workflows → Import from File).
Connect the following credentials in n8n:
Serper API key
OpenAI API key
Google Sheets OAuth2
Gmail OAuth2
Telegram Bot token + chat ID
Create a Google Sheet with columns: Name, Company, Email, LinkedIn Profile, Snippet, Role, Status, Proposal Message, and link it in the relevant nodes.
Update the Telegram chatId to your own.
Activate the workflow.
Trigger it by submitting the lead-gen form with your niche, location, and offer.
# 📁 Files
Complete_100_Autonomous_Lead_Gen_AI_Outreach_Agent.json — the exported n8n workflow. Import directly into n8n.
💡 Customization Ideas
Swap Serper for another search/scraping source (Apollo, Apify, etc.).
Add LinkedIn message outreach as an alternative/parallel channel to email.
Add a CRM sync step (HubSpot, Airtable, Notion) alongside Google Sheets.
Adjust the AI prompts to match your brand voice or industry vertical.
# ⚠️ Disclaimer

This workflow automates cold outreach. Make sure your usage complies with applicable anti-spam laws (e.g. CAN-SPAM, GDPR) and the terms of service of the platforms involved (Google, LinkedIn, Telegram, etc.). Use responsibly.
