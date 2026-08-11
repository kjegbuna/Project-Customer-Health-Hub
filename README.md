# Customer Health Hub

An internal web app that gives a SaaS team an at-a-glance **health score (0–10)** for every customer — unifying finance, support, product-usage, and relationship signals into a single screen so the team can spot at-risk accounts before renewals.

> Built during my summer 2026 internship at **Chezie**. This public repo is a **scrubbed demo** running on sample data — no real customer information, credentials, or company data.

🔗 **Live demo:** https://kjegbuna.github.io/Project-Customer-Health-Hub/

---

## What it is
A single-page web app with two views:
- **Portfolio** — every active customer in one table with a color-coded health score, filters (At risk / Watch / Healthy / Inactive), search, sortable columns, and summary KPI tiles.
- **Customer detail** — a per-customer page with four panels (Product Usage, Finance & Renewals, Support & Stability, Stakeholders & Interactions), a plain-English "why" behind the score, and drill-downs into the underlying tickets, invoices, contacts, and activity.

## Why it was needed (the problem)
Signals about customer health lived in separate tools — billing, support, and product analytics — so no one had a single view of which accounts were healthy versus at risk heading into renewals. Risk was only noticed after something went wrong. The hub consolidates those signals into one score and one screen, so the team can act early and walk into renewal (and due-diligence) conversations informed.

## What I built / how it works
- A **weighted scoring model** that combines four areas — relationships (highest weight), product usage, support, then finance — into a 0–10 score, and maps it to an At risk / Watch / Healthy status with a one-line explanation.
- A **backend on Supabase (Postgres)** that aggregates raw records (invoices, support tickets, interactions, usage events, stakeholders) into summary views the app reads live.
- **Secure, team-only access**: authentication via Supabase Auth with **row-level security** so only accounts on the company's email domain can read any data — enforced at the database, not just the UI.
- A **self-contained front end** (one HTML file, no framework) that renders the portfolio, detail pages, and drill-downs, with source links back to support tools.

## Tools & tech
`HTML / CSS / JavaScript (no framework)` · `Supabase (Postgres, Auth, Row-Level Security)` · `Netlify (hosting + continuous deploy from GitHub)` · `Git / GitHub` · built with `Claude / Claude Code`

## Results / impact
- Unified **five separate data domains** into one health view.
- Automated a **0–10 health score** for 29 customers with an explainable reason, replacing gut-feel assessments.
- Locked all data to **company-domain accounts only** via database-level security.
- Removed the hand-maintained health tracker entirely by reading live data across 13 tables and 100,000+ records, keeping the view current with zero manual updates replaced a weekly spreadsheet refresh.
- Put every signal an owner needs (contract, 62 invoices, 325 support tickets, product usage, 211 contacts) on a single page, cutting renewal prep from ~10 minutes across tools to one click.
