# ✅ Filter by Validity

A simple, fast workflow designed to process bulk records from a spreadsheet and filter them based on validation logic.

## 🏢 Business Problem

When handling large lists of leads, emails, or data entries, it is common to have invalid, duplicate, or malformed records. Manually sifting through spreadsheets to validate data is tedious. This workflow automates the validation process, ensuring only clean data moves forward in your funnel.

## ✨ Features

* **Manual Execution:** Triggered manually for controlled data processing.
* **Batch Validation:** Uses batch processing to handle large spreadsheets efficiently.
* **Conditional Filtering:** Employs an `If` node to strictly segregate valid records from invalid ones based on defined criteria.

## 🔄 Workflow Overview

1. **Trigger:** The workflow is triggered manually.
2. **Main Processing Steps:**
   * Uses `Split In Batches` to break down large lists of data.
   * Reads target records from Google Sheets.
   * Passes the data through an `If` node, applying logical rules (e.g., checking if an email field contains an "@" symbol or if a domain is active).
3. **Output:** The filtered data is typically routed or flagged directly back in Google Sheets as Valid/Invalid.

## 🔌 Integrations

* n8n
* Google Sheets

## 🔑 Required Credentials

* `<GOOGLE_SHEETS_OAUTH2_API>` (Google Sheets OAuth credential)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `Filter by Validity.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **Google Sheets:** Connect your account, provide the `<GOOGLE_SHEETS_ID>`, and ensure the node is pointing to the correct data column.
* **Filter Logic:** Update the `If` node to reflect your specific definition of "Valid" (e.g., Regex match for emails, length constraints, or empty field checks).

## 🎯 Example Use Case

**Email List Scrubbing:** Before launching a mass email campaign, a marketer uses this workflow to process a spreadsheet of 5,000 scraped emails. The workflow batches the list, checks for structural validity, and updates the spreadsheet with a "Valid" tag, effectively preventing high bounce rates.

## 📁 Folder Structure

```text
Filter by Validity/
├── Filter by Validity.json
└── README.md
```

## ⚠️ Notes

* Adjust the batch sizes if you are reading/writing massive amounts of data to prevent API timeouts with Google.
