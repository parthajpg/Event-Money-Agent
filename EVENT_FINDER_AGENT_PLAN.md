# 🛰️ Stage 0: Autonomous Event Finder Agent — Architecture & Implementation Plan

## 📌 Executive Summary
The **Event Finder Agent (Stage 0)** is an autonomous discovery engine that proactively searches the web, social media, and event aggregators for upcoming high-potential events. It extracts structured event metadata, filters out low-potential leads, and pipes qualified opportunities directly into the **Event Money Agent** pipeline (Stages 1 to 7) for automated sponsorship and financial analysis.

---

## 🏗️ End-to-End System Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│              STAGE 0: AUTONOMOUS EVENT FINDER AGENT                     │
│                                                                         │
│  [ Schedule Trigger (Daily) / On-Demand Webhook / Telegram / Form ]     │
│                                  │                                      │
│                                  ▼                                      │
│                  [ Dynamic Search Query Generator ]                     │
│                                  │                                      │
│         ┌────────────────────────┴────────────────────────┐             │
│         ▼                                                 ▼             │
│   [ AI Web Search ]                             [ Platform Aggregators] │
│   (Tavily / SerpAPI / Google)                   (Luma, Unstop, Meetup)  │
│         └────────────────────────┬────────────────────────┘             │
│                                  ▼                                      │
│                   [ Event Extractor & Normalizer ]                      │
│                  (Gemini Flash — Structured Output)                     │
│                                  │                                      │
│                                  ▼                                      │
│                  [ Deduplicator & Potential Filter ]                    │
│                     (Score: Attendance, Type, ROI)                      │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │
                                   ▼ Emits single / batch of events
┌─────────────────────────────────────────────────────────────────────────┐
│                 EVENT MONEY PIPELINE (STAGES 1 – 6)                     │
│                                                                         │
│  1. Event Scout        ──► 2. Demand Analyst ──► 3. B2B Deal Hunter     │
│  4. Claim Verifier     ──► 5. Money Analyst  ──► 6. Partner Finder      │
└──────────────────────────────────┬──────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│               STAGE 7: COMMANDER & HUMAN APPROVAL                       │
│                                                                         │
│   - Consolidates Executive Report & Portfolio Calculations             │
│   - Sends Actionable Telegram Card with Approve / Reject Options        │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🌐 Data Sources & Discovery Strategies

### 1. AI-Powered Live Web Search (Primary)
- **Engines**: Tavily Search API, SerpAPI, or Google Custom Search API.
- **Search Query Patterns**:
  - `upcoming college cultural fests in [City/State] 2025 OR 2026`
  - `upcoming developer hackathons and tech summits in [Country]`
  - `business expo convention center [City] schedule`
  - `site:unstop.com/events [City] cultural fest`
  - `site:lu.ma/discover [City] tech`

### 2. Direct Event Directory Feeds (Secondary)
- **Unstop & Devfolio**: Ideal for college tech/cultural fests and hackathons.
- **Lu.ma (Luma) & Meetup.com**: Ideal for startup, AI, and developer conferences.
- **10times & TradeIndia**: Ideal for trade expos, B2B exhibitions, and industrial summits.
- **Eventbrite Public Search RSS / API**: General public events and conventions.

---

## 📋 Stage 0: Detailed Workflow Specification (n8n)

### Node 1: Trigger
- **Schedule Trigger**: Runs automatically every morning (e.g., 08:00 AM).
- **Manual / Webhook Trigger**: For on-demand event hunting by region/niche.

### Node 2: Parameter Setup (Search Criteria)
Sets target parameters:
```json
{
  "target_regions": ["Chennai", "Bengaluru", "Hyderabad", "Mumbai"],
  "event_categories": ["College Cultural Fest", "Tech Conference", "Hackathon", "B2B Expo"],
  "timeframe_days": 60,
  "min_expected_attendance": 1000
}
```

### Node 3: Multi-Query Search Execution
Executes targeted web search queries across specified categories and locations using the Search Tool node.

### Node 4: LLM Event Extractor & Normalizer (Gemini Flash)
Parses raw web snippets, HTML, or markdown into structured event objects conforming to the schema below.

### Node 5: Deduplication & Scoring Filter (Code Node)
- Filters out past events or duplicate entries.
- Calculates an **Opportunity Score** ($0 - 100$) based on:
  - Expected attendance (higher = better).
  - Target demographic monetization potential (students/developers/executives).
  - Completeness of contact/venue details.

### Node 6: Loop Over Qualified Events
Iterates through discovered events and triggers **Commander (Stage 7)** or **Stage 1 (Event Scout)** for each qualified lead.

---

## 📦 Data Contract / Output Schema

Each discovered event output by Stage 0 conforms to this JSON structure:

```json
{
  "event_id": "evt_chennai_fest_2026_01",
  "name": "Saarang Cultural Festival 2026",
  "type": "College Cultural Festival",
  "organizer": "IIT Madras Student Body",
  "location": {
    "venue": "IIT Madras Campus",
    "city": "Chennai",
    "state": "Tamil Nadu",
    "country": "India"
  },
  "dates": {
    "start_date": "2026-01-10",
    "end_date": "2026-01-14",
    "status": "confirmed"
  },
  "audience": {
    "expected_attendance": 15000,
    "demographics": "College students aged 18-25, young professionals",
    "key_interests": ["Music", "Dance", "Gaming", "Fashion", "Tech"]
  },
  "raw_event_summary": "Annual 5-day cultural fest at IIT Madras with 15k+ footfall, concerts, competitions, looking for youth & FMCG brand partners.",
  "source_urls": [
    "https://example.com/saarang-2026"
  ],
  "opportunity_score": 92
}
```

---

## 🛠️ Implementation Roadmap

### Phase 1: Search Integration & Prototype
- [ ] Choose search provider (Tavily free tier / SerpAPI / Google Custom Search).
- [ ] Create `Event Money Agent - Event Hunter (Stage 0).json` in n8n.
- [ ] Test extraction accuracy on 5 real event search queries.

### Phase 2: Pipeline Chaining
- [ ] Connect Stage 0 output into Stage 1 (Event Scout) or Commander (Stage 7).
- [ ] Add batch throttling to avoid LLM rate limits (1 event every 5 seconds).

### Phase 3: Autonomous Telegram Digest
- [ ] Configure morning cron schedule.
- [ ] Aggregate all daily discovered events into a single high-level Telegram digest with quick-action approval buttons.
