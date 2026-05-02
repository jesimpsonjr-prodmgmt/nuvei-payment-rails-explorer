# Nuvei US Payment Rails Explorer

An interactive product demo exploring US bank-based payment rails (ACH, RTP, FedNow) across Nuvei's core verticals: Gaming, Prediction Markets, and Crypto.

[Live Demo](https://jesimpsonjr-prodmgmt.github.io/nuvei-payment-rails-explorer/) | [Portfolio](https://johnsimpson.io)

---

## Problem Statement

Nuvei's US bank transfer business spans three payment rails (ACH, RTP, FedNow) and serves high-velocity verticals where settlement speed, reversibility, and transaction limits directly impact product experience and risk exposure. A Product Manager owning these rails needs to understand the trade-offs between them, not just technically, but in the context of specific vertical requirements.

A gaming operator needs instant deposits to keep players engaged. A prediction market platform needs irrevocable settlement before event outcomes are finalized. A crypto exchange needs real-time fund availability to match volatile asset prices. Each vertical imposes different constraints on which rail to recommend, when, and why.

This demo simulates the product thinking behind those decisions.

## Target User

- Hiring managers evaluating PM candidates for digital payments roles
- Payment operations teams comparing rail capabilities for merchant onboarding
- Product managers new to US bank-based payment rails who need a visual reference

## What This Demo Includes

### 1. Payment Rail Selector & Comparison Engine
Select a vertical (Gaming/iGaming, Prediction Markets, Crypto/Digital Assets) and transaction type (deposit, withdrawal, recurring). The tool recommends the optimal payment rail and provides a side-by-side comparison of settlement speed, cost structure, transaction limits, availability, reversibility, and risk profile. PM annotations explain *why* each recommendation fits the vertical context.

### 2. Transaction Lifecycle Simulator
A visual, animated flow showing what happens when a payment moves through each rail — from initiation through clearing to settlement. Includes realistic timing (ACH: 1-3 business days batch, RTP: seconds, FedNow: seconds) and failure/return scenarios (NSF, unauthorized, timeout) that illustrate how product teams must handle edge cases differently per rail.

### 3. Merchant KPI Dashboard
A simulated analytics view showing the metrics a PM in this role would monitor: approval rates by rail, settlement time distribution, transaction volume by vertical, and return/failure rates. Uses realistic data distributions modeled on publicly available industry benchmarks.

## Product Decisions

### What was built and why
- **Vertical-specific rail recommendations** — The job requires understanding Gaming, Prediction Market, and Crypto use cases. The selector demonstrates that rail choice is a product decision, not just a technical one.
- **Transaction lifecycle visualization** — PMs own the end-to-end delivery of payment features. Understanding what happens between "user clicks pay" and "funds settle" is table stakes.
- **KPI dashboard** — The role explicitly requires monitoring product KPIs and creating dashboards. This shows the PM mindset of measuring what matters.

### What was excluded and why
- **Card payments** — The role is specifically about US bank-based rails. Including cards would dilute the demo's focus and signal a lack of prioritization discipline.
- **Global payment methods (SEPA, Faster Payments, Interac)** — The role is US-focused. Scope creep into global rails would demonstrate the opposite of good PM judgment.
- **Live API integration** — Nuvei's API requires merchant credentials and commercial onboarding. Simulated data with industry-accurate values tells a better story than generic sandbox test transactions. A production implementation would integrate with Nuvei's REST 2.0 API.
- **Fraud/risk management module** — While Nuvei offers Assured Funds and fraud tools, adding this would expand scope beyond the core payment rails focus of the role.

## Architecture Decisions

- **Client-side only (single HTML file)** — No backend, no build tools. Runs on GitHub Pages. This is a product thinking demo, not a systems architecture showcase.
- **Simulated data with realistic values** — Transaction limits, settlement times, and cost structures are sourced from current Nacha, TCH, and Federal Reserve published specifications. KPI distributions are modeled on industry benchmarks for gaming and fintech verticals.
- **No external dependencies beyond CDN libraries** — Chart.js for the KPI dashboard. Everything else is vanilla HTML/CSS/JS. Minimal dependency footprint is a deliberate choice.

## Domain Context

### The Three US Bank-Based Payment Rails

| Attribute | ACH | RTP | FedNow |
|---|---|---|---|
| Operator | Nacha (via FedACH + EPN) | The Clearing House | Federal Reserve |
| Launched | 1970s (Same-Day: 2016) | 2017 | July 2023 |
| Settlement | Batch (1-3 days), Same-Day available | Real-time (seconds) | Real-time (seconds) |
| Availability | Business days (Same-Day windows) | 24/7/365 | 24/7/365 |
| Transaction Limit | $1M (Same-Day), $10M effective Sept 2027 | $10M (network max) | $10M (as of Sept 2025) |
| Reversibility | Reversible (returns up to 60 days) | Irrevocable | Irrevocable |
| Direction | Credit and Debit | Credit only | Credit only |
| FI Participation | ~10,000+ | 675+ | 1,200+ |
| Cost per txn | $0.20-0.50 | $0.50-1.00 | $0.01-0.045 |

### Why This Matters for Nuvei's Verticals
- **Gaming/iGaming**: Players expect instant deposits. RTP/FedNow enable real-time fund availability, reducing drop-off at the deposit screen. ACH works for withdrawals where players are less sensitive to timing.
- **Prediction Markets**: Event outcomes can be determined in seconds. Irrevocable settlement (RTP/FedNow) prevents disputes after market resolution. ACH's reversibility creates risk exposure for the platform.
- **Crypto/Digital Assets**: Volatile asset prices mean deposit speed directly impacts the price a user gets. Real-time rails match the speed expectation of crypto-native users. ACH creates arbitrage risk during the settlement window.

## Tech Stack

- HTML5, CSS3, vanilla JavaScript
- Chart.js (CDN) for KPI dashboard charts
- No build tools, no framework, no backend
- Hosted on GitHub Pages

---

Built by John Simpson — Senior Product Manager — 20 years in enterprise fintech & payments

Code is AI-assisted. Product thinking, domain expertise, and strategic commentary are mine.
