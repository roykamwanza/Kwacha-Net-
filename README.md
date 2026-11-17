# Zambia Take-Home Pay Calculator (2026)

Work out your take-home pay in Zambia: **PAYE, NAPSA and NHIMA, shown band by band.**

**Live site:** https://roykamwanza.github.io/zambia-take-home-pay/

## What it does

- **Salary → take-home:** enter a basic salary and allowances, and see PAYE, NAPSA, NHIMA and your take-home pay.
- **Take-home → salary:** enter the take-home you want, and it finds the basic salary you need.
- **Monthly or yearly** figures.
- **Shows its working:** a band-by-band PAYE table, every step from gross to take-home, and what the employer pays on top.
- **Raise insight:** how much of your next K1,000 a month you would actually keep.
- **Shareable links:** every result has its own URL, e.g. `/?mode=gross&amount=15000&allow=3000&period=m`.
- **Private:** everything runs in the browser. Nothing is sent to a server.

## Rates used (2026)

| Item | Rule |
|---|---|
| PAYE (monthly) | 0% up to K5,100 · 20% K5,100–K7,100 · 30% K7,100–K9,200 · 37% above K9,200, on gross pay |
| NAPSA | 5% employee + 5% employer of gross pay, on earnings up to K37,236 a month (max K1,861.80 each) |
| NHIMA | 1% employee + 1% employer of basic salary |

Sources: [PwC Zambia 2026 Budget Bulletin](https://www.pwc.com/zm/en/assets/pdf/zambia-2026-national-budget-bulletin.pdf) · [PaySpace NAPSA ceiling 2026](https://support.payspace.com/portal/en/kb/articles/zambia-napsa-contribution-ceiling-increase-effective-january-2026) · [NHIMA](https://www.nhima.co.zm/membership/registration-steps) · [ZRA](https://www.zra.org.zm)

This is an estimate, not tax advice.

## Built with

Plain HTML, CSS and JavaScript in one file. No framework and no build step.

## Files

| Path | What it is |
|---|---|
| `index.html` | The whole app |
| `favicon.svg` | Tab icon |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

## Run it locally

Open `index.html` in a browser.

## Publish with GitHub Pages

1. The repository is named `zambia-take-home-pay`.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, then click **Save**.
4. After a minute or two, the site is live at https://roykamwanza.github.io/zambia-take-home-pay/.

Every push to `main` updates the site.

## Updating the rates

All rates are at the top of the `<script>` in `index.html` (`BANDS`, `NAPSA_RATE`, `NAPSA_CEIL`, `NHIMA_RATE`). Change them there and update the "Rates and sources" section.

---

Built by [Roy Kamwanza](https://roykamwanza.github.io) · [LinkedIn](https://www.linkedin.com/in/roy-kamwanza-0550b5244/) · [GitHub](https://github.com/roykamwanza)
