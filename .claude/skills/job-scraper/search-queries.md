# Search Queries for Job Scraper — José Pedro Nolasco Henriques

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first.

- **`linkedin-search`** (country-agnostic) — pass `--location` per target market.
- **`freehire-search`** (country-agnostic, tech-focused) — pass `--country` / `--region` facets; one call can span several countries.
- **Danish portals** (`jobindex-search`, `jobnet-search`, `jobbank-search`, `jobdanmark-search`) — Denmark only. Run these for the Denmark leg of the search. `jobnet`/`jobdanmark` skew Danish-language public-sector; `jobindex` and `jobbank` (Akademikernes Jobbank, highly-educated/graduate) are the most useful for English-speaking tech roles.

The `site:` templates further down are the **WebSearch fallback** — for company career pages or when a CLI fails.

**Language scope:** write every query category in the languages you work in (Portuguese,
English, Spanish). Translate each category's keywords rather than machine-translating
word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend"). Two *separate*
language checks then apply to what comes back — the **Language Filter** below (scrape-time,
on the language a posting is *written* in) and `04-job-evaluation.md`'s **Language Gate**
(on the languages the role *requires*). See the Language Filter section for how they differ.

## Target Profile (drives keywords)

- **Primary roles:** AI Automation / AI Integration Engineer (LLM agents, RAG, chatbots — **Claude Code** by name), Engineering Effectiveness / Developer Productivity / DevEx, Platform / Build engineering, CI/CD & delivery-infrastructure re-engineering.
- **Secondary roles:** Software Engineer (Python/TypeScript), Process & Operations improvement, Data Engineer, Test-automation architecture (Playwright), VR/AR / Digital Twin, Cybersecurity.
- **Seniority:** early-career — MSc (2026) + ~1yr Software Quality Engineer (Glartek) + founder. Target **junior / graduate / trainee / mid** roles first; senior/staff/VP only where the AI-in-production differentiator makes it plausible.

## Geography (open to relocation)

- **Home market:** Portugal (Leiria base — Lisbon ~1.5h, Coimbra ~1h, Aveiro/Ovar ~1.5h, Porto ~2h). Remote-first preferred for non-relocation roles.
- **Relocation-OK countries:** Denmark, Norway, Finland, Poland, Netherlands, Switzerland, Luxembourg.
- **Remote:** any EU-remote role is in scope regardless of country.

### LinkedIn `--location` strings per market
`Portugal` · `Denmark` · `Norway` · `Finland` · `Poland` · `Netherlands` · `Switzerland` · `Luxembourg` · `Remote`
(City-level when useful: `Lisbon, Portugal`, `Copenhagen, Denmark`, `Amsterdam, Netherlands`, `Zurich, Switzerland`, `Warsaw, Poland`.)

### freehire facets per market
`--country PT,DK,NO,FI,PL,NL,CH,LU` (comma = OR). Add `--region eu,none` to sweep remote roles that never resolved a geography. Discover live facet values at `/api/v1/jobs/facets?q=<role>` — never invent them.

## Query Categories

Queries are grouped by priority. Write **each category in every language you work in** (see Language scope above). Combine each query with your location terms where the site supports it.

### Priority 1: AI Automation / AI Integration
```
linkedin  -q "AI Engineer"                 -l <market> --jobage 14
linkedin  -q "AI automation"               -l <market> --jobage 14
linkedin  -q "Machine Learning Engineer"   -l <market> --jobage 14
freehire  -q "AI automation agent"  --category ml_ai --country <codes> --jobage 21
freehire  -q "agentic AI RAG LLM"                    --country <codes> --jobage 21
jobindex  -q "AI engineer"        --jobage 14 --sort date      # Denmark
jobbank   --key "AI"  --work-area 31 --since <date>            # Denmark, IT-Software
```

### Priority 2: Engineering Effectiveness / DevEx / Platform / CI-CD
```
linkedin  -q "Developer Productivity Engineering Effectiveness" -l <market> --jobage 30
linkedin  -q "Platform Engineer"     -l <market> --jobage 14
linkedin  -q "DevOps CI/CD"          -l <market> --jobage 14
freehire  --category devops          --country <codes> --jobage 21
jobindex  -q "platform engineer"     --jobage 14 --sort date   # Denmark
```

### Priority 3: Software Engineer / Data Engineer (Python)
```
linkedin  -q "Python Software Engineer"  -l <market> --jobage 14
linkedin  -q "Data Engineer"             -l <market> --jobage 14
freehire  -q "python"  --seniority junior,middle --country <codes> --jobage 21
```

### Priority 4: Process & Operations / Test Automation (wider net)
```
linkedin  -q "Process Engineer continuous improvement" -l <market> --jobage 30
linkedin  -q "Test Automation Playwright"              -l <market> --jobage 30
freehire  --category qa  --country <codes> --jobage 21
```

## Location Filter

Portugal roles: verify commute from Leiria, or remote/hybrid feasibility. Relocation-OK countries: accept onsite/hybrid (relocation expected). Reject only markets outside the list above (unless fully remote-EU).

## Language Filter

The candidate's languages (source of truth: the `Languages:` line in the candidate profile /
CLAUDE.md Identity section) are **Portuguese (Native, C2), English (C2), Spanish (B1),
French (A1)**.

A posting **written in** a language outside that set is a strong proxy for the job requiring
that language day to day. Filter on the language of the **posting body**, not the employer's
country:

| Posting body language | Action |
|---|---|
| English, Portuguese, Spanish | **Include.** Working proficiency. |
| French | **Include but mark `⚠ FR`.** A1 is not professional working proficiency; the user decides. |
| Danish, Norwegian, Swedish, Finnish, Polish, German, Dutch, or any other language outside the set | **Exclude.** Record in `seen_jobs.json` with `"status": "skipped"` and `"skip_reason": "language"`, and count it in the Step 5 summary. |

Rules that keep this honest:

- **Filter on the posting body, not the employer.** A Danish company posting in English is
  **in scope** - that is the common case for Nordic tech roles and excluding it would gut the
  Denmark leg of the search.
- **A stated English-working-language line overrides the body language.** If a
  Danish-language posting explicitly says the working language is English, include it.
- **Never silently drop.** Excluded postings are counted in the Step 5 output so the user can
  see what the filter cost them, and they stay in `seen_jobs.json` so dedup still works.
- **Mixed-language postings** (Danish intro, English requirements) count as English.

> **Trade-off, recorded 2026-08-10:** this filter is applied at the user's explicit request.
> On the 2026-08-10 run it would have excluded **Bankdata Platform Engineer**, which ranked
> **79/100, the single highest-scoring job of that batch**, plus HOFOR AI Engineer (63) and
> Eurofins AI Automation Specialist (63). The user applied to Bankdata anyway with an English
> cover letter. If good Danish-language matches keep getting dropped, revisit this filter.

### Two separate checks, both applied

The table above is a **scrape-time** screen on the language a posting is *written in* — the
candidate's explicit policy, with its cost recorded in the trade-off note. It is distinct
from `04-job-evaluation.md`'s **Language Gate**, which runs later (at `/scrape` Step 3 and
in `/rank`) and reads the languages a posting requires **for the role**: a required language
not declared at all is a hard FAIL, while a declared language at a stated bar above the
declared level is a FLAG for the user to judge, never a silent exclusion. Upstream's default
is that a posting merely *written* in an undeclared language still passes; this fork
deliberately overrides that with the filter above. Both checks run, and neither is silent.

## Date Filter

Last 14 days by default (30 for the thinner Priority-2/4 categories). If a posting date can't be determined, include and flag "date unknown".

## WebSearch fallback (`site:` templates)

Use only for portals without a CLI or company career pages:
```
site:linkedin.com/jobs "AI Engineer" (Portugal OR Denmark OR Netherlands OR remote)
site:boards.greenhouse.io "AI Engineer" Europe
site:jobs.lever.co "Platform Engineer" Europe
```
