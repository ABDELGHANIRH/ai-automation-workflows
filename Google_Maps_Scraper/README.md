# 🗺️ AI-Powered Google Maps Scraper

A robust automation that scrapes local business data from Google Maps, cleans it, and uses AI to extract and structure the information into a spreadsheet.

## 🏢 Business Problem

Finding and compiling lists of local businesses (B2B leads) from Google Maps is tedious. Raw map scraping often yields messy, unstructured data with missing or malformed fields. This workflow completely automates the scraping process and utilizes AI to parse, clean, and perfectly structure the data before saving it.

## ✨ Features

* **Automated Map Extraction:** Scrapes raw business data dynamically using HTTP Requests.
* **AI Data Structuring:** Uses Google Gemini and LangChain to parse messy text and extract precise data points (e.g., categorizing business types, formatting phone numbers).
* **Deduplication:** Automatically filters out duplicate listings to maintain database hygiene.
* **Structured Output:** Pushes clean, ready-to-use data into Google Sheets.

## 🔄 Workflow Overview

1. **Trigger:** The workflow starts, preparing a list of search queries or locations.
2. **Main Processing Steps:**
   * Fetches raw data using an `HTTP Request` node.
   * `Split In Batches` and `Wait` nodes handle large data volumes to prevent rate limits.
   * `Code` and `Filter` nodes do initial cleaning.
   * A `Remove Duplicates` node ensures unique entries.
   * LangChain and Google Gemini analyze the raw snippets and use a `Structured Output Parser` to format the data cleanly.
3. **Output:** The perfectly structured lead data is appended to Google Sheets.

## 🔌 Integrations

* n8n
* HTTP Request
* LangChain
* Google Gemini
* Google Sheets

## 🔑 Required Credentials

* `<GOOGLE_SHEETS_OAUTH2_API>` (Google Sheets OAuth credential)
* `<GOOGLE_GEMINI_API_KEY>` (Google AI API Key)
* `<API_KEY>` (If utilizing a third-party Google Maps scraping API)

## 📥 How to Import

1. Open your n8n instance.
2. Click on **Workflows** > **Add Workflow**.
3. Click on the options menu (top right) and select **Import from File**.
4. Select the `Google_Maps_Scraper.json` file from this folder.
5. Reconnect your credentials when prompted.

## ⚙️ Configuration

Before running the workflow, ensure you have configured the following:
* **API Endpoints:** Configure the HTTP Request node with your target URL or Maps API endpoint.
* **AI Extraction:** Review the LangChain Prompt and Structured Output Parser to ensure Gemini is extracting the specific fields you need (e.g., Name, Phone, Address, Website).
* **Google Sheets:** Connect your `<GOOGLE_SHEETS_ID>` and ensure columns match the structured output from Gemini.

## 🎯 Example Use Case

**Local B2B Lead Generation:** A marketing agency wants to pitch SEO services to local dentists. They trigger the workflow with a search term. The HTTP node scrapes 200 listings. The deduplicator removes 15 duplicates. Google Gemini then reads the raw text, cleanly separating the clinic name, address, and formatting the phone number perfectly, saving a pristine list directly to Google Sheets for the sales team.

## 📁 Folder Structure

```text
Google_Maps_Scraper/
├── Google_Maps_Scraper.json
└── README.md
```

## ⚠️ Notes

* Ensure you comply with Google Maps Terms of Service when scraping data.
* Complex AI parsing operations with Gemini can consume significant API tokens if the raw scraped text is extremely large.
