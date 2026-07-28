# 🤖 AI Gmail Auto-Replier (Warm-up)

An advanced, AI-powered email automation workflow designed to simulate human conversation and warm up a Gmail inbox to improve deliverability.

## 🏢 Business Problem

Brand new email domains or inboxes often suffer from poor sender reputation, causing legitimate outreach emails to land in spam folders. The traditional solution is "domain warming"—sending and replying to emails gradually to build trust. This workflow automates that process using an AI agent to read incoming emails and generate contextually relevant, human-like replies.

## ✨ Features

* **Inbox Monitoring:** Automatically triggers when a new email arrives in a specified Gmail account.
* **AI Agent Integration:** Uses LangChain and Google Gemini to comprehend the incoming email context.
* **Human-Like Responses:** Generates nuanced, varied, and natural-sounding replies to build sender reputation.
* **Automated Dispatch:** Directly sends the AI-generated response via Gmail.

## 🔄 Workflow Overview

1. **Trigger:** A `Gmail Trigger` monitors the inbox for new incoming messages.
2. **Main Processing Steps:**
   * Reads the email content using `Email Read Imap` and `Gmail`.
   * A `Wait` node introduces a random delay to simulate natural human response times.
   * LangChain and Google Gemini evaluate the email content.
   * An AI Agent formulates a contextually appropriate reply.
   * An `If` node checks safety and conditions before sending.
3. **Output:** The response is sent via the `Email Send` node.

## 🔌 Integrations

* n8n
* Gmail
* LangChain
* Google Gemini

## 🔑 Required Credentials

* `<GMAIL_OAUTH2_API>` (Google/Gmail OAuth credential)
* `<GOOGLE_GEMINI_API_KEY>` (Google AI API Key)
* `<IMAP_CREDENTIALS>` (If required for specific inbox reading)
* `<SMTP_CREDENTIALS>` (If using basic SMTP for sending)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `Gmail Auto-Replier (Warm-up).json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **Gmail Connection:** Authenticate your Google account for both triggering and sending.
* **AI Model:** Provide your Gemini API key and adjust the agent's system prompt to dictate the "persona" of the warm-up replies.
* **Wait Nodes:** Configure the delay to match your desired sending velocity.

## 🎯 Example Use Case

**Automated Domain Warming:** An agency purchases a new domain for cold outreach. They set up this workflow to monitor an inbox. When test emails (or emails from warming pools) arrive, the workflow waits 15 minutes, uses Gemini to read the message, generates a friendly, casual 3-sentence reply, and sends it back. This activity signals to ISPs that the inbox is active and legitimate.

## 📁 Folder Structure

```text
Gmail Auto-Replier (Warm-up)/
├── Gmail Auto-Replier (Warm-up).json
└── README.md
```

## ⚠️ Notes

* Ensure your AI prompts prevent the agent from agreeing to malicious requests or sending inappropriate content.
* Monitor API costs associated with LangChain and Google Gemini.
