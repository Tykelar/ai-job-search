# CV-tailoring: hybrid-upgrade trigger note

**Status (2026-07-23): pure A is active. The verbatim-selection hybrid is DEFERRED.**

This note records the decision and the exact changes to make **if and when** we flip from
pure A to the hybrid. It is the in-repo companion to the `cv-tailoring-philosophy` memory.

## The two approaches

- **A — drafter-reviewer (active).** `/apply` regenerates tailored prose per role in LaTeX
  moderncv, then runs a grounding audit + reviewer agent. Flexible; the risk is wording
  drift / fabrication that the audit only partially catches.
- **B — verbatim selection (proven over 44 apps, legacy `build-cv-usi`).** Only the About Me
  is generated; every other line is copied character-for-character from a curated master.
  No drift possible, but rigid.
- **Hybrid (the deferred target).** B's content law on top of A's infrastructure: verbatim
  selection from `cv/master_cv.md` for all bullets/skills/projects/headline, with the
  profile statement as the one generative surface, keeping A's LaTeX output + reviewer +
  ATS/tracker pipeline as a second check.

## Current state (what is already in place)

`cv/master_cv.md` (the curated master, USI-derived, kept in sync by `/sync-usi` Step 2) is
already wired into `/apply` as an **additional grounding + phrasing source** — the drafter is
told to prefer reusing the master's exact bullet wording, and both grounding audits (Step 2
drafter, Step 3 reviewer) cite it. `/apply` still **regenerates** prose; the philosophy is
unchanged. This is the on-ramp: the master exists and is trusted, so flipping to the hybrid
is a workflow change, not a data-migration.

## Trigger — flip to the hybrid when ANY of these shows up in practice

- A tailored CV states a metric, date, title, or fact that the master/profile does not
  support (fabrication), and it happens more than once across applications.
- Bullets get silently reworded in ways that soften or inflate a claim (drift), i.e. the
  grounding audit passes but the *wording* has wandered from the approved master.
- José reports that regenerated CVs "don't sound like the master" or need repeated manual
  correction back toward the master's phrasing.

One-off issues are not the trigger — the signal is a **pattern** across a few applications.

## Changes to make when triggered

1. **`/apply` Step 2 (drafter):** replace "regenerate tailored prose" with **verbatim
   selection**. Every bullet, skill row, project, and headline is copied
   character-for-character from `cv/master_cv.md`; the drafter only **picks and orders**.
   The **profile statement stays generative** (facts from the master only, no em-dashes) —
   that is where role-specific framing lives.
2. **LaTeX becomes pure presentation:** selected master lines are placed into
   `\cventry`/`\cvitem` verbatim — a formatting transform, not a rewrite. Keep the 2-page
   ATS-tuned moderncv output and the compile/inspect/ATS loop unchanged.
3. **`/apply` Step 3 (reviewer):** re-scope from co-author to second check — verify
   (a) profile-statement grounding + voice, (b) **verbatim fidelity** (every non-About-Me
   line traces to an exact line in the master), (c) selection quality (are the
   highest-relevance bullets surfaced for the posting). Its research still feeds the cover
   letter and the profile statement, which remain generative.
4. **Add a verbatim-fidelity item** to `/apply` Step 6 and the CLAUDE.md verification
   checklist: "Every CV line except the profile statement is an exact copy of a line in
   `cv/master_cv.md`."
5. **Keyword matching becomes selection, not insertion:** surface the skill row / bullet
   that already carries the posting's term; never insert a keyword into a bullet. The
   master's broad Skills section is the ATS keyword surface. (For the two primary targets —
   EngEff/DevEx and AI Automation — the master already carries the DORA/cycle-time/
   deployment-frequency and AI-agent/RAG/Claude-Code bullets, so this is well-supported.)

## Do NOT

- Do **not** register the master via `/add-template` — that mechanism is for LaTeX
  skeletons (presentation). The master is content. The moderncv template stays the only
  registered template.
- Do **not** make cover letters verbatim — verbatim selection is a CV-only discipline;
  cover letters stay fully generative.
- Do **not** hand-edit facts into `cv/master_cv.md` — facts flow USI corpus -> `/sync-usi`.

See also: `cv/master_cv.md` header, the `cv-tailoring-philosophy` and
`master-cv-snapshot-provenance` memories.
