# Zambia Take-Home Pay Calculator (2026)

Work out your take-home pay in Zambia: **PAYE, NAPSA and NHIMA, shown band by band.**

**Live site:** https://zambia-take-home-pay.vercel.app

## What it does

- **Salary → take-home:** enter a basic salary and allowances, and see PAYE, NAPSA, NHIMA and your take-home pay.
- **Take-home → salary:** enter the take-home you want, and it finds the basic salary you need.
- **Monthly or yearly** figures.
- **Shows its working:** a band-by-band PAYE table, every step from gross to take-home, and what the employer pays on top.
- **Raise insight:** how much of your next K1,000 a month you would actually keep.
- **Shareable links:** every result has its own URL, e.g. `/?mode=gross&amount=15000&allow=3000&period=m`.
- **Ask about your pay:** an AI assistant (Google Gemini) that explains your result, such as why PAYE is what it is or what a raise would leave you with. It only explains pay rules and declines financial advice.
- **Private calculator:** the calculator runs in the browser. Only questions typed into the assistant, with your pay figures, are sent to Gemini.

## Rates used (2026)

| Item | Rule |
|---|---|
| PAYE (monthly) | 0% up to K5,100 · 20% K5,100–K7,100 · 30% K7,100–K9,200 · 37% above K9,200, on gross pay |
| NAPSA | 5% employee + 5% employer of gross pay, on earnings up to K37,236 a month (max K1,861.80 each) |
| NHIMA | 1% employee + 1% employer of basic salary |

Sources: [PwC Zambia 2026 Budget Bulletin](https://www.pwc.com/zm/en/assets/pdf/zambia-2026-national-budget-bulletin.pdf) · [PaySpace NAPSA ceiling 2026](https://support.payspace.com/portal/en/kb/articles/zambia-napsa-contribution-ceiling-increase-effective-january-2026) · [NHIMA](https://www.nhima.co.zm/membership/registration-steps) · [ZRA](https://www.zra.org.zm)

This is an estimate, not tax advice.

## Built with

- Plain HTML, CSS and JavaScript in one file, with no framework and no build step
- One Vercel serverless function (`api/chat.js`) that calls the Gemini API, so the API key never reaches the browser

## Files

| Path | What it is |
|---|---|
| `index.html` | The whole app |
| `favicon.svg` | Tab icon |
| `api/chat.js` | The assistant: builds the prompt from the user's figures and calls Gemini |

## Run it locally

Open `index.html` in a browser for the calculator. To run the assistant locally, use `vercel dev` with `GEMINI_API_KEY` set.

## Deploy on Vercel

1. Import this repository at [vercel.com/new](https://vercel.com/new) and click **Deploy**. No settings to change.
2. For the assistant, get a free API key at [Google AI Studio](https://aistudio.google.com), then in Vercel go to **Settings → Environment Variables** and add `GEMINI_API_KEY`.
3. Optional: add `GEMINI_MODEL` to choose a specific Gemini model.
4. Redeploy. Every push to `main` deploys automatically.

The assistant limits each visitor to 8 messages a minute and 400 characters per message.

## Updating the rates

All rates are at the top of the `<script>` in `index.html` (`BANDS`, `NAPSA_RATE`, `NAPSA_CEIL`, `NHIMA_RATE`). Change them there and update the "Rates and sources" section and the rules in `api/chat.js`.

---

Built by [Roy Kamwanza](https://roykamwanza.github.io) · [LinkedIn](https://www.linkedin.com/in/roy-kamwanza-0550b5244/) · [GitHub](https://github.com/roykamwanza)
