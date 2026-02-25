# AI-Augmented-Market-Intelligence-Pipeline

## Summary
This project is a high-performance automation ecosystem built on Make.com. It transforms the manual task of monitoring industry news and competitor updates into an autonomous, 24/7 intelligence engine. By orchestrating RSS feeds, Apify’s web scraping actors, and OpenAI’s GPT-4, the system discovers, extracts, and structures deep-web data into a centralized Google Sheets dashboard every 30 minutes.

## Key Accomplishments
End-to-End Autonomy: Created a "zero-touch" workflow that triggers every 30 minutes to ensure real-time data freshness.

Resilient Architecture: Implemented advanced error-handling logic (using "Break" and "Ignore" directives) to handle API timeouts and website structure changes without crashing the pipeline.

Structured Data Synthesis: Developed custom prompt engineering to convert unstructured HTML/Text into validated JSON objects for 100% database compatibility.

Operational Efficiency: Reduced manual research time by an estimated 15+ hours per week while increasing the volume of monitored sources.

## Technical Challenges Solved
Dynamic Content Extraction: Overcame anti-scraping measures by routing requests through Apify, ensuring high-fidelity data retrieval from Javascript-heavy sites.

Data Deduplication: Configured lookup logic within Google Sheets to prevent redundant processing of the same RSS items, optimizing API credit usage.

Rate Limit Optimization: Balanced the frequency of the 30-minute polling cycle with OpenAI and Apify’s concurrency limits to maintain a cost-effective operation.

## Technical Summary: "How it Works"
The workflow follows a linear logic path with multiple "safety nets" to ensure data integrity:

Ingestion & Discovery: The process begins with an RSS Feed watcher that monitors specific industry URLs. Simultaneously, a Google Sheets module checks for any manually added targets or "keywords" to watch.

Scraping Orchestration: Once a new URL is identified, the system triggers a sequence of Apify modules. These modules perform deep-scrapes of the target pages, bypassing bot-detection and extracting the raw text and metadata.

Variable Extraction (AI Layer): The raw data is passed to OpenAI (GPT-4). Using a specialized prompt, the AI identifies and extracts key variables (e.g., Company Name, Sentiment, Product Price, or Trend Category) and formats them into a JSON string.

Data Parsing: A JSON Parser module breaks down the AI's output into distinct variables that the system can map into a spreadsheet.

Final Loading & Archiving: The structured data is appended to a Google Sheets database. Multiple "Break" modules are placed throughout the final steps to ensure that if a specific row fails to update, the system pauses and retries rather than losing the data.

## Tech Stack
Automation Engine: Make.com

Data Extraction: Apify (Web Scrapers)

Artificial Intelligence: OpenAI API (GPT-4)

Database/UI: Google Sheets

Formats: JSON, RSS, Regex
