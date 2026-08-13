<!--
  CURATED MASTER CV CONTENT BANK — CV-voice bullet / skill / project bank for José Pedro Nolasco Henriques.

  PROVENANCE
  - Source of truth: the USI corpus (C:\Users\josep\Desktop\Dev\USI). This file is a USI-DERIVED artifact.
  - Imported on 2026-07-23 from the legacy build-cv-usi master
    (CV builder/CV_material/CV_Complete_USI_Jose_Henriques.md), validated over 44 past applications.
  - KEPT IN SYNC BY /sync-usi (Step 2, target #5): the skill reconciles FACTS ONLY against the
    USI packs (dates, metrics, titles, entries) while preserving the curated CV-voice phrasing.
    Do not hand-edit facts here. New facts go into the USI corpus, then re-run /sync-usi.
  - Last reconciled against USI: 2026-08-13. Two passes: (1) tooling/skills refresh - Qwen, LangChain,
    ChromaDB, OpenClaw, Docker, Cloudflare Tunnel, UiPath/RPA, eval-harness design, PII-redaction
    design, containerized deployment; countries 16+->20+; finance-markets interest bullet.
    (2) COVERAGE AUDIT against all 57 cv-audience USI blocks - found two whole projects missing from
    this bank (project-usi-rag, the only unrepresented `featured: true` block, and project-usi-corpus)
    and added them; rewrote the RAG entry, which had been carrying only v1 (rag-mini) and badly
    understated the work. Audit for MISSING BLOCKS on every sync, not just facts inside existing lines.

  PROJECT ENTRY FORMAT (mandatory since 2026-08-13)
  - Every project is THREE lines: **Title**, then *Tech stack: a · b · c*, then the description.
    The .tex twin renders this as \cvproject{Title}{Tech stack}{Description} (three args).
  - The stack line must fit ONE rendered line (~95 chars incl. the "Tech stack: " label).
    Trim items rather than wrap. Items trace to the USI block's `stack` frontmatter.
  - Titles and descriptions must NOT repeat the stack: no "(Python + Ollama)" title suffix,
    no "built with X, Y, Z" prose. Description = what it is + what came of it.

  ROLE UNDER THE HYBRID /apply WORKFLOW (active since 2026-07-23)
  - This file IS the verbatim-selection master: every tailored-CV line except the About Me
    paragraph must be an exact copy of a line in here. /apply picks and orders; it never rewords.
  - applications/main_example.tex is this same content rendered in the compact LaTeX template
    (the copy-base for tailored CVs). /sync-usi keeps the two line-for-line identical.
  - See applications/HYBRID_TRIGGER.md and the cv-tailoring-philosophy memory.
-->

# José Pedro Henriques
Portuguese | (+351) 912 678 001 | josepedronolasco@gmail.com | Portfolio: tykelar.github.io | LinkedIn: josepedroh | GitHub: Tykelar

---

## About Me
<!-- Rendered WITHOUT the "About Me" heading on the CV: separator rule + text only.
     The headline line was dropped from the CV header on 2026-07-23 (José's call);
     headline variants still exist in the USI summary block for LinkedIn/other use.
     Self-description in the opening clause is "Software Engineer" (default, this
     file) or "AI Automation Engineer" for AI-agent/AI-automation-heavy roles -
     pick per posting. Never "Software Quality Engineer" as self-description;
     that stays only as the literal Work Experience job header for Glartek. -->

Computer Engineering MSc and Software Engineer who re-engineers delivery infrastructure, improves engineering velocity, and integrates AI into engineering workflows. At a technology company I led a Lean-driven re-engineering of the delivery pipeline, from diagnosing accumulated technical debt through to measurable gains in delivery speed and reliability, formalized in a master's thesis on Lean CI/CD and AI-ready infrastructure. Alongside this I founded and ran a cooperative through its full operational lifecycle, and bring a systems-level perspective spanning applied AI, immersive technologies, and cybersecurity. Get to know me better [here](https://tykelar.github.io)!

---

## Education

**Master's in Computer Engineering** | Polytechnic University of Leiria | Sep 2024 – Jul 2026
*Thesis: Lean-Driven QA & CI/CD Re-Engineering Towards AI-Ready Infrastructures (18/20)*

**Bachelor's in Computational Engineering** | University of Aveiro | Sep 2021 – Jul 2024
*Final Project: Big Data Analysis & Representation, NO2 Air Pollution in VR (17/20)*

**Electrotechnical Engineering (1 year)** | ESTGA, University of Aveiro | Sep 2020 – Jul 2021

---

## Work Experience

### Software Quality Engineer, Glartek | Sep 2025 – Jun 2026
*AI-native, mobile-first, no-code EHSQ (Environment, Health, Safety & Quality) Connected Worker platform for frontline industrial operations.*
- Built AI agent skills deployed in internal engineering repositories, enabling automated assistance for complex engineering and process workflows.
- Led a Lean-driven re-engineering of delivery infrastructure and processes, resolving accumulated technical debt and cutting total pipeline job time by more than 50%.
- Redesigned delivery and engineering workflows, contributing to up to 20% more features deployed per sprint.
- Restructured task distribution and handovers, reducing time consumption around 30% and eliminating duplicated work.
- Contributed to the architecture and testing of an embedded AI chatbot that helps users navigate the platform.
- Contributed to the architecture and testing of a RAG system letting users query their own uploaded documents.
- Drove integration of AI agents and services into product and engineering workflows.
- Collaborated on an in-house image-recognition application built on YOLO object detection: labeled and curated the training dataset, helped define detection classes, and ran and evaluated training and optimization tests.
- Designed and implemented a test framework in Playwright, including reusable helpers and utilities for scalable coverage.
- Integrated the automated test battery into GitLab CI pipeline jobs, enabling fully automated execution as part of workflow.
- Led the Cypress to Playwright migration, including trade-off evaluation, implementation, and documentation.
- Standardized test naming and data conventions and introduced seed-driven data setup to reduce coupling and instability.
- Scripted reproducible local and virtual test environments (seed, rebuild, reinitialize services) in Shell/Bash to improve dev experience.
- Maintained and extended an existing Cypress battery; analyzed self-built reports and failure patterns to prioritize fixes.

### Founder & President, Florescer (Cooperative) | Jan 2023 – May 2026
*Non-profit cooperative working on local educational, social, and environmental initiatives.*
- Founded a non-profit cooperative: legal incorporation, administrative setup, governance structure, and ongoing compliance.
- Owned the full entrepreneurial process from idea to operational execution with no prior institutional support.
- Coordinated partnerships with public and private institutions to fund and support community programmes.
- Led educational activities, community workshops, and public-space renovation initiatives.
- Organized and monitored internal procedures for consistent operational execution.
- Managed the full physical setup and operational launch of a café/restaurant space and a nursing-school space.

### Warehouse Manager Assistant, Airking | Jul 2020 – Sep 2020
- Organized inventory, materials, and warehouse and storage flows.
- Optimized storage and transport procedures, improving handling and distribution time by up to 20%.
- Supported the full logistics cycle (picking, dispatch, transport, retrieval); drove forklift for load handling.
- Performed technical assembly support, including ventilation conduit assembly.

### Hospitality Consultant, IMPACT Consulting, Malta | Jul 2018 – Aug 2018
- Built Excel databases from publicly available company information for business outreach.
- Conducted company and individual outreach for partnership opportunities.
- Produced documentation linking travel agencies and hospitality brands.

---

## Languages

Portuguese: Native (C2) · English: C2 · Spanish: B1 · French: A1

---

## Skills

**Process, Operations & Continuous Improvement:** Process analysis and mapping · Workflow re-engineering · Operational efficiency · Waste identification and prioritization · Procedure standardization · Task ownership and handover design · KPI design and tracking · Lean Software Development · Technical debt diagnosis and remediation · Continuous improvement (PDCA / Kaizen) · Process automation (RPA, UiPath)
**QA, Testing & Reliability:** Software QA (manual and automated) · End-to-end test framework design (Playwright) · Reusable test helpers and utilities · Cypress maintenance and extension · API integration testing · Component-level unit testing · Test pyramid design and coverage rebalancing · Flaky test mitigation · Seed-driven test data · Failure-pattern and log analysis · Shift-left quality · Eval and benchmark harness design (golden sets, controlled A/B)
**CI/CD, DevOps & Delivery:** CI/CD foundations and practical application · Pipeline optimization and feedback-loop reduction · Build/test resource efficiency · CI job integration for test batteries · Test parallelization · GitLab MR label and workflow governance · Local environment automation scripting · Environment reproducibility · Containerized deployment (Docker Compose) · Tooling and migration assessment
**Applied AI & Machine Learning:** CNNs and image classification · YOLO object detection · RNNs and sequence prediction · Transfer Learning · Hyperparameter optimization (Optuna) · LLM integration and AI agents · RAG system design, testing and evaluation (recall@k benchmarking) · Vector databases (Chroma) · LangChain · Chatbot and embedded AI chat · Local LLM deployment (Ollama, Gemma, Qwen) · Prompt engineering
**Cybersecurity & Defensive Engineering:** Offensive security · OSINT and footprinting · Vulnerability assessment and reporting · SIEM implementation and log centralization · Threat detection and alerting · Host-based intrusion detection (HIDS) · File integrity monitoring · Wazuh and Elastic Stack (ELK) · Data privacy and PII redaction pipeline design
**Immersive Tech, 3D & Visualization:** Virtual and Augmented Reality · Digital Twins · 3D modelling and printing · VTK 2D/3D/VR visualization · Unity (C#) · Godot · Blender · VRChat SDK · Additive manufacturing and rapid prototyping
**Data, Analysis & Reporting:** Excel database creation and maintenance · Data structuring and reporting · SQL data handling · SPSS statistics · KPI and operational metric tracking · Analytical reasoning
**Engineering Foundations:** Physics and Mathematics (classical and quantum mechanics) · Scientific computing and simulation (MATLAB) · Engineering drawings · Systems and computer hardware architecture · Elementary electrical circuits
**Programming Languages:** Python · TypeScript · JavaScript · Java · C# (Unity) · React Native · SQL Server / SQL · MATLAB · Shell / Bash · Assembly · C
**Tools & Platforms:** Playwright · Cypress · GitLab CI · Bash / Shell · Git · MS Project · Excel · SQL · SPSS · Unity · Godot · Blender · VRChat SDK · VTK · Ollama (Gemma, Qwen) · LangChain · ChromaDB · OpenClaw · Docker / Docker Compose · Cloudflare Tunnel · UiPath · Wazuh · Elastic Stack (ELK) · Microsoft 365
**Soft Skills:** Initiative and autonomy · Problem-solving (root-cause-first) · Fast learning and resilience · Leadership and team dynamics · Communication with technical and non-technical stakeholders · Adaptability

---

## Projects

**Lean-Driven QA & CI/CD Re-Engineering Towards AI-Ready Infrastructures (Master's Thesis)**
*Tech stack: CI/CD architecture · QA architecture · Test-suite optimization · Research*
Research into engineering infrastructures that stay scalable, understandable, and ready for AI integration: CI/CD architecture, QA integration, shift-left quality, flakiness dynamics, and toolchain-migration criteria. Directly informed by the Glartek work.

**Big Data Analysis & Representation: NO2 Air Pollution in VR (Bachelor's Final Project)**
*Tech stack: OpenXR · VTK · Unity · 3D*
A VR system for visualizing large-scale NO2 air-pollution data across an urban area, with a user study comparing VR and desktop interaction. Supervised by Prof. Paulo Dias (IEETA, University of Aveiro).

**Niche-Field SaaS Marketing & Admin Platform**
*Tech stack: TypeScript · React · Express · PostgreSQL · Drizzle · Zod · Playwright · Vercel*
A multi-tenant SaaS platform helping businesses in a niche field market themselves and manage the information central to their operations. Built solo end to end: architecture, data model, API, UI, auth, testing, and deploy.

**Shared Expense Tracker (Serverless PWA)**
*Tech stack: TypeScript · React · Supabase · PostgreSQL (RLS) · Google OAuth · Workbox*
A private, installable expense-tracking PWA for two people, deliberately built with no backend of my own to maintain, with authorization enforced in the database rather than in the client. Delivered solo end to end.

**USI-RAG: Production RAG Chatbot**
*Tech stack: Python · LangChain · ChromaDB · Ollama · Docker Compose · Cloudflare Tunnel*
A publicly deployed chatbot answering visitor questions over a structured personal knowledge corpus. Every retrieval change is gated by a 27-case golden evaluation set; controlled A/B testing exposed a silent embedding-tokenizer defect degrading every measurement, and fixing it raised recall@5 from 56% to 70%. Ships behind an audience-filtering and PII-redaction safety gate.

**From-Scratch Local RAG Pipeline**
*Tech stack: Python · Ollama · nomic-embed-text · numpy*
A framework-free local RAG pipeline built to turn RAG theory into hands-on implementation. Built a recall@k evaluation harness, then caught the evaluation itself being too permissive: tightening the ground truth dropped apparent recall@1 from 71% to 14%, turning retrieval depth from an assumption into a measured choice.

**USI: Unified Source of Information (Personal Knowledge Corpus)**
*Tech stack: Python · YAML · Markdown*
A person-agnostic single-source-of-truth corpus holding identity, skills, projects, and experience as tagged Markdown blocks, ending the drift of maintaining the same facts across a CV, a portfolio site, and an assistant's context. Schema-level audience gating keeps each export to what is appropriate. Powers CV automation, the portfolio site, and the USI-RAG chatbot.

**SIEM Implementation: Security Monitoring & Detection**
*Tech stack: Wazuh · Elasticsearch · Logstash · Kibana · HIDS · FIM*
Designed and deployed a working SIEM centralizing log collection, with detection rules, alerting, file integrity monitoring, and host-based intrusion detection, validated against simulated attacks.

**Cybersecurity Assessment & Footprinting (Client Project)**
*Tech stack: OSINT · Offensive security · Vulnerability assessment*
External attack-surface mapping for a small cooperative; delivered a prioritized vulnerability and remediation report and presented it to the client.

**Digital Twin & Animal Tracking App**
*Tech stack: Kotlin · React Native · Firebase · A-Frame*
A mobile system keeping a live digital twin of tracked animals across large-scale environments, with two-way communication and an AR layer mapping positions in real space.

**1:1 Architectural VR Walkthrough (Client Project)**
*Tech stack: Unity · 3D modelling · Desktop + headset*
Accurate 1:1-scale 3D building models navigable on desktop and in VR, used by clients to plan interior decoration in a spatially accurate representation of their space.

**Mobile Client-Management App (Cooperative)**
*Tech stack: React Native · Firebase*
A mobile app letting a cooperative access and manage client information on the go, delivered end to end.

**Sign Language Recognition: Image-to-Text (Academic)**
*Tech stack: Python · Computer vision · ML*
A computer-vision system reading sign-language gestures from images and converting them to text at 98% classification accuracy.

**CNN Match Classification: League of Legends (Academic)**
*Tech stack: Python · CNNs · Transfer Learning · Optuna*
A multiclass-multilabel CNN over spatial heatmap images predicting match outcome, player role, and duration; compared single-input, per-output, Transfer Learning, and Optuna-optimized architectures.

**Further Academic ML & Computing**
*Tech stack: Python · YOLO · RNNs · MATLAB · SPSS*
YOLO multi-class object detection at scale; RNN sequence prediction; MATLAB physics and mathematics simulations; SPSS statistical analysis across research cases.

**Game Design & Development and Maker Practice**
*Tech stack: Unity · Godot · Blender · VRChat SDK · FDM printing*
Independent multi-engine game development with published content, plus an ongoing home 3D modelling and printing practice for rapid prototyping.

---

## Other Relevant Experience

- International exposure: travel across 20+ countries (Africa, America, Asia, Europe), training courses in Finland, Poland, and Portugal, and six months living in Poland (Erasmus+).
- Founded a student-run radio station using governmental funds for school-improvement, sourced, and set up the equipment.
- 18+ years of Scouting across national and international activities, including World Scout Jamboree participation.
- Recurring Banco Alimentar food-bank volunteer (2018–2025); further volunteer work across forest conservation and animal welfare; community ambassador roles (Unlimited Future, Quinta da Carvalheira, Erasmus Student Network).
- Personal maker practice: home-based 3D modelling and printing for rapid prototyping and iterative problem-solving.
- Writing: two personal blogs on personal growth/psychology and creative writing.
- Personal interest in financial markets and portfolio management: equities and options trading, margin accounts, and risk/position sizing via a live brokerage account (surface only for finance-adjacent roles).

---

## References

Formal recommendation letter from the CTO of Glartek, available on request; additional references on request.
