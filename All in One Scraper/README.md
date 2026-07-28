# 🕷️ All in One Scraper

A comprehensive data scraping automation designed to fetch, process, and store web data dynamically.

## 🏢 Business Problem

Manual data extraction from web sources is time-consuming and prone to errors. Businesses need a reliable, automated way to extract large datasets, process them sequentially without hitting rate limits, and store the structured data directly into a spreadsheet for analysis or outreach.

## ✨ Features

* **Automated Data Extraction:** Uses HTTP requests to scrape data dynamically.
* **Batch Processing:** Handles large datasets by splitting them into manageable batches to avoid rate limits or timeouts.
* **Custom Code Processing:** Utilizes custom JavaScript nodes to format, clean, and structure the scraped data.
* **Direct Database Integration:** Seamlessly pushes the cleaned data into Google Sheets.

## 🔄 Workflow Overview

1. **Trigger:** The workflow is initiated via a manual trigger.
2. **Main Processing Steps:** 
   * Prepares the data using `Set` and custom `Code` nodes.
   * Uses `Split In Batches` to handle pagination or bulk data scraping.
   * `HTTP Request` nodes perform the actual scraping or API calls.
   * Adds `Wait` nodes to respect server rate limits and avoid bans.
   * Filters and formats data using `If` and `Code` logic.
3. **Output:** The final structured data is appended or updated directly in Google Sheets.

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
4. Select the `All in One Scraper.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **Google Sheets:** Connect your Google account and select the correct `<GOOGLE_SHEETS_ID>` and worksheet.
* **HTTP Requests:** Verify the target URL/Endpoint for the scraper and adjust any headers or authentication tokens if necessary.
* **Batch Settings:** Adjust the batch size in the `Split In Batches` node depending on your API rate limits.

## 🎯 Example Use Case

**Lead Generation & Competitor Tracking:** A marketing agency triggers this workflow to scrape a list of directories or competitor websites. The workflow systematically processes thousands of pages, extracts key contact information, and cleanly organizes it into a centralized Google Sheet for the sales team to review.

## 📁 Folder Structure

```text
All in One Scraper/
├── All in One Scraper.json
└── README.md
```

## ⚠️ Notes

* **Rate Limiting:** Be mindful of the target website's `robots.txt` and rate limits. The `Wait` node is crucial to prevent IP bans.
* **Dynamic HTML Changes:** If scraping raw HTML, the custom `Code` node may need updates if the target website changes its structure.
