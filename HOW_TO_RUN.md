# 🚀 How to Run Event Money Agent Locally

---

## ⚡ FAST TRACK: Run Event Money Agent 2.1 (Zero-Credential Native Memory)

Import the unified **Agent 2.1** with automatic anti-duplicate memory & verified brand resolution:
1. Open **http://localhost:5678** in your browser.
2. In n8n, click the **`...` (3-dot menu)** in the top right → **`Import from File`**.
3. Select:
   ```
   c:\Users\ParthasarathyE\Downloads\JavaPrograms\Event-Money-Agent\Event Money Agent 2.1.json
   ```
4. Verify the credentials:
   - **Groq Model nodes**: linked to your saved Groq account (`wnyadzTYaSb9M0x1`).
   - **Send Telegram Briefing node**: linked to your Telegram bot.
5. In **`Agent Master Config`**, verify your `telegram_chat_ids` (supports comma-separated IDs).
6. Click **`Execute Workflow`**.
7. **Zero Setup & Zero Duplicates**: Automatically logs seen events in persistent memory so previously seen events are never repeated!

---

## ⚡ Agent 2.0 (Single Workflow Baseline)

Located at `Event Money Agent 2.0.json`.

## 🏛️ LEGACY SETUP — Stages 0 to 7 (Multi-Agent System)

### How to import in n8n:
1. Open **http://localhost:5678** in your browser.
2. In the workflows list or on an empty canvas, click the **`...` (3-dot menu)** in the top right.
3. Click **`Import from File`**.
4. Navigate to:
   ```
   c:\Users\ParthasarathyE\Downloads\JavaPrograms\Event-Money-Agent\backup\
   ```
5. Import all 7 workflow files one by one:
   - `Event Money Agent - Event Scout (Stage 1).json`
   - `Event Money Agent - Demand Analyst (Stage 2).json`
   - `Event Money Agent - B2B Deal Hunter (Stage 3).json`
   - `Event Money Agent - Verifier (Stage 4).json`
   - `Event Money Agent - Money Analyst (Stage 5).json`
   - `Event Money Agent - Partner Finder (Stage 6).json`
   - `Event Money Agent - Commander (Stage 7).json`
6. Press **`Ctrl + S`** to save each workflow after importing.

---

## ✅ STEP 2 — Set Up Credentials

Only two credentials are required:

### 1. Google Gemini API Key
1. Go to **https://aistudio.google.com** → Get API Key.
2. In n8n: **Credentials** (left sidebar) → **Add Credential**.
3. Search for **"Google Gemini (PaLM) API"** → Enter your API key → Click **Save**.
4. Open each sub-workflow (Stages 1–6) → click the **Gemini Flash Lite** node → select your saved Gemini credential.

### 2. Telegram Bot Token
1. Open Telegram → message **@BotFather** → send `/newbot` → follow prompts to get your token.
2. In n8n: **Credentials** → **Add Credential** → search **"Telegram API"** → paste token → Click **Save**.
3. Open **Commander (Stage 7)** → click the **"Human Approval"** node → select your Telegram credential.

---

## ✅ STEP 3 — Link Sub-Workflows in Commander

Open **"Event Money Agent - Commander (Stage 7)"**. For each of the 6 orange **Execute Workflow** nodes, ensure the matching workflow is selected in the **Workflow** dropdown:

| Node Name | Workflow Dropdown Selection |
|---|---|
| **`Execute Event Scout`** | `Event Money Agent - Event Scout (Stage 1)` |
| **`Execute Demand Analyst`** | `Event Money Agent - Demand Analyst (Stage 2)` |
| **`Execute Deal Hunter`** | `Event Money Agent - B2B Deal Hunter (Stage 3)` |
| **`Execute Verifier`** | `Event Money Agent - Verifier (Stage 4)` |
| **`Execute Money Analyst`** | `Event Money Agent - Money Analyst (Stage 5)` |
| **`Execute Partner Finder`** | `Event Money Agent - Partner Finder (Stage 6)` |

Press **`Ctrl + S`** to save Commander.

---

## ✅ STEP 4 — Run the Commander Agent

1. Open **"Event Money Agent - Commander (Stage 7)"** in n8n.
2. Check the **"Event Input"** node (second node) — edit the event description if desired:
   ```
   College cultural festival in Chennai, 5,000 expected attendees, audience primarily students aged 18-24.
   ```
3. Click **`Execute Workflow`** (orange button at the bottom).
4. Watch the pipeline run through all stages.
5. When complete, check your Telegram for the full report and approval action!

---

## 📋 Checklist

- [ ] Stages 1 to 6 imported and saved
- [ ] Commander (Stage 7) imported and saved
- [ ] Google Gemini credential added and linked in Stages 1–6
- [ ] Telegram credential added and linked in Commander
- [ ] All 6 Execute Workflow nodes linked to their respective workflows in Commander
- [ ] Commander executed successfully
- [ ] Telegram approval message received
