# Dissertation / Project Work Outline & Abstract

**Dissertation / Project / Project Work Title:**  
**Autonomous Multi-Agent System for Intelligent Job-Matching, Dynamic Skill-Recency Profiling, and Human-in-the-Loop Application Proxy**

- **Course No. :** `[Insert Course No., e.g., BITS ZG629T / SS ZG629T]`
- **Course Title:** Dissertation / Project / Project Work
- **Dissertation / Project / Project Work Done by:**  
  - **Student Name:** `[Insert Student Name]`
  - **BITS ID:** `[Insert Student ID, e.g., 2024xxxxxxx]`
  - **Degree Program:** `[Insert Degree Name, e.g., M.Tech in Software Systems / AI & ML]`
  - **Research Area:** Artificial Intelligence, Autonomous Multi-Agent Systems, Natural Language Processing, and Information Retrieval
- **Dissertation / Project Work carried out at:**  
  `[Insert Organization Name & Location, e.g., Employing Organization Name, Bangalore, India]`

---

```
                       /\
                      /  \
                     /    \
                    / BITS \
                   / PILANI \
                  /__________\
   BIRLA INSTITUTE OF TECHNOLOGY & SCIENCE, PILANI
        VIDYA VIHAR, PILANI, RAJASTHAN - 333031
```

**Submission Date / Term:** `[Insert Month and Year, e.g., November 2026]`

---

## Contents

1. [Broad Area of Work](#1-broad-area-of-work)
2. [Background](#2-background)
3. [Objectives](#3-objectives)
4. [Scope of Work & Multi-Agent Architecture](#4-scope-of-work--multi-agent-architecture)
5. [Plan of Work](#5-plan-of-work)
6. [Literature References](#6-literature-references)
7. [Particulars of the Supervisor and Examiner](#7-particulars-of-the-supervisor-and-examiner)
8. [Remarks of the Supervisor](#8-remarks-of-the-supervisor)
9. [BITS Pilani WILP Division Outline Sheet](#9-bits-pilani-wilp-division-outline-sheet)

---

## 1. Broad Area of Work

Autonomous AI agents, Retrieval-Augmented Generation (RAG), and Multi-Agent Orchestration represent foundational frontiers in modern Information Science and applied Artificial Intelligence. While classical search and recommendation systems act as passive retrieval mechanisms, next-generation agentic workflows transition systems from passive inquiry to **goal-driven autonomous action** in complex, semi-structured web environments.

The broad range of this dissertation spans Artificial Intelligence, Natural Language Processing (NLP), Web Mining, and Distributed Multi-Agent Systems, focusing on the following core domains:

1. **Natural Language Processing & Information Extraction (IE):** Dynamic semantic parsing of unstructured candidate resumes (PDF/DOCX), lexical normalization of technical skills, taxonomy-based ontology mapping, and contextual entity recognition.
2. **Mathematical Retrieval & Recency Decay Modeling:** Multi-factor weighted ranking algorithms that balance core technical competence, years of experience, and temporal recency decay ($\gamma$) to eliminate legacy skill mismatches.
3. **Retrieval-Augmented Grounding & Reasoning:** Zero-hallucination question-answering powered by Large Language Models (LLMs) strictly constrained by verified candidate factual profiles and resume citations.
4. **Autonomous Web Agents & Anti-Detection Automation:** Headless browser orchestration (Playwright/Chrome DevTools Protocol) with stochastic Gaussian pacing, human typing cadences, and session state serialization.
5. **Human-in-the-Loop (HITL) Machine Collaboration:** Mobile-first, asynchronous event-driven escalation protocols (Server-Sent Events) that solicit real-time human micro-approvals for low-confidence or subjective decision boundaries.

---

## 2. Background

In today's highly competitive recruitment ecosystem, finding relevant employment opportunities on major talent portals (e.g., Naukri, LinkedIn) is a time-consuming, repetitive, and cognitively fatiguing process for software professionals. Candidates typically spend 30 to 60 minutes daily manually browsing listings, filtering out irrelevant postings, parsing repetitive employer questionnaires, and submitting applications.

Conventional automation tools and simplistic web scrapers fail in real-world recruitment settings due to several critical shortcomings:
1. **Lack of Dynamic Grounding:** Naive scrapers blindly apply to postings using static keywords, ignoring the candidate's actual depth and recency of experience (e.g., applying for senior Kafka roles based on skills last utilized five years ago).
2. **Hallucination in Automated Question Answering:** Modern job portals embed mandatory, non-standard screening questionnaires (e.g., *"Describe your production experience with distributed event streaming in Go"*). Primitive bots either crash, guess randomly, or generate unverified hallucinations that lead to immediate recruiter disqualification.
3. **Aggressive Bot Detection & IP Blacklisting:** Job portals employ sophisticated anti-bot firewalls (e.g., Cloudflare, CAPTCHAs, behavioral mouse tracking). Scripted requests with mechanical periodicity are rapidly detected and banned.
4. **Absence of User Supervision:** Existing tools operate as "black boxes" with no seamless supervision mechanism, leaving candidates unaware of what data or answers were submitted on their behalf.

To address this challenge, this dissertation designs and develops an **autonomous, privacy-preserving, multi-agent application proxy**. The system delegates repetitive discovery and form resolution to specialized AI sub-agents while placing a **10-second mobile remote control** in the candidate's hands for high-confidence supervision.

---

## 3. Objectives

The primary research and engineering objectives of this project are:

1. **Investigate Agentic Workflow Patterns:** Analyze state-of-the-art autonomous agent frameworks, tool-use paradigms, and Retrieval-Augmented Generation (RAG) strategies for goal-directed web tasks.
2. **Formulate a Dynamic Skill-Recency Mathematical Matching Model:** Develop a weighted ranking function incorporating years of experience, skill hierarchy, and time-decay penalty ($\gamma$) to ensure applicants are matched only with roles reflecting active competencies ($\ge 70\%$ match score).
3. **Engineer a 3-Tier Autonomous Questionnaire Resolution Cascade:**
   - *Tier 1 (Deterministic Profile):* Regex and fuzzy matching for standardized screening parameters (compensation, notice period, location).
   - *Tier 2 (Grounded LLM Reasoning):* Schema-enforced LLM inference strictly grounded in resume facts with confidence thresholds ($\ge 85\%$) and zero-hallucination guardrails.
   - *Tier 3 (Human-in-the-Loop Escalation):* Asynchronous mobile push notifications allowing 1-tap candidate review and approval for subjective or borderline questions.
4. **Develop a Specialized Multi-Agent Web Automation Pipeline:** Build autonomous agents (Crawler Agent, Matching Agent, QA Agent, Memory Agent) that operate with stealth Playwright profiles, Gaussian human delays (8s–25s), and automated session preservation.
5. **Implement Hardware-Level Credential Protection & Local Data Self-Containment:** Ensure zero plaintext credential leakage by implementing AES-256-GCM encryption at rest, memory-only session decryption, and local SQLite storage with online backup snapshots.
6. **Empirical Prototype Validation & User Evaluation:** Deploy and test the prototype across live job portal workflows (e.g., Naukri) under a controlled daily application cap (5/day pilot, scaling to 15/day) to quantify time-savings, match accuracy, auto-resolution rates, and account safety.

---

## 4. Scope of Work & Multi-Agent Architecture

The scope of this dissertation covers the end-to-end design, implementation, and empirical validation of an autonomous multi-agent proxy system. The architecture is decomposed into the following specialized agents and components:

```
+-------------------------------------------------------------------------+
|                  1. CANDIDATE ACCESS LAYER (UI & INGRESS)               |
|   Mobile PWA & Desktop Dashboard • Biometric Auth • Mission Control     |
+------------------------------------+------------------------------------+
                                     |
                                     v
+-------------------------------------------------------------------------+
|                2. MULTI-AGENT AUTONOMOUS CORE & ADAPTERS                |
|                                                                         |
|  +---------------------+   +---------------------+   +---------------+  |
|  | Resume Parsing      |   | Stealth Portal      |   | Job Matching  |  |
|  | Agent               |   | Crawler Agent       |   | Agent         |  |
|  | (PDF/DOCX Extractor)|   | (Naukri/Playwright) |   | (Recency 70%) |  |
|  +----------+----------+   +----------+----------+   +-------+-------+  |
|             |                         |                      |          |
|             +-------------------------+----------------------+          |
|                                       |                                 |
|                                       v                                 |
|                 +-----------------------------------------+             |
|                 | 3-Tier QA Reasoning Agent               |             |
|                 | (T1 Regex | T2 LLM Grounding | T3 HITL) |             |
|                 +---------------------+-------------------+             |
|                                       |                                 |
|                                       v                                 |
|                 +-----------------------------------------+             |
|                 | Question Memory & Semantic Cache Agent  |             |
|                 | (SQLite Permanent Deduplication Engine) |             |
|                 +-----------------------------------------+             |
+------------------------------------+------------------------------------+
                                     |
                                     v
+-------------------------------------------------------------------------+
|                   3. LOCAL DATA & ENCRYPTED STORAGE                     |
|  SQLite (WAL Mode) • AES-256-GCM Vault • VACUUM INTO Daily Backups      |
+-------------------------------------------------------------------------+
```

### Detailed Agent Responsibilities:

1. **Resume Ingestion & Parsing Agent:**
   - Ingests candidate master resumes in PDF and DOCX formats.
   - Extracts structured work history, project narratives, and technical skills into an interactive matrix with **Years of Experience**, **Last Used Year**, and proficiency levels (**Beginner, Intermediate, Expert**).

2. **Stealth Portal Crawler Agent (Naukri Connector):**
   - Interacts with job portals using Playwright and the Chrome DevTools Protocol.
   - Applies anti-detection measures: user-agent masking, dynamic viewport emulation, randomized Gaussian delay pacing (8s–25s), and circuit breaker pauses on challenge screens.
   - Handles automated login with AES-256-GCM encrypted credentials and serializes authenticated session cookies.

3. **Job Matching & Recency Decay Agent:**
   - Computes weighted technical relevance against required and preferred skills.
   - Implements the mathematical recency multiplier $\gamma(s)$:
     $$\gamma(s) = \begin{cases} 1.0 & \Delta Y \le 1 \text{ (Active)} \\ 0.8 & \Delta Y = 2 \text{ (Recent)} \\ 0.5 & \Delta Y \ge 3 \text{ (Legacy Penalty)} \end{cases}$$
   - Filters out listings scoring below the candidate's configurable auto-apply match gate ($\ge 60\%, \ge 70\%, \ge 80\%, \ge 85\%$) or violating hard constraints (current employer, blacklisted consultancies, location).

4. **3-Tier QA Reasoning Agent:**
   - **Tier 1 (Pre-configured Rule Engine):** Matches recurring standard questions (`CTC`, `notice period`, `current location`) against pre-configured candidate profiles using regular expressions.
   - **Tier 2 (Grounded LLM Reasoning Engine):** Ingests non-standard technical questions and resume context. Generates schema-validated answers with required citations. Auto-submits if confidence $\ge 85\%$.
   - **Tier 3 (Human-in-the-Loop Mobile Feed):** For subjective or borderline questions, pushes an interactive card to the mobile app with an editable AI draft. Tapping *"Approve & Apply"* executes submission in real time.

5. **Question Memory & Semantic Cache Agent:**
   - Normalizes and hashes all answered questions into a persistent SQLite memory store.
   - Guarantees that any identical or semantically equivalent recruiter question is never presented to the candidate more than once.

6. **Candidate Access Layer (Mobile App & Desktop UI):**
   - Mobile-first Progressive Web App (PWA) with a "Welcome" authentication screen, face/biometric unlock, Naukri credential provisioning, interactive skill matrix, and Mission Control quota meters.

---

## 5. Plan of Work

The project is structured into distinct, sequential milestones across the academic semester:

| Phases | Duration / Milestones | Detailed Work to be Done |
| :--- | :--- | :--- |
| **Phase 1: Problem Definition & Literature Review** | Weeks 1 – 3 | Comprehensive literature review on Autonomous Agents, RAG Grounding, and Anti-Detection Web Automation. Prepare detailed project outline and requirements specification (`REQUIREMENTS.md`). |
| **Phase 2: Architectural Design & Security Modeling** | Weeks 4 – 6 | Formulate multi-agent high-level design (`ARCHITECTURE.md`). Design AES-256-GCM vault, SQLite WAL relational schema, and the mathematical skill-recency decay algorithm. Create component and sequence diagrams. |
| **Phase 3: Agent Core Development & Parser Engineering** | Weeks 7 – 10 | Implement Resume Ingestion Agent (PDF/DOCX extraction). Build Playwright Stealth Crawler Agent with Gaussian pacing. Construct the 3-Tier QA Reasoning Engine and Question Memory store. |
| **Phase 4: Candidate Access Layer & Mobile Feed** | Weeks 11 – 13 | Build the mobile-first frontend UI (`ui/`). Implement Candidate Authentication, Naukri Portal Vault, Dynamic Skill Matrix (with Beginner/Intermediate/Expert selectors), and Mission Control auto-apply percentage tabs ($\ge 60\% \dots \ge 85\%$). |
| **Phase 5: Prototype Testing & User Evaluation** | Weeks 14 – 15 | Conduct live pilot runs under a 5 applications/day cap. Evaluate matching precision, questionnaire auto-resolution rate, prompt grounding accuracy, and zero-CAPTCHA safety. |
| **Phase 6: Dissertation Review & Final Submission** | Weeks 16 – 17 | Compile dissertation report, document experimental results and ablation studies, present work to Supervisor and Examiner, and complete final submission. |

---

## 6. Literature References

1. **J. Wei, X. Wang, D. Schuurmans, et al.** "Chain-of-thought prompting elicits reasoning in large language models." *Advances in Neural Information Processing Systems (NeurIPS)*, 35:24824–24837, 2022.
2. **P. Lewis, E. Perez, A. Piktus, et al.** "Retrieval-augmented generation for knowledge-intensive NLP tasks." *Advances in Neural Information Processing Systems (NeurIPS)*, 33:9459–9474, 2020.
3. **L. Wang, C. Ma, X. Feng, et al.** "A survey on large language model based autonomous agents." *Frontiers of Computer Science*, 18(6):186345, 2024.
4. **Q. Wu, G. Bansal, J. Zhang, et al.** "AutoGen: Enabling next-gen LLM applications via multi-agent conversation." *arXiv preprint arXiv:2308.08155*, 2023.
5. **S. Yao, J. Zhao, D. Yu, et al.** "ReAct: Synergizing reasoning and acting in language models." *International Conference on Learning Representations (ICLR)*, 2023.
6. **M. Shridhar, X. Yuan, M. Côté, et al.** "ALFWorld: Aligning text and embodied environments for interactive learning." *International Conference on Learning Representations (ICLR)*, 2021.
7. **J. R. Trippas, D. Spina, L. Cavedon, H. Joho, and M. Sanderson.** "Informing the design of spoken conversational search: Perspective paper." *Proceedings of the 2018 Conference on Human Information Interaction & Retrieval (CHIIR '18)*, pages 32–41, ACM, 2018.
8. **N. Belkin.** "Anomalous states of knowledge as a basis for information retrieval." *The Canadian Journal of Information Science*, 5:133–143, 1980.
9. **S. Avula, G. Chadwick, J. Arguello, and R. Capra.** "Searchbots: User engagement with chatbots during collaborative search." *Proceedings of the 2018 Conference on Human Information Interaction & Retrieval*, pages 52–61. ACM, 2018.
10. **A. Kaushik and G. J. F. Jones.** "Exploring current user web search behaviours in analysis tasks to be supported in conversational search." *Second International Workshop on Conversational Approaches to Information Retrieval (CAIR '18)*, Ann Arbor, MI, USA, 2018.

---

## 7. Particulars of the Supervisor and Examiner

| Particulars | Supervisor | Additional Examiner |
| :--- | :--- | :--- |
| **Name** | `[Insert Supervisor Name]` | `[Insert Examiner Name]` |
| **Qualification** | `[Insert Supervisor Qualification, e.g., Ph.D., M.Tech]` | `[Insert Examiner Qualification]` |
| **Designation** | `[Insert Designation, e.g., Technical Director / Professor]` | `[Insert Examiner Designation]` |
| **Employing Organization and Location** | `[Insert Organization & Location]` | `[Insert Organization & Location]` |
| **Phone No. (with STD Code)** | `[Insert Phone Number]` | `[Insert Phone Number]` |
| **Email Address** | `[Insert Supervisor Email]` | `[Insert Examiner Email]` |

---

## 8. Remarks of the Supervisor

*(Draft evaluation statement for the Supervisor's endorsement)*

> "The proposed dissertation project addresses an innovative, highly relevant problem at the intersection of Autonomous AI Agents, Information Retrieval, and Human-Computer Interaction. The student has formulated a rigorous multi-agent architecture featuring stealth browser orchestration, dynamic skill-recency decay modeling, and a 3-tier questionnaire answering cascade with human-in-the-loop mobile escalation.
> 
> The project incorporates essential engineering guardrails including hardware-grade AES-256-GCM credential encryption, deterministic ground-truth verification, and anti-bot pacing mechanisms. The proposed methodology, comprehensive literature foundation, and empirical validation plan on live recruitment workflows satisfy the academic standards and technical depth required for master's degree dissertation research. I approve the project proposal and outline as the supervisor."

---

## 9. BITS Pilani WILP Division Outline Sheet

### BIRLA INSTITUTE OF TECHNOLOGY & SCIENCE, PILANI  
**WORK INTEGRATED LEARNING PROGRAMMES (WILP) DIVISION**  
**ACADEMIC YEAR 2026–2027**  

#### DISSERTATION / PROJECT WORK OUTLINE

| Identification Field | Student & Supervisor Particulars |
| :--- | :--- |
| **STUDENT ID No.** | `[Insert Student ID, e.g., 2024xxxxxxx]` |
| **NAME OF THE STUDENT** | `[Insert Student Name]` |
| **STUDENT'S EMAIL ADDRESS** | `[Insert Student Email, e.g., f2024xxxx@pilani.bits-pilani.ac.in]` |
| **STUDENT’S EMPLOYING ORGANIZATION & LOCATION** | `[Insert Employing Organization & City]` |
| **SUPERVISOR’S NAME** | `[Insert Supervisor Name]` |
| **SUPERVISOR’S EMPLOYING ORGANIZATION & LOCATION** | `[Insert Supervisor Organization & City]` |
| **SUPERVISOR’S EMAIL ADDRESS** | `[Insert Supervisor Email]` |
| **ADDITIONAL EXAMINER’S NAME** | `[Insert Additional Examiner Name]` |
| **ADDITIONAL EXAMINER’S EMPLOYING ORGANIZATION & LOCATION** | `[Insert Examiner Organization & City]` |
| **ADDITIONAL EXAMINER’S EMAIL ADDRESS** | `[Insert Examiner Email]` |
| **DISSERTATION / PROJECT WORK TITLE** | **Autonomous Multi-Agent System for Intelligent Job-Matching, Dynamic Skill-Recency Profiling, and Human-in-the-Loop Application Proxy** |

---

### Endorsement Signatures

| | | |
| :---: | :---: | :---: |
| &nbsp; | &nbsp; | &nbsp; |
| _______________________________ | _______________________________ | _______________________________ |
| **Signature of Student** | **Signature of Supervisor** | **Signature of Additional Examiner** |
| **Name:** `[Insert Student Name]` | **Name:** `[Insert Supervisor Name]` | **Name:** `[Insert Examiner Name]` |
| **Date:** `[Insert Date]` | **Date:** `[Insert Date]` | **Date:** `[Insert Date]` |
