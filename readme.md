# Private Expense Log

A lightweight, privacy-first personal expense tracker that runs 100% in your browser. Connect your Gmail in one click to automatically categorize online transactions, log cash spends manually, and monitor monthly category budgets—with zero backend servers or central databases.

**Live Demo:** [https://rithik9988.github.io/private-expense-log/](https://www.google.com/search?q=https://rithik9988.github.io/private-expense-log/)

---

## Features

- **1-Click Gmail Auto-Sync:** Uses Google Identity Services (OAuth 2.0) and the Gmail REST API (`gmail.readonly`) to scan the last 30 days of debit, UPI, and ride-receipt emails and deduplicate matching alerts.
- **Smart Auto-Categorization:** Automatically sorts transactions into **Commute** (Uber, Ola, Rapido, FlexiRide), **Quick Commerce** (Zepto, Blinkit, Instamart, Amazon Fresh), **Shopping** (Amazon, Flipkart, Myntra), **Food & Dining** (Zomato, Swiggy), **Bills & Utilities**, and **Other**.
- **Cash & Manual Logging:** Add cash or manual expenses alongside online transactions and track your Cash vs. Online split.
- **Category Dashboard & Month Filter:** Interactive Chart.js doughnut chart and category progress bars with a dynamic month-by-month filter.
- **Monthly Category Budgets:** Set custom ₹ limits per category with live **On track**, **Near limit (80%+)**, and **Over budget (100%+)** alerts.
- **CSV Export & Sample Data:** Export your current view to `.csv` anytime, or click **Try Sample Data** to preview the dashboard without signing in.

---

## Privacy & Security Architecture

- **Zero Backend / No Central Database:** Everything runs client-side in your browser. The site creator never sees, stores, or has access to your emails or expenses.
- **Ephemeral In-Memory Gmail Data:** OAuth access tokens and Gmail-synced transactions are kept strictly in RAM for your active session—never written to `localStorage` or cookies—so they disappear automatically when you refresh or close the tab.
- **Instant Sign Out & Token Revocation:** Clicking **Sign Out** immediately revokes your Google access token via `google.accounts.oauth2.revoke()`, clears all session data, and resets the dashboard.
- **Least Privilege & XSS Protection:** Requests read-only Gmail access (`gmail.readonly`) over HTTPS and sanitizes all rendered text with HTML escaping.

---

## Tech Stack

- **Frontend:** Single-file HTML5, [Tailwind CSS](https://tailwindcss.com/) (CDN), Vanilla JavaScript
- **Charts:** [Chart.js](https://www.chartjs.org/)
- **Auth & Email API:** [Google Identity Services](https://developers.google.com/identity/oauth2/web/guides/overview) & [Gmail REST API](https://developers.google.com/gmail/api)
- **Hosting:** [GitHub Pages](https://pages.github.com/)

---

## Run Locally or Self-Host

1. Clone or download `index.html` from this repository.
2. *(Optional)* To enable **Connect Gmail** on your own domain, create a Web Application **OAuth 2.0 Client ID** in [Google Cloud Console](https://console.cloud.google.com/) with the **Gmail API** enabled, add your domain under **Authorized JavaScript origins**, and paste your Client ID into `DEFAULT_GOOGLE_CLIENT_ID` in `index.html`.
3. Open `index.html` via a local web server or deploy it to GitHub Pages, Netlify, or Vercel.
