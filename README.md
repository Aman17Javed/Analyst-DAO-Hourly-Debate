Analyst DAO – Hourly Debate
Overview
The Analyst DAO – Hourly Debate is an automated workflow built using n8n to provide hourly cryptocurrency trading signals. It fetches real-time price data from CoinGecko, classifies risk levels, analyzes the data using OpenAI's GPT-3.5-turbo model, logs the results to Google Sheets, and sends formatted trade signals via WhatsApp using Twilio.
Workflow Description
This workflow runs every hour and performs the following steps:

Trigger Every Hour: Initiates the workflow on an hourly schedule.
Fetch Data: Retrieves price data for selected cryptocurrencies (Bitcoin, Ethereum, Solana, Cardano, Polkadot, Binance Coin) from CoinGecko’s API, including 24-hour price changes.
Classify Data: Processes the API response to classify each coin’s risk level (Low, Medium, High) based on its 24-hour price change.
Analyzing Data: Uses OpenAI’s GPT-3.5-turbo to generate trade recommendations (Buy, Sell, Hold) based on price trends and risk levels.
Parsing the Output to JSON: Parses OpenAI’s output into structured JSON and adds timestamps.
Append Data: Logs the parsed data (coin, action, reasoning, date) to a Google Sheet for record-keeping.
Integrating Messages: Formats the parsed data into a WhatsApp-friendly message.
Sending Message to WhatsApp: Sends the formatted trade signals to a specified WhatsApp number via Twilio.

Prerequisites
To run this workflow, ensure you have:

An n8n instance set up (cloud or self-hosted).
API credentials for:
CoinGecko API: No key required (public API).
OpenAI: For the GPT-3.5-turbo model (configured in the "Analyzing Data" node).
Google Sheets: OAuth2 credentials for writing to the specified spreadsheet.
Twilio: Account credentials for sending WhatsApp messages.


A Google Sheet with a sheet named "Sheet2" for logging data.
A WhatsApp-enabled Twilio number.

Setup Instructions

Import the Workflow:

Copy the JSON content from Analyst DAO – Hourly Debate.json.
In n8n, go to Workflows > Import from File/Clipboard and paste the JSON.


Configure Credentials:

OpenAI: Set up credentials in the "Analyzing Data" node for the GPT-3.5-turbo model.
Google Sheets: Configure OAuth2 credentials in the "Append Data" node and ensure the target spreadsheet (1ZX7NRVj3J4hkcMANN8n4GuyLihYs0z70-wrK_FiSFis) is accessible.
Twilio: Add credentials in the "Sending Message to WhatsApp" node, including the Twilio phone number (+14155238886) and recipient WhatsApp number (+923034818109).


Verify Node Configurations:

Ensure the CoinGecko API URL in the "Fetch Data" node is correct.
Check the Google Sheet ID and sheet name in the "Append Data" node.
Confirm the WhatsApp message format in the "Integrating Messages" node.


Activate the Workflow:

In n8n, toggle the workflow to Active to start running it hourly.



Node Details

Trigger Every Hour (c9c0cfac-0ddf-4005-bc70-6188ccee4506): Triggers the workflow every hour.
Fetch Data (ab22fa6a-e043-4b0d-97ce-1cdb3f8769c5): Queries CoinGecko for price data.
Classify Data (ed0a3d1c-c45a-4310-88a6-fd5af6249d40): Processes price data and assigns risk levels.
Analyzing Data (1fa1be57-2d08-4b8f-a628-22a785c850ea): Uses OpenAI to generate trade recommendations.
Parsing the Output to JSON (9e858167-9d9f-411e-a5e1-0298bd63a6de): Parses and timestamps OpenAI’s output.
Append Data (39b30141-00af-41a8-ae37-626a16cb74e9): Logs data to Google Sheets.
Integrating Messages (d310ee54-c081-4a04-92d6-8e6b6b0175e4): Formats trade signals for WhatsApp.
Sending Message to WhatsApp (abff4d47-18fa-43bb-98a6-29acdaab7897): Sends the message via Twilio.

Output

Google Sheets: Trade signals are appended to "Sheet2" with columns: coin, action, reasoning, date.
WhatsApp: A formatted message with trade signals, e.g.:📊 *Crypto Trade Signals*

💰 *BITCOIN*
Action: Buy
Reason: Strong upward momentum with low risk.
Date: 8/20/2025, 3:43:00 PM

💰 *ETHEREUM*
Action: Hold
Reason: Stable price with medium risk.
Date: 8/20/2025, 3:43:00 PM



Notes

The workflow assumes the CoinGecko API is available and the listed coins (Bitcoin, Ethereum, etc.) are valid.
Ensure the Google Sheet has appropriate permissions for the n8n service account.
The Twilio node requires a WhatsApp-enabled number and a recipient who has opted into WhatsApp messaging.
Monitor OpenAI usage to avoid exceeding API limits.

Troubleshooting

API Errors: Check CoinGecko API status or rate limits.
Google Sheets Errors: Verify sheet permissions and column mappings.
Twilio Errors: Confirm the recipient number is WhatsApp-enabled and credentials are valid.
OpenAI Errors: Ensure the API key is active and the model is accessible.

License
This workflow is provided as-is for educational purposes. Use at your own risk.
