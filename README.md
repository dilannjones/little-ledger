# 🌷 Little Ledger

**A cozy, browser-based bill planner built around a digital cash-envelope system.**

[**Open Little Ledger**](https://dilannjones.github.io/little-ledger/)

Little Ledger helps organize recurring bills across multiple bank accounts and work out how much to transfer from each biweekly paycheck—without rewriting lists or doing the math by hand. Each bank account acts like a digital envelope for a particular group of bills or savings allocations.

> Personal project · Built for everyday budgeting · No bank connection or automatic payments

## ✨ What it does

### Overview
- See your paycheck, planned allocations, and remaining unallocated funds.
- Review account summaries and checklist progress.

### ☑️ Bills Checklist — review first
- Organize bills by the bank account that funds them.
- Edit a monthly bill estimate and automatically calculate half as its suggested per-paycheck allocation.
- Override the per-paycheck amount manually whenever needed.
- Mark individual bills **Reviewed**, or use **Check All / Uncheck All**.
- Keep review checkmarks separate for each biweekly payday.
- Checking a bill **does not** mark it paid, transfer money, or change an account balance.

### 💸 Payday Plan — transfer second
- See one combined planned transfer amount for each bank account.
- Compare **Planned** totals from the bill allocations against **Actual** transfers you've recorded.
- Track transferred-so-far and remaining-to-transfer amounts.
- Record a transfer after completing it in your banking app; the app remembers the chosen source account.
- Display **✓ Transferred** for recorded accounts and help avoid duplicate payday entries.
- Show actual recorded transfer amounts even when they differ from the plan.
- Keep allocations independent of existing account balances, preserving any extra cushion in each envelope.

### 🏦 Bank Accounts and Activity
- Manage account nicknames, bank labels, types, icons, notes, and optional tracked balances.
- View and undo recorded transfers or other transactions.
- Preserve linked bills when renaming an account.
- Use nicknames rather than storing banking credentials or account numbers.

### ☁️ Access across devices
- Hosted on **GitHub Pages** as a responsive browser app.
- Uses **Supabase Authentication** for email/password sign-in.
- Stores each signed-in user's ledger in **Supabase Postgres**, protected with row-level security policies.
- Loads cloud data on sign-in and saves edits to the cloud.
- Offers JSON backup and restore, including an explicit first-time import from existing browser data.
- Remembers the selected navigation tab and paycheck locally in the browser.

## 💗 The intended payday routine

1. Open **Bills Checklist** for the paycheck you're working on.
2. Update variable amounts; mark each allocation as **Reviewed**.
3. Go to **Payday Plan** to see how much to transfer into each account.
4. Make those transfers in your actual banking apps.
5. Click **Record** for each bank account to track the completed transfer.
6. Compare planned and actual totals, and revisit **Activity** if a transfer needs correcting.

The selected pay period uses a biweekly schedule. Fixed per-paycheck allocations still apply even when a monthly bill isn't due during that two-week window.

## 🛠️ Tech stack

| Layer | Technology |
| --- | --- |
| Frontend | HTML, CSS, and vanilla JavaScript |
| Hosting & deployment | GitHub Pages |
| Authentication | Supabase Auth |
| Database | Supabase Postgres with row-level security (RLS) |
| Client-side cloud API | Supabase JavaScript SDK |
| Local convenience & backup | Browser storage and downloadable JSON files |

The application is intentionally lightweight: no paid budgeting service, native app installation, or banking integration is needed.

## 🔒 Privacy and security

- Financial ledger records are intended to be accessible only to their authenticated owner through Supabase RLS policies.
- The website's **source code is public** because it is hosted through a public GitHub repository. **Never commit personal ledger exports, bank details, passwords, or secret/service-role API keys.**
- Browser-facing Supabase publishable keys are designed to be public; **secret and service-role keys must never appear in the client code**.
- The app does not connect to banks, initiate real money transfers, or automatically pay bills.
- Data also has a local browser copy. Use a trusted device and avoid entering account numbers or credentials.
- Sync occurs when saving/loading; already-open browser tabs on separate devices do **not** live-update in real time. Refresh to load the latest saved data, and avoid simultaneous edits on multiple devices.
- Download occasional JSON backups, especially before major changes. Test your own RLS configuration and keep your Supabase project credentials secure.

## 🚀 Deployment notes

The site is served from the repository's `main` branch using GitHub Pages. Updates to the frontend can be committed to GitHub and will appear after Pages deploys successfully.

The Supabase project needs:

- Email authentication configured with the GitHub Pages site URL and redirect URL.
- A `public.user_ledgers` table containing a user ID and ledger JSON.
- RLS enabled, with policies ensuring authenticated users can only read and modify their own row.
- The **project URL and publishable key** configured in the client application, never a privileged API key.

**Important:** Do not replace an existing cloud ledger with demo/sample data. Back up browser data before initial migration or restore.

## ✅ Project milestones

- Replaced a handwritten, biweekly payday worksheet with a browser-based cash-envelope planner.
- Added grouped bills and adjustable per-paycheck allocation calculations.
- Introduced paycheck-specific review checklists and bulk review controls.
- Built account-by-account transfer recording, completion indicators, and running totals.
- Added a clean planned-versus-actual comparison.
- Added account management, transaction history, and JSON backup/restore.
- Deployed the app with GitHub Pages.
- Added Supabase sign-in, private ledger storage, and cross-device syncing.
- Verified that ledger data could be accessed on a second device after first-time import.

## 🌱 Possible future improvements

- Save a historical **snapshot of each payday's planned bill amounts** so later edits don't change old plans.
- Provide clearer cloud sync conflict handling for simultaneous editing.
- Add optional reminders and exportable payday summaries.

---

Made with care to make payday a little less stressful. 🌷
