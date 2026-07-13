# 🐦 AI Twitter Automation

An automated, scheduled workflow that interacts with Twitter and uses AI to generate content, analyze tweets, or manage interactions dynamically.

## 🏢 Business Problem

Maintaining an active presence on X (formerly Twitter) requires constant monitoring, content creation, and engagement. Doing this manually drains time. This workflow automates Twitter interactions—whether it's fetching tweets for analysis, scheduling AI-generated posts, or responding to mentions—all centralized and logged into a spreadsheet.

## ✨ Features

* **Scheduled Execution:** Runs on autopilot at specified intervals.
* **Native Twitter Integration:** Interacts directly with the Twitter API to post or fetch tweets.
* **AI Content Generation:** Employs LangChain and Google Gemini to craft engaging tweets or analyze fetched sentiment.
* **Database Tracking:** Logs all activities (posts made, tweets fetched) directly into Google Sheets.

## 🔄 Workflow Overview

1. **Trigger:** A `Schedule Trigger` initiates the sequence.
2. **Main Processing Steps:**
   * An `HTTP Request` or native `Twitter` node interacts with the X API.
   * LangChain and Google Gemini generate text, reply suggestions, or summarize content.
   * A `Limit` node acts as a safeguard to prevent spamming.
   * `If` logic dictates routing (e.g., "Is this a positive mention?").
3. **Output:** The final action is taken on Twitter, and the data is archived into Google Sheets.

## 🔌 Integrations

* n8n
* Twitter (X)
* LangChain
* Google Gemini
* Google Sheets
* HTTP Request

## 🔑 Required Credentials

* `<TWITTER_OAUTH2_API>` (Twitter Developer Credentials)
* `<GOOGLE_SHEETS_OAUTH2_API>` (Google Sheets OAuth credential)
* `<GOOGLE_GEMINI_API_KEY>` (Google AI API Key)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `Twitter.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **Twitter API:** Ensure your Twitter Developer app has the necessary read/write permissions.
* **AI Model:** Configure the system prompt in Gemini to match your brand voice.
* **Schedule:** Adjust the `Schedule Trigger` to your preferred posting/fetching frequency.
* **Google Sheets:** Connect the `<GOOGLE_SHEETS_ID>` to log the activity.

## 🎯 Example Use Case

**Automated Content Pipeline:** A content creator wants to post twice a day. They have a Google Sheet of rough ideas. Every 12 hours, the `Schedule Trigger` fires, pulling an idea from the Sheet. Gemini expands the idea into a 280-character tweet with relevant hashtags. The `Twitter` node posts it, and the Sheet is updated with the live tweet URL.

## 📁 Folder Structure

```text
Twitter/
├── Twitter.json
└── README.md
```

## ⚠️ Notes

* Be strictly compliant with Twitter's Developer Terms of Service to avoid account suspension, especially concerning automated replies or high-volume posting.
