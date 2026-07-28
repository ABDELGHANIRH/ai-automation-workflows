# 🕸️ Website Scraper & Email Extractor

An automated workflow designed to visit a list of URLs, scrape their content, and intelligently extract contact email addresses using custom code.

## 🏢 Business Problem

When building outreach lists, you often have a list of company domains but lack the actual contact email addresses. Manually visiting hundreds of websites to find a "Contact Us" email is incredibly inefficient. This workflow automates the process of parsing web pages and extracting emails at scale.

## ✨ Features

* **Bulk URL Processing:** Reads a list of target URLs directly from Google Sheets.
* **Batching System:** Processes URLs in batches to prevent server timeouts and memory overload.
* **Web Scraping:** Uses HTTP Requests to download the raw HTML of the target websites.
* **Custom Email Extraction:** Utilizes custom JavaScript to parse the HTML and regex match email patterns.
* **Data Enrichment:** Pushes the extracted emails back into the original Google Sheet.

## 🔄 Workflow Overview

1. **Trigger:** Initiated via a `Manual Trigger`.
2. **Main Processing Steps:**
   * Reads a list of URLs from Google Sheets.
   * `Split In Batches` ensures the system processes a few URLs at a time.
   * `HTTP Request` accesses the web page.
   * `Code` nodes execute JavaScript (likely regular expressions) to locate `mailto:` links or standard email formats within the text.
   * An `If` node verifies if an email was actually found.
3. **Output:** Valid extracted emails are updated in the respective row in Google Sheets.

## 🔌 Integrations

* n8n
* HTTP Request
* Google Sheets

## 🔑 Required Credentials

* `<GOOGLE_SHEETS_OAUTH2_API>` (Google Sheets OAuth credential)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `Website_Scraper_&_Email_Extractor.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **Google Sheets:** Connect the `<GOOGLE_SHEETS_ID>` and verify that your sheet has a column for the URL and an empty column to receive the Email.
* **Batch Size:** Adjust the `Split In Batches` node depending on how fast you want the scraper to run vs. the memory limits of your n8n instance.

## 🎯 Example Use Case

**B2B Lead Enrichment:** A sales team buys a list of 1,000 local business names and domains but has no contact information. They paste the URLs into a Google Sheet and trigger this workflow. The automation visits each site, searches the homepage for standard emails (like info@, contact@), and populates the spreadsheet, giving the sales team actionable leads.

## 📁 Folder Structure

```text
Website_Scraper_&_Email_Extractor/
├── Website_Scraper_&_Email_Extractor.json
└── README.md
```

## ⚠️ Notes

* **Scraping Limitations:** Simple HTTP requests may fail on sites heavily protected by Cloudflare or those that render their content entirely in JavaScript (SPAs).
* **Regex Accuracy:** The custom code might extract generic emails or occasionally pick up false positives. Manual spot-checking of the final list is recommended.
