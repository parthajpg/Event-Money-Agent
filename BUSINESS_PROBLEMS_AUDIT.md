# ⚠️ Event Money Agent — Business Problems Audit

> **Purpose:** Unfiltered identification of business-layer problems in the current project state.
> **Date:** September 2026
> **Auditor:** Principal Architect Review

---

## 🔴 PROBLEM 1 — Revenue Projections Are Built on Unvalidated Assumptions

### What the plan says
- 15 pitches/month → 3 closed SME deals → ₹15,000 commission
- 1 foreign hospitality group → ₹40,000 profit
- **Total: ₹55,000/month with >90% net margin**

### What is actually wrong
- **20% cold close rate** is used for a brand-new operator with zero track record, zero portfolio, and zero existing sponsor relationships. Industry reality for cold B2B outreach in India by a new solo operator is **3–5% in month 1**.
- The model never accounts for **deal cycle delays** — a sponsor who says yes on Day 1 may not transfer money until after the event, which could be 60 days away.
- **No revenue from month 1 or 2 is near-certain.** First revenue will realistically come at month 2–3 after trust is built.
- The ₹40,000 hospitality profit assumes a group booking exists. There is **no channel, no hotel partnership, no booking system, and no foreign delegate outreach mechanism** built anywhere in the project.

### Business risk
If close rate is 5% instead of 20%, monthly revenue drops from ₹55,000 to under ₹10,000 — below operational viability.

---

## 🔴 PROBLEM 2 — Revenue Stream B (Foreign Hospitality) Does Not Exist

### What the plan says
Foreign hospitality is projected to contribute **₹40,000/month** — nearly 73% of total profit margin.

### What is actually missing
- No hotel partnership or block booking agreement is in place.
- No foreign delegate discovery mechanism exists in any workflow.
- No outreach template for international conference organizers exists.
- No payment infrastructure for USD/EUR invoicing exists.
- The AI pipeline has zero nodes, zero prompts, and zero data fields related to foreign delegates.

### Business risk
This revenue stream is entirely fictional in the current state. The real monthly ceiling without it is approximately **₹15,000**, not ₹55,000. Every financial projection in the plan is overstated by 4x.

---

## 🔴 PROBLEM 3 — The AI Generates Fake Sponsor Contacts

### What is happening
The B2B Deal Hunter (Stage 3) generates company names, decision-maker names, phone numbers, and email addresses using only LLM inference. It has no web search tool, no directory access, and no live data source.

### Real consequence
- You will call phone numbers that do not exist or belong to the wrong person.
- You will email addresses that bounce.
- You will approach the wrong person at a company, get rejected, and burn that lead permanently.
- Your credibility with event organizers collapses if you claim you have verified sponsor leads that turn out to be fabricated.

### Business risk
Operating on hallucinated contact data is worse than having no data. It creates false confidence and wastes the most scarce resource — **your personal calling time**.

---

## 🔴 PROBLEM 4 — No Post-Approval Outreach Tool Exists

### What the plan promises
The system is described as an "autonomous deal-brokering engine."

### What actually happens after Human Approval
The Telegram bot sends a summary. You click Approve. The workflow ends. Nothing else happens.

- No WhatsApp message is drafted.
- No cold email is generated.
- No pitch script or call guide is produced.
- No follow-up schedule is set.

### Business risk
Every deal still requires **100% manual outreach effort** from you after the bot approves. The system is an information tool, not a brokering engine. The gap between "AI found an opportunity" and "money is in your account" is entirely manual and unstructured.

---

## 🔴 PROBLEM 5 — No CRM, No Memory, No Pipeline Visibility

### What is happening
When Stage 0 discovers events and passes them to Commander, each event runs as an isolated execution. There is no database, no Google Sheet, no Airtable — nothing that persists.

### Real consequence
- If a workflow run fails at any stage, the event is gone. You cannot retry it.
- You have no visibility into how many events you've contacted, what stage each deal is at, or which sponsors you've already pitched.
- You cannot identify if the same sponsor is being pitched across 3 different events simultaneously — which will get you blacklisted.
- You cannot track follow-up dates, responses, or closures.

### Business risk
Without a CRM, you are running a business blind. You will double-contact sponsors, lose promising leads, and have no data to improve your pitch or conversion rate over time.

---

## 🔴 PROBLEM 6 — The "Avoid the Big Brand Trap" Rule Is Not Enforced

### What the plan says
> "Never pitch mega-corporations. Target local champions where the founder can approve ₹15k–₹50k within 48 hours."

### What is actually happening
The B2B Deal Hunter (Stage 3) is given no constraint on company size. Depending on the event input, it will freely suggest Reliance, Swiggy, Byju's, or other large brands as target sponsors — companies with 6-month agency procurement cycles.

There is no filtering rule, no company size check, and no revenue-range validation in the prompt or in any code node.

### Business risk
If you spend your first week calling the marketing team at Swiggy or Byju's because the AI suggested it, you will get zero responses and waste your most critical early momentum window.

---

## 🔴 PROBLEM 7 — Organizer Bypass Risk Has No Technical Safeguard

### What the plan says
> "Never reveal the sponsor's contact until the organizer confirms the fee."

### What is actually happening
The system sends a Telegram card with full opportunity details — company names, industries, pitch angles — to you. There is nothing stopping you or anyone with access from sharing this with the organizer directly, which lets the organizer approach the sponsor without you, cutting out your commission.

More critically, the system has no concept of a **signed brokerage agreement** or even a WhatsApp confirmation workflow. Your commission claim is verbal and unenforceable.

### Business risk
You can lose your commission on every deal where you introduce the organizer to the sponsor before payment is secured. This is the highest-frequency failure mode in commission brokering.

---

## 🟡 PROBLEM 8 — No Repeatable Pitch Asset Exists

### What is missing
The plan recommends sending organizers "a clean 1-page PDF showing verified demographic fit." This PDF does not exist. There is no template, no generated document, no automated PDF creation in the pipeline.

Every pitch requires you to manually compile and write a proposal document from scratch after reading the AI report.

### Business risk
Without a professional pitch asset, your conversion rate with event organizers drops significantly. A text message saying "I have a sponsor for you" converts far worse than a structured one-page proposal with audience demographics, sponsor profile, and deal terms.

---

## 🟡 PROBLEM 9 — 6-Month Event Horizon Is Strategically Wrong for Month 1

### The logic problem
The urgency matrix correctly identifies 30–60 day events as highest priority. But the system is being built in September 2026. The pipeline of 30–60 day events for October–November 2026 is **already being worked by other agencies and student coordinators**. You are entering late.

### Business risk
Month 1 will mostly surface events in the 90–180 day range (January–March 2027). Those are good for pipeline building but produce zero revenue in month 1 or 2. The P&L model that assumes ₹55,000 in month 1 is not achievable under this timeline.

---

## 🟡 PROBLEM 10 — No Legal or Compliance Structure

### What is missing
- No business registration (GST, sole proprietorship, or LLP).
- No brokerage agreement template between you and event organizers.
- No service agreement between you and sponsors.
- No invoice template for 15–20% commission.

### Business risk
When you close your first ₹50,000 deal, the sponsor may refuse to pay "commission" to an unregistered individual. Without a signed agreement, you have no legal standing to collect. This is not a month-6 problem — it will hit you on your **first closed deal**.

---

## Summary Table

| # | Problem | Revenue Impact | Urgency |
|---|---|---|---|
| 1 | Projected close rate is 4x too optimistic | Direct — month 1 revenue near zero | 🔴 Critical |
| 2 | Foreign hospitality stream does not exist | ₹40,000/month missing from projections | 🔴 Critical |
| 3 | AI generates fake sponsor contacts | Every outreach call is a blind guess | 🔴 Critical |
| 4 | No post-approval outreach tool | 100% manual effort after AI approves | 🔴 Critical |
| 5 | No CRM or pipeline tracking | Deals lost, no iteration possible | 🔴 Critical |
| 6 | Big brand filter not enforced in AI | First week wasted on wrong targets | 🔴 Critical |
| 7 | No commission protection mechanism | First deal closed = commission lost | 🔴 Critical |
| 8 | No pitch asset (PDF/proposal) | Low organizer conversion rate | 🟡 High |
| 9 | 6-month horizon wrong for month 1 | Revenue delayed to month 3 minimum | 🟡 High |
| 10 | No legal/compliance structure | Cannot legally collect first commission | 🟡 High |

---

## Recommended Fix Priority (Ordered)

1. **Get a real contact data source** — Integrate Tavily search inside Stage 3 to find actual business websites, Google Maps listings, and LinkedIn profiles. No more hallucinated contacts.
2. **Build a Google Sheets CRM** — Log every discovered event and its pipeline status immediately after Stage 0 runs.
3. **Build a commission protection script** — A WhatsApp message template that establishes your broker role in writing before any introduction is made.
4. **Correct the P&L model** — Reforecast month 1 at 5% close rate, not 20%. Set month 3 as first revenue target.
5. **Create a one-page pitch PDF template** — Even a static Canva template that you fill manually is better than nothing.
6. **Add SME-size filter to Stage 3** — Explicitly exclude companies above 500 employees or above ₹100Cr revenue in the prompt.
7. **Treat Revenue Stream B as a separate project** — Remove it from current P&L entirely. Build it fresh with a hotel partnership first.


---
---

# 🛠️ Fixes — Detailed Action Plan for Every Business Problem

> Each fix has three parts: **What to do**, **How exactly**, and **Definition of done**.

---

## FIX 1 — Rebuild the P&L Model on Honest Numbers

### What to do
Replace the single-scenario 20% close rate P&L with a 3-scenario model built on real ramp timelines.

### How exactly

**Revised Monthly Targets**

| Month | Pitches Sent | Deals Closed | Close Rate | Revenue |
|---|---|---|---|---|
| Month 1 | 10 | 0 | 0% | Rs 0 |
| Month 2 | 15 | 1 | 7% | Rs 6,000 - Rs 10,000 |
| Month 3 | 20 | 2 | 10% | Rs 15,000 - Rs 25,000 |
| Month 4+ | 20 | 3-4 | 15-20% | Rs 30,000 - Rs 55,000 |

- Month 1 target is not revenue. It is 3 organizer conversations and 1 introduction made.
- Deal cycle rule: Revenue counts only when money reaches your bank account, not on verbal yes.
- Build 3 scenario tabs in Google Sheets: Conservative (5%), Base (10%), Optimistic (20%). Track actuals every Friday.

### Definition of done
A Google Sheet P&L exists with three scenario columns. Actuals updated weekly. No financial decision is made based on the optimistic scenario alone.

---

## FIX 2 — Remove Foreign Hospitality from Current P&L. Build It Separately.

### What to do
Strip Revenue Stream B from all current projections. Execute it as a 3-step separate phase.

### How exactly

**Step 1 — Get one hotel deal first (Week 1-2)**
- Call the Sales/Events Manager at 2 four-star hotels near conference venues in your city.
- Pitch: "I bring groups of 5-15 foreign delegates per booking. I need a negotiated group rate and 10-12% agent commission per room night in writing."
- A WhatsApp message confirming the rate is a valid starting agreement.

**Step 2 — Find one real international conference (Week 2-4)**
- Search ieee.org/conferences, springer.com/conferences, or "international conference [city] 2027".
- Contact the organizing committee and request to be listed as the official accommodation partner in delegate welcome emails.

**Step 3 — Add foreign delegate flag to Stage 0 (Week 3)**
- Add foreign_likelihood: High | Medium | Low to Stage 0 output based on whether the event is international/academic.
- Events flagged High go to a separate Google Sheet tab for manual hospitality follow-up.

### Definition of done
One hotel rate card confirmed in writing. One conference where you can contact delegates. Revenue Stream B removed from current P&L and moved to a separate Phase 2 tab.

---

## FIX 3 — Replace Hallucinated Contacts with Real Web-Sourced Data

### What to do
Add Tavily web search as a live tool inside Stage 3. Every company contact must come from a real URL before it is output.

### How exactly

In Stage 3 — attach a Tavily Tool node to the B2B Deal Hunter agent. The agent must run these searches before outputting any contact:

- "[company name] [city] owner founder director phone"
- "site:justdial.com [company name] [city]"
- "site:indiamart.com [company name] [city]"

Add these fields to every Stage 3 opportunity output:
- contact_source_url: actual URL where contact was found
- phone_verified: number from the source
- contact_confidence: HIGH | MEDIUM | LOW | UNVERIFIED

Rule: If contact_confidence is UNVERIFIED, the Telegram card must show a warning symbol. Never display it as confirmed.

### Definition of done
Every Stage 3 company has a contact_source_url. Zero contacts output without a search being run. Telegram card shows confidence level for every lead.

---

## FIX 4 — Build the Post-Approval Outreach Engine

### What to do
After Human Approval in Commander, add three output nodes that enable action within 30 minutes.

### How exactly

**Output A — Organizer WhatsApp Message (auto-generated):**
"Hi [Organizer Name], I am [Your Name], an event sponsorship consultant.
I have a [category] brand looking to sponsor events like [Event Name] in [City].
Before I connect both parties, I need written confirmation of our 15% facilitation fee (payable within 48 hours of sponsor funds received).
Reply Agreed to proceed."

**Output B — Sponsor Phone Call Script (auto-generated):**
Opening: "Hi, is this the [Role] at [Company]? I have a specific opportunity matching your target audience. 90 seconds?"
Pitch: "[Event Name] in [City] on [Date] — [X,XXX] attendees, primarily [demographic]. [Category] slot — you'd be the only [category] brand. Ticket: Rs [X]."
Close: "What number can I send the brief to on WhatsApp?"

**Output C — Google Sheets CRM row update:**
Status set to APPROVED - OUTREACH PENDING with today's date and follow-up date = today + 3 days.

### Definition of done
Clicking Approve delivers: organizer message copy-ready, sponsor call script, CRM row with follow-up date. First outreach possible within 30 minutes.

---

## FIX 5 — Build the Google Sheets CRM

### What to do
Create a Google Sheet pipeline tracker. Add a Sheets write node in Stage 0 after events are discovered — so every event is logged before Commander even runs.

### How exactly

**Sheet 1: Events (written automatically by Stage 0)**

Columns: event_id, event_name, city, event_date, urgency (HOT/PRIME/PIPELINE/LONG_HORIZON), sme_fit_score, source_url, organizer_phone (updated manually), status (NEW/CONTACTED/NEGOTIATING/CLOSED/DEAD), last_action (free text), follow_up_date (auto = today + 3 days), commission_estimate (from Stage 5), commission_received (filled manually on payment).

Where to add the write node in n8n: In Stage 0 — after Expand Qualified Events, before Format Event String. Every event logs to Sheets even if Commander fails downstream.

**Sheet 2: Sponsors Contacted** — Prevents double-pitching the same sponsor at multiple events.
Columns: company_name, event_id (linked to Sheet 1), pitch_date (auto), response (Interested/Rejected/No Response/Follow Up).

### Definition of done
Every Stage 0 run automatically creates Google Sheets rows. Pipeline visible in real time. No event silently lost.

---

## FIX 6 — Enforce the SME-Only Filter in Stage 3

### What to do
Add hard constraints to Stage 3 prompt AND a code-level blocklist to catch mega-brands even if the LLM ignores the prompt.

### How exactly

**Add to Stage 3 system prompt (before the JSON schema):**
MANDATORY TARGETING CONSTRAINTS:
- ONLY suggest companies with fewer than 500 employees.
- ONLY suggest companies with a physical local presence in the event city.
- ONLY suggest companies where ONE person can approve Rs 15,000-Rs 75,000 within 48 hours without committee approval.
- PREFERRED: Local IELTS/coaching centers, independent cafes, cloud kitchens, city-based PG chains, regional D2C brands, local gyms, city EdTech startups.
- NEVER suggest: Reliance, Jio, Swiggy, Zomato, Byju's, PhysicsWallah, Unacademy, HDFC, ICICI, Coca-Cola, PepsiCo, RedBull, Amazon, Flipkart, Ola, Uber, Paytm, Google, Microsoft, or any NSE/BSE top-100 company.

**Add a code blocklist node after Parse Output in Stage 3 to filter any that slip through.**

### Definition of done
Run Stage 3 on any event. Zero mega-brands in output. Every suggestion has a local decision-maker reachable by phone.

---

## FIX 7 — Build Commission Protection into the Workflow

### What to do
Generate a commission lock-in WhatsApp template as part of every Commander output — shown at the top of the approval card, before the sponsor list is revealed.

### How exactly

Add a Commission Lock Message node in Commander before Human Approval. Output:

"SEND THIS TO THE ORGANIZER FIRST — before revealing any sponsor name:

Hi [Organizer Name], I am [Your Name], an event sponsorship consultant. I have sourced a [category] brand interested in [Event Name] on [Date] in [City].

Before the introduction:
- Facilitation fee: 15% of the sponsorship value
- Payable: within 48 hours of sponsor fund receipt

Reply Agreed to proceed.

WARNING: Screenshot their reply. This is your only legal protection.
WARNING: Do NOT reveal the sponsor name until Agreed is received."

The Telegram approval card shows this at the top. The Approve button says: "Organizer confirmed. Show me the sponsor details."

### Definition of done
Every approval card shows the commission lock script as Step 1. You have a WhatsApp screenshot for every deal before any introduction is made.

---

## FIX 8 — Auto-Generate a One-Page Pitch Brief

### What to do
Add an LLM node after Commander's final report that outputs a WhatsApp-ready pitch brief — copy-paste ready, zero writing needed.

### How exactly

Add Generate Pitch Brief node after Assemble Final Report. The brief is sent to you via Telegram after approval — structured as:

Event name, city, date, attendance, demographic profile, sponsorship category available, format (stall/booth/sponsor), ticket size range, audience fit score, 3 bullet reasons why this sponsor category fits this event specifically, and a call-to-action line.

Format it for WhatsApp (no markdown, clean line breaks, emoji headers).

### Definition of done
Every approved opportunity produces a formatted brief in Telegram. You can send it to a sponsor in under 60 seconds without writing anything.

---

## FIX 9 — Month 1 Strategy: Manual Network First, AI Second

### What to do
Do not rely on Stage 0 for your first revenue. Use your personal network to find 3 confirmed events in week 1, then run the AI pipeline on those specific events.

### How exactly

**Week 1 — Manual sourcing (no AI required):**
1. Call 3 friends at local colleges: "Is your fest happening in the next 30 days? Who handles sponsorships?"
2. Check Instagram for posts from college cultural committees in your city. DM them directly.
3. Search unstop.com/events manually for your city filtered by next 30 days.
4. Target by Friday of week 1: 3 confirmed event names and 3 organizer phone numbers.

**Week 1-2 — AI-assisted (use Manual Trigger in Commander):**
Run your 3 manually found events through Commander using the Manual Trigger. AI generates sponsor pitch packs for real, verified events you already know exist.

Stage 0 role in month 1: Pipeline building only. Log all events to Google Sheets. Only pursue urgency HOT events (30 days or less). Everything else is month-2+ pipeline.

### Definition of done
End of week 1: 3 event names confirmed, 3 phone numbers in hand, 3 AI outputs ready. First sponsor calls happen in week 2.

---

## FIX 10 — Legal Structure: Minimum Viable in 7 Days

### What to do
Register as a sole proprietor and create 3 documents before your first outreach call.

### How exactly

**Day 1-2: Business Setup**
- Sole proprietorship under your name. Cost: Rs 0-Rs 500. No GST needed until Rs 10L annual revenue.
- Use your existing bank account + UPI ID for early deals.

**Day 2-3: Create 3 Documents**

Document 1 — Commission Confirmation Script (WhatsApp, from Fix 7): Screenshot every Agreed reply and store in Google Drive folder: Commission Agreements.

Document 2 — Invoice Template (Google Docs):
From: [Your Name] — Event Sponsorship Consultant
To: [Organizer/Sponsor Name]
Date, Invoice Number, Service description, Amount (15% of confirmed sponsorship), UPI and bank details.

Document 3 — One-Para Brokerage Agreement (send via WhatsApp):
"[Your Name] agrees to source and introduce sponsors to [Organizer] for [Event] on [Date]. [Organizer] agrees to pay a 15% facilitation fee on all sponsorship funds received through this introduction, payable within 48 hours. Both parties confirm by replying Agreed."
Screenshot of Agreed reply = valid informal agreement for deals under Rs 1 Lakh.

### Definition of done
Business name decided. UPI/bank ready for payment. Invoice template in Google Docs. WhatsApp agreement script ready. You can legally request and collect payment from deal 1.

---

## Implementation Timeline

WEEK 1 — Foundation (no code changes needed)
- Fix 9: Manually source 3 confirmed events via personal network
- Fix 10: Register business and create 3 legal documents
- Fix 1: Rebuild P&L in Google Sheets with 3 scenarios

WEEK 2 — Data and CRM (n8n workflow changes)
- Fix 5: Google Sheets CRM schema + write node added to Stage 0
- Fix 6: SME blocklist added to Stage 3 prompt and code node
- Fix 3: Tavily search tool added to Stage 3 B2B Deal Hunter

WEEK 3 — Outreach Engine (n8n workflow changes)
- Fix 7: Commission lock message added to Commander output
- Fix 4: Organizer message and sponsor call script added after Approval
- Fix 8: Pitch brief generator node added

WEEK 4 — Revenue Stream B (offline actions only)
- Fix 2: Contact 2 hotels for group rate agreement
- Fix 2: Identify 1 international conference to partner with

MONTH 2+ — Scale on a working, honest foundation
- Close first deal using the fixed pipeline
- Update P&L actuals every Friday
- Iterate on close rate using real data
- Activate Revenue Stream B only when hotel deal is signed
