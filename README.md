# Kwacha Net

Kwacha Net is a take-home pay calculator for Zambia. It shows how PAYE, NAPSA and NHIMA are worked out from a salary and explains each result with an AI assistant.

**Live:** https://kwacha-net.vercel.app

## Features

- **Salary to take-home:** enter a basic salary and allowances to see PAYE, NAPSA, NHIMA and take-home pay.
- **Take-home to salary:** enter a target take-home and get the basic salary required.
- **Full breakdown:** PAYE band by band, every step from gross to take-home, and the employer's contributions.
- **Pay assistant:** answers questions about a result, such as why PAYE is a given amount or what a raise would leave. It explains pay rules only and does not give financial advice.
- **Monthly and yearly views.**
- **Shareable results:** every result has its own URL, for example `/?mode=gross&amount=15000&allow=3000&period=m`.

## Rates (2026 tax year)

| Item | Rule |
|---|---|
| PAYE (monthly) | 0% up to K5,100 · 20% K5,100–K7,100 · 30% K7,100–K9,200 · 37% above K9,200, on gross pay |
| NAPSA | 5% employee + 5% employer of gross pay, on earnings up to K37,236 a month (maximum K1,861.80 each) |
| NHIMA | 1% employee + 1% employer of basic salary |

Sources: [PwC Zambia 2026 Budget Bulletin](https://www.pwc.com/zm/en/assets/pdf/zambia-2026-national-budget-bulletin.pdf) · [PaySpace: NAPSA ceiling 2026](https://support.payspace.com/portal/en/kb/articles/zambia-napsa-contribution-ceiling-increase-effective-january-2026) · [NHIMA](https://www.nhima.co.zm/membership/registration-steps) · [Zambia Revenue Authority](https://www.zra.org.zm)

Results are estimates and are not tax advice. They exclude pension top-ups, loans, union dues and special tax credits.

## Tech stack

- HTML, CSS and JavaScript in a single page, with no framework or build step
- A Node.js serverless function on Vercel (`api/chat.js`)
- Google Gemini API for the pay assistant

## Project structure

| Path | Purpose |
|---|---|
| `index.html` | The calculator: layout, styles and logic |
| `api/chat.js` | Serverless function that builds the assistant's prompt from the user's figures and calls Gemini |
| `favicon.svg` | Site icon |

## Running locally

Open `index.html` in a browser to use the calculator. To run the assistant as well, use the [Vercel CLI](https://vercel.com/docs/cli):

```bash
vercel dev
```

with `GEMINI_API_KEY` set in your environment.

## Deployment

1. Import the repository into [Vercel](https://vercel.com/new) and deploy. No build settings are needed.
2. Add these environment variables under **Settings → Environment Variables**:

| Variable | Required | Description |
|---|---|---|
| `GEMINI_API_KEY` | Yes | API key from [Google AI Studio](https://aistudio.google.com) |
| `GEMINI_MODEL` | No | Overrides the default Gemini model |

3. Redeploy. Every push to `main` deploys automatically.

## Security and privacy

- The Gemini API key is stored on the server and never sent to the browser.
- The calculator runs entirely in the browser. Only questions typed into the assistant, together with the calculated figures, are sent to Gemini.
- The assistant allows 8 messages per minute per visitor and 400 characters per message.

## Updating the rates

The rates are defined at the top of the `<script>` in `index.html` (`BANDS`, `NAPSA_RATE`, `NAPSA_CEIL`, `NHIMA_RATE`). When they change, also update the **Rates and sources** section of the page and the rules in `api/chat.js`.
