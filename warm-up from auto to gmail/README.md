# 🔥 Email Warm-up & Interaction Engine

An advanced inbox warming workflow that utilizes AI chat triggers to generate contextually relevant emails, dispatch them, and handle automated replies between inboxes.

## 🏢 Business Problem

When launching new outreach domains, sending cold emails immediately leads to spam placement. Domains need to be "warmed up" by establishing a pattern of healthy, conversational email traffic. This workflow generates high-quality, AI-driven conversational threads between specific inboxes to rapidly build sender reputation.

## ✨ Features

* **Manual & Chat Triggers:** Can be initiated manually or via a chat interface for testing.
* **AI Conversation Generation:** Uses Google Gemini and LangChain to draft realistic, multi-turn conversational emails.
* **Multi-Provider Routing:** Uses a `Switch` node to route actions differently based on whether it is sending via SMTP or receiving via Gmail.
* **Automated Dispatch & Delay:** Integrates `Wait` nodes to simulate human delay before sending.

## 🔄 Workflow Overview

1. **Trigger:** Initiated via `Manual Trigger` or `Chat Trigger`.
2. **Main Processing Steps:**
   * LangChain and Google Gemini generate the core email content, structured by an `Output Parser`.
   * Custom `Code` formats the generated text.
   * A `Switch` node routes the message logic.
   * A `Wait` node introduces a random pause.
3. **Output:** The email is dispatched either through the generic `Email Send` node or directly via `Gmail`.

## 🔌 Integrations

* n8n
* Gmail
* Email (SMTP)
* LangChain
* Google Gemini

## 🔑 Required Credentials

* `<SMTP_CREDENTIALS>` (For sending outgoing emails)
* `<GMAIL_OAUTH2_API>` (For Google Workspace inbox interaction)
* `<GOOGLE_GEMINI_API_KEY>` (Google AI API Key)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `warm-up from auto to gmail.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **Email Connections:** Set up both your sending SMTP credentials and the receiving Gmail OAuth.
* **AI Persona:** Adjust the Gemini prompt so the generated emails sound like typical business correspondence in your niche.
* **Routing Logic:** Ensure the `Switch` node is correctly configured to match your specific inbox setup.

## 🎯 Example Use Case

**Closed-Loop Domain Warming:** An agency has a primary Gmail account and a new secondary domain (SMTP). This workflow triggers a process where Gemini drafts a realistic question about a service. It sends the email from the new domain to the Gmail account. A secondary branch or workflow handles the reply. This automated back-and-forth builds a flawless sending reputation for the new domain.

## 📁 Folder Structure

```text
warm-up from auto to gmail/
├── warm-up from auto to gmail.json
└── README.md
```

## ⚠️ Notes

* Ensure your AI is set to generate harmless, standard business text to avoid triggering spam filters with aggressive or sensitive keywords.
