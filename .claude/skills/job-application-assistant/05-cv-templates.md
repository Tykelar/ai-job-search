---
framework_version: 2.0.0
---

# CV Template and Tailoring Guide (compact style, verbatim-first selection)

## The model: select and order; reword bullets only within bounds

CVs are built by **verbatim-first selection** from a curated master — the content law proven
over 44 legacy applications (`build-cv-usi`), running on the LaTeX pipeline, with a
bounded-rephrasing allowance for experience bullets (added 2026-07-23):

- **Master CV (LaTeX):** `applications/main_example.tex` — the FULL curated content bank
  rendered in the compact style. It is simultaneously the LaTeX skeleton and the verbatim
  content source. It compiles to ~4 pages by design; only tailored CVs have the 2-page rule.
- **Master content bank (Markdown):** `applications/master_cv.md` — the same content,
  USI-derived, kept in sync by `/sync-usi`. The `.tex` master must always match it line for
  line; if they diverge, the Markdown bank (and behind it the USI corpus) wins.
- A tailored CV is `main_example.tex` **copied, then reduced**: keep the blocks relevant to
  the role, delete the rest, reorder within sections. Skill rows, projects, education
  lines, and work headers stay **character-for-character identical** to the master.
- **Experience bullets are verbatim-first**: keep the master's wording unless a light
  rephrase genuinely improves role fit (tightening, aligning to the posting's
  terminology). A rephrased bullet must trace to one specific master bullet and keep its
  facts, metrics, and scope exact — no new claims, no escalated numbers, no merged
  achievements. Verbatim remains the default when rephrasing adds nothing.
- Structurally wrong wording is a master problem: fix it in the USI corpus, re-run
  `/sync-usi`, regenerate — never patch the tailored copy.
- The only fully generative surface: the **About Me paragraph**. The CV header carries no
  headline — name + fixed contact line only.

**Output file:** `applications/<company>_<role>/CV_JoseHenriques_<company>_<role>.tex`

## Template: compact single-column (Carlito)

The visual style is ported from the legacy hyper-optimized builder: Carlito (Calibri-metric)
body, 20pt blue name, ALL-CAPS blue section headings with a thin full-width rule, one-line
work/education headers, dense bullets. Single column — ATS-safe by construction, and the
contact line prints the email as literal text.

Semantic commands (defined in the master's preamble — a tailored CV never needs new ones):

```latex
\cvjob{Job Title, Company}{Sep 2025 – Jun 2026}   % one-line bold work header (has built-in \needspace)
\cvcontext{One-line italic context under a work header.}
\cvedu{Degree}{Institution}{Sep 2024 – Jul 2026}  % one bold education line
\cvedusub{Thesis: Title (18/20)}                  % italic thesis/final-project line under a \cvedu
\cvskill{Category}{item · item · item}            % one skills row
\cvproject{Title}{Description paragraph.}         % project entry
\cvrule                                           % bare separator rule (used above About Me, which has no heading)
```

**Compile with lualatex** (fontspec + system Carlito font; pdflatex cannot load it). Run
from `applications/` with `-output-directory` into the application folder:

```bash
cd applications && lualatex -interaction=nonstopmode -output-directory=<company>_<role> <company>_<role>/CV_JoseHenriques_<company>_<role>.tex
```

Expected output: `Output written on ... (2 pages, ...)`. Any other page count is a failure.

## Fixed 2-page structure

The master carries a `\newpage` before Skills. Tailored CVs keep it, making the page break
deterministic:

- **Page 1:** Header (name + bold contact line, no headline) · About Me (separator rule,
  no heading) · Education · Work Experience · Languages
- **Page 2:** Skills · Projects · Other Relevant Experience · References

Selection budgets (tune to fill both pages, never overfull):

| Section | Tailored budget |
|---|---|
| Glartek bullets | 5-6, ordered for the role |
| Florescer bullets | 3-4 |
| Airking / IMPACT bullets | 2-3 each |
| Education | MSc + BSc with their `\cvedusub` thesis/final-project lines (Thesis 18/20; Final Project 17/20); Electrotechnical line OFF by default (only if the JD explicitly requires electrotechnical knowledge) |
| Skills rows | 6-9, role-relevant first; always keep the tool-name rows (Programming Languages, Tools & Platforms) for ATS |
| Projects | 3-5, thesis entry first by default (the Projects entries carry the full descriptions; the Education sub-lines carry title + grade) |
| Other Relevant Experience | 2-4 bullets |
| References | single fixed line, always last |

**Structural rules (from the legacy workflow):** fixed contact line; no headline; Education
is one bold line per degree plus its italic thesis/final-project sub-line; always include a
Projects section; no "Internship" qualifier on the Glartek title; the en-dash `–` only
inside date ranges; **no em-dashes anywhere**; References never prints referee names or
contact details — only the fixed available-on-request line.

## About Me (the only generative content)

Write it fresh for the role, anchored in the master's paragraph as the voice/quality
baseline (adapt, don't invent a new story):

- Facts from the master/profile only; José's voice (direct, technical, grounded); no
  em-dashes; no keyword stuffing.
- One short paragraph, 2-3 sentences plus the mandatory closing sentence, kept verbatim:
  `Get to know me better \href{https://tykelar.github.io}{here}!`
- Lead with the most role-relevant point, then close with the broader profile
  (systems-level breadth) as context.
- Match the role's lead content: Process / Engineering-Effectiveness roles → Glartek
  re-engineering + outcomes; AI Automation → AI agent/integration work (name **Claude
  Code** where agentic tooling is mentioned); QA / CI → Glartek outcomes + process
  (respect the QA-framing suppression rule in CLAUDE.md); VR / AR → BSc final project +
  immersive; Ops / Process → efficiency outcomes + cross-functional work.

## Glartek bullet ordering (default / general)

By default lead with the **AI agent** bullet and the **Lean re-engineering >50%** bullet,
then the 20% / ~30% impact bullets; demote the QA/Playwright/CI implementation bullets to
the bottom (QA-framing suppression). For a role that explicitly leads on one competency
(e.g. a dedicated Test Automation role), reorder so that competency leads — the order
follows the role, but for general or non-QA roles the QA detail never displaces the
impact/AI bullets. Ordering is always a selection operation; any wording change stays
within the bounded-rephrasing rule.

## Keywords: matched by selection first

Surface the master skill row or bullet that already carries the posting's term. A selected
experience bullet may be lightly retermed to the posting's exact vocabulary where
truthfully equivalent (the posting's tool/method name for the master's synonym — never a
claim the master line does not make); skill rows and headings stay verbatim. The master's
broad Skills section is the ATS keyword surface; the About Me and cover letter (generative)
are where the posting's vocabulary can be engaged directly, where truthfully applicable.
If the profile genuinely has a skill but no master line carries it, that is a
master-coverage gap: report it, fix it in the USI corpus, re-run `/sync-usi`.

## Section headings must match the CV's language

Section names (`Education`, `Work Experience`, `Languages`, `Skills`, `Projects`,
`Other Relevant Experience`, `References`) are literal text in the template (About Me has
no printed heading). If the CV
language (see `CV language` in the candidate profile) were ever not English, translate all
of them, not just body prose — check explicitly during verification. (Skill-row and bullet
content is verbatim master content and only changes language if the master does.)

## Compile-and-inspect loop (MANDATORY)

1. Compile (command above); confirm exactly 2 pages.
2. Read the PDF via the Read tool and inspect both pages:
   - Page 1 ends with Languages; page 2 starts with Skills and ends with References.
   - No orphaned `\cvjob` header (built-in `\needspace` normally prevents it).
   - No overfull page (content pushed past the `\newpage` or onto page 3) and no page
     ending awkwardly early.
3. Fix by **selection**: deselect whole lines (least relevant first) from an overfull
   page; restore the highest-relevance omitted line to a sparse page. Never fix layout by
   rewording to shrink, tightening spacing, or changing geometry.
   `\enlargethispage{2-3\baselineskip}` is allowed for a near-miss trailing spill on
   page 2.
4. Selection scoring when cutting: keep lines that (a) hit THIS posting's keywords and
   responsibilities, (b) carry unique claims (the quantified >50% / 20% / 30% bullets
   survive), (c) the cover letter depends on. Cut the lowest-scoring line first, regardless
   of section.

## ATS parseability

After the layout passes, verify the text layer (`pdftotext -layout`; poppler is optional —
if missing, skip the mechanical check with a warning):

- **Contact details as literal text** — the template prints the email address as text (no
  icons); it must survive extraction.
- **No garbled output** — no `(cid:NNN)` or `�` characters (Carlito under lualatex embeds
  a clean Unicode mapping).
- **Reading order** — single-column, so extraction order matches visual order; verify
  section headings appear in sequence.
- **Keyword coverage** — match the posting's required/preferred terms against the
  extraction, in the posting's language. Coverage improves by selection (see above);
  genuine gaps stay visible and are never stuffed.
