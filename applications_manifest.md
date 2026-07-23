# Applications Manifest

Links each tailored application to its posting and documents, so the URL always
travels with the finished CV/cover letter. Regenerated per `/apply` batch.

- **Posting URLs** are the canonical store in `.claude/skills/job-scraper/job_scraper/seen_jobs.json`.
- Once a role is actually applied to, it also gets a row in `job_search_tracker.csv`
  (with the URL in the `source` column). Until then, it lives here and in `seen_jobs.json`.
- Each CV `.tex` also carries its posting URL in a `%% Source:` header comment
  (a LaTeX comment — it never renders into the PDF).

_Last updated: 2026-07-23 — Strong-Fit shortlist batch (8 applications, not yet submitted)._

| # | Role · Company | Rank | Posting | CV | Cover letter |
|---|---|---|---|---|---|
| 1 | Junior AI Engineer · **Blazity** | 90 Strong | https://justjoin.it/job-offer/blazity-sp-z-o-o--junior-ai-engineer-next-js-llm--warszawa-javascript | `applications/blazity_ai_engineer/CV_JoseHenriques_blazity_ai_engineer.pdf` | `applications/blazity_ai_engineer/CL_JoseHenriques_blazity_ai_engineer.pdf` |
| 2 | AI Engineer 0-to-1 · **Prosus** | 87 Strong | https://nl.linkedin.com/jobs/view/ai-engineer-%E2%80%93-0-to-1-products-at-prosus-4437932485 | `applications/prosus_ai_engineer_0to1/CV_JoseHenriques_prosus_ai_engineer_0to1.pdf` | `applications/prosus_ai_engineer_0to1/CL_JoseHenriques_prosus_ai_engineer_0to1.pdf` |
| 3 | AI Talent Lab Trainee · **Prosus** | 81 Strong | https://nl.linkedin.com/jobs/view/ai-talent-lab-trainee-at-prosus-4442640262 | `applications/prosus_talent_lab_builder/CV_JoseHenriques_prosus_talent_lab_builder.pdf` | `applications/prosus_talent_lab_builder/CL_JoseHenriques_prosus_talent_lab_builder.pdf` |
| 4 | Python AI Engineer · **Data Oriented Defence** | 79 Strong | https://nl.linkedin.com/jobs/view/python-ai-engineer-intern-junior-at-data-oriented-defence-operations-4443771558 | `applications/dodo_python_ai_engineer/CV_JoseHenriques_dodo_python_ai_engineer.pdf` | `applications/dodo_python_ai_engineer/CL_JoseHenriques_dodo_python_ai_engineer.pdf` |
| 5 | Junior AI Engineer · **InnoWave** | 79 Strong | https://pt.linkedin.com/jobs/view/junior-ai-engineer-at-innowave-4440258758 | `applications/innowave_ai_engineer/CV_JoseHenriques_innowave_ai_engineer.pdf` | `applications/innowave_ai_engineer/CL_JoseHenriques_innowave_ai_engineer.pdf` |
| 6 | GenAI Platform & Ops Trainee · **Euronext** | 78 Strong | https://hrhub.wd3.myworkdayjobs.com/Euronext_Career_Page/job/Porto/GenAI-Platform---Operations-Trainee_R28154 | `applications/euronext_genai_trainee/CV_JoseHenriques_euronext_genai_trainee.pdf` | `applications/euronext_genai_trainee/CL_JoseHenriques_euronext_genai_trainee.pdf` |
| 7 | AI Agent Engineer · **Comarch** | 78 Strong | https://pl.linkedin.com/jobs/view/ai-agent-engineer-at-comarch-4440094238 | `applications/comarch_ai_agent_engineer/CV_JoseHenriques_comarch_ai_agent_engineer.pdf` | `applications/comarch_ai_agent_engineer/CL_JoseHenriques_comarch_ai_agent_engineer.pdf` |
| 8 | AI & Automation Engineer · **VFX Financial** | 76 Strong | https://pt.linkedin.com/jobs/view/ai-automation-engineer-at-vfx-financial-4441320412 | `applications/vfx_ai_automation_engineer/CV_JoseHenriques_vfx_ai_automation_engineer.pdf` | `applications/vfx_ai_automation_engineer/CL_JoseHenriques_vfx_ai_automation_engineer.pdf` |
