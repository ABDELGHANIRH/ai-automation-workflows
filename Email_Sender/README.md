# 📧 Scheduled Email Sender

An automated workflow that continuously monitors a spreadsheet and dispatches customized emails on a schedule.

## 🏢 Business Problem

Sending follow-up emails, newsletters, or cold outreach campaigns manually is inefficient and difficult to scale. This workflow completely automates the email dispatch process based on dynamic data stored in a spreadsheet, ensuring timely communication without manual intervention.

## ✨ Features

* **Scheduled Execution:** Runs automatically at predefined intervals using a cron job or interval schedule.
* **Data-Driven Dispatch:** Pulls recipient data directly from Google Sheets.
* **Conditional Logic:** Uses switch nodes to route different types of emails or handle varying follow-up sequences.
* **Native Email Integration:** Sends emails directly through n8n's native email node (SMTP/IMAP).

## 🔄 Workflow Overview

1. **Trigger:** A `Schedule Trigger` starts the workflow at specific times.
2. **Main Processing Steps:**
   * Reads target leads or recipients from Google Sheets.
   * A `Limit` node ensures only a specific number of emails are sent per execution (ideal for warming up domains or preventing spam flags).
   * A `Switch` node routes the data based on conditions (e.g., whether it's a first contact or a follow-up).
3. **Output:** Sends the formulated email via the `Email Send` node.

## 🔌 Integrations

* n8n
* Google Sheets
* Email (SMTP)

## 🔑 Required Credentials

* `<GOOGLE_SHEETS_OAUTH2_API>` (Google Sheets OAuth credential)
* `<SMTP_CREDENTIALS>` (Email SMTP credentials)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `Email_Sender.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **SMTP Credentials:** Connect your email provider by entering your `<SMTP_USERNAME>`, `<SMTP_PASSWORD>`, and host details.
* **Google Sheets:** Connect your account and provide the `<GOOGLE_SHEETS_ID>`. Ensure your sheet has columns like Email, Name, and Status.
* **Schedule:** Adjust the `Schedule Trigger` to your desired frequency (e.g., every hour, daily at 9 AM).

## 🎯 Example Use Case

**Cold Outreach Automation:** A sales representative wants to send 50 personalized emails per day. They populate a Google Sheet with leads. The workflow runs daily, pulls 50 unprocessed leads using the `Limit` node, sends a customized email template to each, and updates the sheet to mark them as "Sent".

## 📁 Folder Structure

```text
Email_Sender/
├── Email_Sender.json
└── README.md
```

## ⚠️ Notes

* Keep an eye on your email provider's daily sending limits to avoid getting your account suspended.
* Ensure your domain has proper SPF, DKIM, and DMARC records set up for optimal deliverability.
