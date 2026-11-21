# n8n AI Expense Tracker

An n8n automation that turns a plain text message like `150 taka rickshaw vara` into a structured expense row in Google Sheets. Send the message to a Telegram bot and get a confirmation reply.

## How it works

1. You send a message to the Telegram bot, in Bangla, Banglish, or English.
2. The **AI Agent** (Google Gemini) reads the message and extracts the amount, category, and a short note.
3. A **Structured Output Parser** forces the AI reply into clean JSON fields.
4. A **Google Sheets** node appends a new row (Date, Amount, Category, Note).
5. The bot replies, for example: `Saved: 150 BDT, Transport ✅`.

## Tools used

- [n8n](https://n8n.io) (Cloud)
- Google Gemini (chat model)
- Telegram Bot API
- Google Sheets

## Categories

Food, Transport, Shopping, Bills, Health, Education, Entertainment, Other.

## Setup

1. Create a Google Sheet with the headers `Date`, `Amount`, `Category`, `Note` in the first row.
2. Create a Telegram bot with [@BotFather](https://t.me/BotFather) and copy the token.
3. Get a free Gemini API key from Google AI Studio.
4. In n8n, go to **Workflows > Import from file** and choose `ai-expense-tracker.json`.
5. Connect your own credentials: Telegram, Google Gemini, and Google Sheets.
6. In the Google Sheets node, select your own spreadsheet and sheet.
7. In the Gemini node, choose an available Gemini model (model names change over time).
8. Click **Publish** to activate the workflow.

## Example

| Message | Date | Amount | Category | Note |
|---|---|---|---|---|
| 150 taka rickshaw vara | 2026-11-21 | 150 | Transport | rickshaw |
| 80 taka chai khelam | 2026-11-21 | 80 | Food | chai |

## Notes

- The workflow also contains a Chat Trigger for testing inside n8n.
- Gemini's free tier has daily limits, so replies can fail with a `429` error when the limit is reached.
- No credentials or API keys are included in this repository. Connect your own accounts after importing.

## Possible improvements

- Monthly total per category.
- Budget alerts when spending crosses a limit.
- Support for voice notes.

