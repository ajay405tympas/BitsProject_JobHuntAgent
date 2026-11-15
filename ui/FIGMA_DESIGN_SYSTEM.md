# Figma Design System & Mobile UI Specification

- **Project**: Autonomous Job-Matching Agent & Application Proxy
- **Layer**: Layer 1 — Candidate Access Layer (`ui/`)
- **Document**: UI Component Library, Figma Token Architecture & Wireframe Specifications
- **Version**: 1.0.0
- **Companion Prototype**: [`figma_screens_visual.html`](file:///c:/ajay/GoLang/GoogleAgents/job-hunt-naukri/ui/figma_screens_visual.html)

---

## 1. Design Principles

1. **Glanceable Status**: Candidate can determine run state, applications submitted, and pending questions within **3 seconds** of opening the app.
2. **Thumb-Zone Optimized**: All primary decision triggers (`Approve & Apply`, `Run Now`, `Save`) reside in the natural thumb zone (bottom 40% of the screen).
3. **Zero-Ambiguity Confidence**: Every automated action clearly presents *why* it was decided (match %, recency weighting, citation source).
4. **Resilient Feedback**: Immediate visual acknowledgment on user actions with optimistic UI updates.

---

## 2. Figma Design Tokens & Variables

### 2.1 Color Palette

| Token Name | Hex Code | Tailwind Class | Semantic Usage |
| :--- | :--- | :--- | :--- |
| `color-bg-base` | `#090d16` | `bg-slate-950` | Primary app canvas background (Dark Mode) |
| `color-surface-card` | `#111827` | `bg-slate-900` | Card containers, modals, bottom sheets |
| `color-surface-elevated` | `#1e293b` | `bg-slate-800` | Input fields, chip tags, nested cards |
| `color-border-subtle` | `#1e293b` | `border-slate-800` | Section dividers, card outlines |
| `color-border-focus` | `#3b82f6` | `border-blue-500` | Active inputs, selected states |
| `color-text-primary` | `#f8fafc` | `text-slate-50` | Main headings, question titles |
| `color-text-secondary` | `#94a3b8` | `text-slate-400` | Descriptions, metadata, secondary labels |
| `color-accent-blue` | `#2563eb` | `bg-blue-600` | Primary action buttons, active navigation |
| `color-success-emerald`| `#10b981` | `text-emerald-500` | $\ge 70\%$ match score, active recency, auto-applied |
| `color-warning-amber` | `#f59e0b` | `text-amber-500` | Tier 3 question review, recent recency decay, pacing wait |
| `color-danger-rose` | `#ef4444` | `text-rose-500` | Circuit breaker trip, legacy decay ($0.5\times$), rejected |

### 2.2 Typography Scale (Inter / SF Pro Display)

| Style | Size / Line Height | Weight | Usage |
| :--- | :--- | :--- | :--- |
| **Display 1** | 28px / 34px | Bold (700) | Metric counters, match score hero |
| **Heading 1** | 20px / 26px | SemiBold (600) | Screen titles, modal headers |
| **Heading 2** | 16px / 22px | SemiBold (600) | Card titles, section headers |
| **Body Regular** | 14px / 20px | Regular (400) | General descriptions, form inputs |
| **Body Medium** | 14px / 20px | Medium (500) | Question prompt text, button labels |
| **Caption Mono** | 12px / 16px | Medium (500) | Code tags, timestamps, API status |
| **Micro Badge** | 10px / 14px | Bold (700) | Tier indicator pills (`T1`, `T2`, `T3`) |

### 2.3 Grid, Spacing & Elevation
* **Base Unit**: 4pt / 8pt grid (`4px`, `8px`, `12px`, `16px`, `24px`, `32px`).
* **Screen Padding**: `16px` horizontal gutter for smartphones ($< 480\text{px}$).
* **Corner Radius**:
  * Chips & Pills: `9999px` (`rounded-full`)
  * Buttons & Inputs: `12px` (`rounded-xl`)
  * Cards & Bottom Sheets: `20px` (`rounded-2xl`)
  * Modal Frames: `28px` (`rounded-3xl`)
* **Elevation / Shadows**:
  * Level 1 (Cards): `0 4px 6px -1px rgba(0, 0, 0, 0.3)`
  * Level 2 (Floating Action / Sticky Bottom Bar): `0 10px 25px -5px rgba(0, 0, 0, 0.5)`

---

## 3. Figma Screen Wireframes & Component Layouts

### Screen 1: App Unlock, Customer Auth & Sign Up

#### 1A. Sign In State
```
+------------------------------------------+
|  [09:00]                            🔋 98%|
|                                          |
|                ⚡ WELCOME                |
|        Personal Career Automation Agent  |
|                                          |
|   +------------------------------------+ |
|   | Username or Email                  | |
|   | candidate@domain.com               | |
|   +------------------------------------+ |
|   +------------------------------------+ |
|   | Password                           | |
|   | ****************               👁️ | |
|   +------------------------------------+ |
|                                          |
|   +------------------------------------+ |
|   |          [  SIGN IN  ]             | |
|   +------------------------------------+ |
|                                          |
|      New to Job Agent? [ Sign Up Now ]   |
|                                          |
|               -- OR --                   |
|                                          |
|        [ 👤 Quick Face ID Unlock ]       |
|                                          |
+------------------------------------------+
```

#### 1B. Sign Up / Registration State
```
+------------------------------------------+
|  [09:00]                            🔋 98%|
|                                          |
|                ✨ CREATE ACCOUNT         |
|         5-Minute Autonomous Onboarding   |
|                                          |
|   +------------------------------------+ |
|   | Candidate Full Name                | |
|   | Jane Doe                           | |
|   +------------------------------------+ |
|   +------------------------------------+ |
|   | Email Address                      | |
|   | jane@domain.com                    | |
|   +------------------------------------+ |
|   +------------------------------------+ |
|   | Master Password                    | |
|   | ••••••••••••••••               👁️ | |
|   +------------------------------------+ |
|   +------------------------------------+ |
|   | Confirm Password                   | |
|   | ••••••••••••••••               👁️ | |
|   +------------------------------------+ |
|                                          |
|   +------------------------------------+ |
|   | [ CREATE ACCOUNT & START SETUP -> ]| |
|   +------------------------------------+ |
|                                          |
|      Already registered? [ Sign In ]     |
|                                          |
+------------------------------------------+
```

### Screen 2: Portal Provisioning & Encrypted Vault
```
+------------------------------------------+
|  < Back        PORTAL VAULT        [Help] |
|------------------------------------------|
|  Select Target Portal:                   |
|  [ Naukri 🟢 ]     [ Portal 2 ⚪ ]  [ + ] |
|                                          |
|  🔒 AES-256-GCM Hardware Encrypted Vault |
|  "Decrypted only in memory during scan"  |
|                                          |
|  Portal Username / Email:                |
|  +------------------------------------+  |
|  | user@naukri.com                    |  |
|  +------------------------------------+  |
|                                          |
|  Portal Password:                        |
|  +------------------------------------+  |
|  | ••••••••••••••••                👁️ |  |
|  +------------------------------------+  |
|                                          |
|  Session Health:                         |
|  • Status: Active Cookie Session 🟢      |
|  • Last Verified: Today at 09:02 AM      |
|                                          |
|  [ Verify Login Now ]   [ Save to Vault ]|
+------------------------------------------+
```

### Screen 3: Resume Studio & Skill Extractor
```
+------------------------------------------+
|  < Back        RESUME STUDIO             |
|------------------------------------------|
|  Active Master Resume:                   |
|  +------------------------------------+  |
|  | 📄 resume_v4_lead_arch.pdf         |  |
|  | Uploaded 2 days ago • 142 KB       |  |
|  | [ Replace Resume ]                 |  |
|  +------------------------------------+  |
|                                          |
|  Extraction Baseline:                    |
|  • Total Calculated Exp: 11.2 Years      |
|  • Skills Discovered: 24 Technologies    |
|                                          |
|  Recent Ingestion Logs:                  |
|  ✓ PDF Sections Parsed (Work, Edu, Skills|
|  ✓ Dynamic Timeline Model Built          |
|  ✓ Ready for Recency Verification        |
|                                          |
|     [  Go to Skill Recency Matrix -> ]   |
+------------------------------------------+
```

### Screen 4: Dynamic Skill Recency Matrix
```
+------------------------------------------+
|  < Back        SKILL RECENCY MATRIX      |
|------------------------------------------|
|  Review & verify recency for each skill: |
|                                          |
|  +------------------------------------+  |
|  | ⭐ Go (Golang)      [1.0x Active 🟢] |  |
|  | Exp: [ - ]  6.0 yrs  [ + ]          |  |
|  | Last Used: [ 2026 (Active)     v ]  |  |
|  | Level: ( ) Beg   ( ) Int   (•) Exp  |  |
|  +------------------------------------+  |
|                                          |
|  +------------------------------------+  |
|  | ⭐ Kubernetes       [1.0x Active 🟢] |  |
|  | Exp: [ - ]  5.0 yrs  [ + ]          |  |
|  | Last Used: [ 2026 (Active)     v ]  |  |
|  | Level: ( ) Beg   ( ) Int   (•) Exp  |  |
|  +------------------------------------+  |
|                                          |
|  +------------------------------------+  |
|  | ▫️ Kafka           [0.8x Recent 🟡] |  |
|  | Exp: [ - ]  4.5 yrs  [ + ]          |  |
|  | Last Used: [ 2024              v ]  |  |
|  | Level: ( ) Beg   (•) Int   ( ) Exp  |  |
|  +------------------------------------+  |
|                                          |
|  +------------------------------------+  |
|  | ▫️ Cassandra       [0.5x Legacy 🔴] |  |
|  | Exp: [ - ]  2.0 yrs  [ + ]          |  |
|  | Last Used: [ 2022              v ]  |  |
|  | Level: (•) Beg   ( ) Int   ( ) Exp  |  |
|  +------------------------------------+  |
|                                          |
|  [ + Add Missing Skill ]  [ Save Matrix ]|
+------------------------------------------+
```

### Screen 5: Predefined QA Profile Settings
```
+------------------------------------------+
|  < Back        SCREENING QA PROFILE      |
|------------------------------------------|
|  Auto-fills standard recruiter questions |
|  without invoking AI or alerting you:    |
|                                          |
|  Current CTC (LPA):    Expected CTC:     |
|  +---------------+     +---------------+ |
|  | 35.0          |     | 45.0          | |
|  +---------------+     +---------------+ |
|                                          |
|  Notice Period:                          |
|  +------------------------------------+  |
|  | 30 Days (Serving: No)            v |  |
|  +------------------------------------+  |
|                                          |
|  Preferred Locations:                    |
|  [Bangalore x] [Remote x] [Hyderabad x]  |
|                                          |
|  Willing to Relocate?   [ ON / OFF ]     |
|  Holding Other Offers?  [ ON / OFF ]     |
|                                          |
|        [ Save Screening Profile ]        |
+------------------------------------------+
```

### Screen 6: Mission Control & Daily Run
```
+------------------------------------------+
|  ⚡ AGENT ACTIVE             [ 🟢 Connected]|
|  Next Scan: Tomorrow at 09:00 AM         |
|------------------------------------------|
|  DAILY PILOT CAP:                        |
|  [■■■■■■■□□□] 3 of 5 Applied Today       |
|                                          |
|  AUTO-APPLY MATCH GATE (PERCENTAGE TAB): |
|  Apply to all jobs with score greater than:|
|  [ ≥60% ]   [ ≥70%* ]   [ ≥80% ]  [ ≥85% ]|
|  (4 qualifying jobs meet criteria today) |
|                                          |
|  LIVE RUN STATUS:                        |
|  +------------------------------------+  |
|  | 🟢 Scanning Naukri Listings...     |  |
|  | Last Job: Lead Cloud Architect     |  |
|  | Score: 88% • Status: Applied       |  |
|  +------------------------------------+  |
|                                          |
|  SAFETY & ANTI-BOT:                      |
|  • Pacing: Gaussian 14s wait active      |
|  • CAPTCHA Lock: 0 events detected       |
|                                          |
|   [  ⚡ RUN SCAN NOW  ]  [ Dry-Run Mode ] |
|------------------------------------------|
|  [🏠 Home]  [⚠️ Queue (1)]  [📋 Matches]  |
+------------------------------------------+
```

### Screen 7: Mobile Question Escalation Feed (Tier 3 Approval)
```
+------------------------------------------+
|  ⚠️ ACTION REQUIRED                      |
|  1 High-Match Job requires your review   |
|------------------------------------------|
|  Role: Staff Cloud Architect             |
|  Company: FinTech ScaleUp • Bangalore    |
|  Match Score: [ 92% Match 🟢 ]           |
|                                          |
|  Recruiter Question:                     |
|  "Describe your production experience    |
|   designing Kafka event streams?"        |
|                                          |
|  ✨ AI Draft (Strictly from resume):     |
|  +------------------------------------+  |
|  | Designed high-throughput Kafka     |  |
|  | streaming pipelines handling 50k   |  |
|  | events/sec in Go microservices.   |  |
|  +------------------------------------+  |
|  Confidence: 74% • Source: Resume Sec 4  |
|                                          |
|  [x] Remember this answer in SQLite      |
|                                          |
|  +------------------------------------+  |
|  |      [  ✅ APPROVE & APPLY  ]       |  |
|  +------------------------------------+  |
|             [  ⏭️ Skip Job  ]             |
+------------------------------------------+
```

### Screen 8: Application History & Match Radar
```
+------------------------------------------+
|  APPLICATION AUDIT TRAIL     [Filters v] |
|------------------------------------------|
|  [ All (12) ]  [ Applied (3) ]  [ Skipped ]
|                                          |
|  +------------------------------------+  |
|  | Staff Architect • FinTech Corp     |  |
|  | Applied Today at 09:05 AM          |  |
|  | Score: 92% 🟢 • Tier 3 (User Appr) |  |
|  | [ View Answers ]  [ View on Portal]|  |
|  +------------------------------------+  |
|                                          |
|  +------------------------------------+  |
|  | Senior Go Engineer • Cloud SaaS    |  |
|  | Applied Today at 09:02 AM          |  |
|  | Score: 84% 🟢 • Tier 1 (Auto-fill) |  |
|  +------------------------------------+  |
|                                          |
|  +------------------------------------+  |
|  | Full Stack Lead • Legacy Agency    |  |
|  | Filtered: Missing Cloud Skills     |  |
|  | Score: 48% ⚪ • Status: Skipped    |  |
|  +------------------------------------+  |
+------------------------------------------+
```

### Screen 9: Market Intelligence & Skill Gap Radar
```
+------------------------------------------+
|  < Back        SKILL GAP RADAR    [Export]|
|------------------------------------------|
|  Top missing technologies across jobs    |
|  scoring 50%–69% (Market Demand Trends): |
|                                          |
|  1. Kafka Streams (6 listings require)   |
|  [■■■■■■■■■■■■■■■□□□□□] 75% Demand       |
|  Impact: +6 jobs unlock • [ + Add ]      |
|                                          |
|  2. Terraform / IaC (5 listings require) |
|  [■■■■■■■■■■■■□□□□□□□□] 62% Demand       |
|  Impact: +5 jobs unlock • [ + Add ]      |
|                                          |
|  3. GraphQL API (4 listings require)     |
|  [■■■■■■■■■□□□□□□□□□□□] 50% Demand       |
|  Impact: +4 jobs unlock • [ + Add ]      |
|                                          |
|  4. OpenTelemetry (3 listings require)   |
|  [■■■■■■■□□□□□□□□□□□□□] 38% Demand       |
|  Impact: +3 jobs unlock • [ + Add ]      |
|                                          |
|  Market Salary Index:                    |
|  Avg Offered: ₹38L – ₹52L for Go + K8s   |
+------------------------------------------+
```

---

## 4. Desktop Widescreen Layout Wireframes (> 1024px)

```
+------------------------------------------------------------------------------------------------------------------------+
| ⚡ JOB AGENT WORKSTATION         [ 🟢 Naukri Session Valid ] [ Gaussian Delay: 14s ]    [ 👤 candidate@domain.com ]    |
+-------------------+----------------------------------------------------+-----------------------------------------------+
| NAVIGATION        | MASTER PANE (Listings / Mission Status)            | DETAIL INSPECTOR PANE (Match & QA Editor)     |
|                   |                                                    |                                               |
| [⚡] Mission Ctrl | Today's Postings (Mon-Sat 09:00 AM Scan):          | Target: Staff Cloud Architect (92% Match 🟢)  |
| [⚠️] Queue (1)     | -------------------------------------------------- | Company: FinTech ScaleUp • Bangalore / Hybrid |
| [📋] Matches (12)  | • [92%] Staff Cloud Architect — FinTech ScaleUp    | Auto-Apply Threshold: ≥ 70% [QUALIFIED]       |
| [📊] Skill Radar   | • [84%] Senior Go Engineer — CloudSaaS Global      | --------------------------------------------- |
|                   | • [48%] Full Stack Lead — Legacy Agency [Filtered] | Recruiter Screening Question (Tier 3 Review): |
| STUDIO & SETTINGS |                                                    | "Describe your production experience with     |
| [🔒] Naukri Vault | Daily Quota Cap: [■■■■■■■□□□] 3 / 5 Applied        |  distributed Kafka pipelines in Go?"          |
| [📄] Resume Studio|                                                    |                                               |
| [⭐] Skill Matrix  | Match Gate: [ ≥60% ] [ ≥70%* ] [ ≥80% ] [ ≥85% ]   | ✨ AI Suggested Answer (Resume Section 4):    |
| [⚙️] Screening QA  | (4 jobs qualify for automatic submission today)    | +-------------------------------------------+ |
|                   |                                                    | | Designed high-throughput Kafka streaming  | |
| SYSTEM STATUS     | Live SSE Execution Stream:                         | | pipelines handling 50k events/sec in Go.  | |
| SQLite WAL: OK    | [09:05:12] Found 14 fresh postings in last 24h     | +-------------------------------------------+ |
| Playwright: Ready | [09:05:40] Lead SRE (84%) -> Auto-Applied (T1)     | Confidence: 74% • Citations: Project Delta    |
| Tailscale: Active | [09:06:05] Staff Arch (92%) -> Pushed to Queue (T3)|                                               |
|                   |                                                    | [x] Remember this answer in SQLite Cache      |
| [ ? Shortcuts ]   | Action Triggers:                                   |                                               |
| [ J/K ] Navigate  | [ ⚡ Run Scan Now ]  [ Dry-Run (Score Only) ]       | [  ✅ APPROVE & APPLY (A) ]   [ SKIP (S) ]    |
| [ A ]   Approve   |                                                    |                                               |
| [ S ]   Skip      |                                                    | Side-by-Side Resume Diff:                     |
| [ R ]   Run Now   |                                                    | • Go (6 yrs, 2026): Match 1.0x                |
| [ / ]   Search    |                                                    | • Kubernetes (5 yrs, 2026): Match 1.0x        |
|                   |                                                    | • Kafka (4.5 yrs, 2024): Match 0.8x           |
+-------------------+----------------------------------------------------+-----------------------------------------------+
```

---

## 5. Modal Dialog Specifications

### 5.1 Circuit Breaker & CAPTCHA Safety Modal (`CAL-MODAL-01`)
```
+-------------------------------------------------------------+
| ⚠️ BOT CHALLENGE DETECTED — AGENT PAUSED                    |
+-------------------------------------------------------------+
| The portal crawler encountered a security verification on: |
| Portal: Naukri (https://www.naukri.com/login)               |
| Challenge Type: Cloudflare Turnstile / CAPTCHA Modal        |
|                                                             |
| [ Screenshot of Portal Verification Screen ]                |
|                                                             |
| Instructions:                                               |
| 1. Open the portal in your browser or solve the displayed   |
|    verification challenge manually.                         |
| 2. Do not brute force automated retries to protect account. |
|                                                             |
| [  ✅ I Solved It — Resume Crawler  ]   [  Abort Run  ]      |
+-------------------------------------------------------------+
```

---

## 6. React Component Tree & Hook Architecture

```
web/src/
├── components/
│   ├── layout/
│   │   ├── AppShell.tsx            <-- Responsive wrapper (Drawer/Sidebar + TopBar + BottomNav)
│   │   ├── DesktopSidebar.tsx      <-- 240px fixed left workstation rail
│   │   ├── MobileBottomNav.tsx     <-- Mobile 4-tab thumb dock
│   │   └── CircuitBreakerModal.tsx <-- Global event-driven CAPTCHA pause dialog
│   ├── mission/
│   │   ├── MissionControl.tsx      <-- Live scan telemetry, quota progress, and run triggers
│   │   └── MatchGateSelector.tsx   <-- Threshold tabs (≥60%, ≥70%, ≥80%, ≥85%)
│   ├── queue/
│   │   ├── QuestionQueue.tsx       <-- Tier 3 HITL question cards
│   │   └── InlineAnswerEditor.tsx  <-- AI draft textarea with citation badge
│   ├── matches/
│   │   ├── MasterDetailSplit.tsx   <-- Desktop dual pane layout
│   │   └── MatchInspector.tsx      <-- Resume vs. Job Description diff visualizer
│   ├── radar/
│   │   └── SkillGapChart.tsx       <-- Horizontal bar chart of top 10 market gaps
│   └── studio/
│       ├── NaukriVault.tsx         <-- AES-256-GCM encrypted portal credential manager
│       ├── ResumeStudio.tsx        <-- Drag-and-drop PDF/DOCX ingestion
│       ├── SkillRecencyMatrix.tsx  <-- Steppers, last-used years, and level selection dots
│       └── PredefinedQAProfile.tsx <-- Standard screening questions form
└── hooks/
    ├── useEventStream.ts           <-- SSE connection manager with auto-reconnect
    ├── useKeyboardShortcuts.ts     <-- Global hotkeys (A, S, J, K, R, Space, /)
    └── useResponsiveLayout.ts      <-- Breakpoint observer (<640px, 640-1024px, >1024px)
```

