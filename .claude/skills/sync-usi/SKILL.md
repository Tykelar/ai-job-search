---
name: sync-usi
description: >
  Refreshes the candidate profile from the USI corpus (the Unified Source of
  Information repo). Runs the bridge script to regenerate the source packs in
  documents/usi/, then folds new or changed facts into the candidate profile
  files and CLAUDE.md. Triggers on: /sync-usi, sync usi, refresh profile from
  USI, update profile from corpus
allowed-tools: Read, Write, Edit, Glob, Grep, Bash(python tools/sync_usi.py), Bash(python -c *), AskUserQuestion
---

# Sync Profile from USI

The **USI corpus** (`C:\Users\josep\Desktop\Dev\USI`, overridable via the `USI_HOME`
environment variable) is the single source of truth for everything about the candidate:
identity, skills, experience, education, projects, traits, positioning strategy. This
skill pulls the current state of the corpus into this workspace and updates every file
that carries profile content.

**Direction of flow: USI → this repo, never the reverse.** If the user provides new
facts about themselves during any session, those belong in the USI corpus first (tell
the user to add them there, or offer to edit the USI block directly since the corpus is
an additional working directory), then re-run this skill. Never hand-edit profile facts
into this repo's files without the corpus carrying them — that recreates the stale-copy
problem this skill exists to prevent.

## Step 1 — Regenerate the source packs

Run from the repo root:

```
python tools/sync_usi.py
```

This calls USI's export API (`scripts/build.py`) and writes three packs to
`documents/usi/` (gitignored, machine-generated — never hand-edit):

| Pack | Contents |
|---|---|
| `usi-content.md` | All CV-surfaceable blocks (audience = `cv`), body only |
| `usi-content.json` | Same blocks with frontmatter: itemized skills, tools, stacks, metrics, language levels |
| `usi-strategy.md` | Meta blocks: positioning strategy, impact/bullet bank, keyword banks — includes **private** audience content |

If the script fails because the USI repo is missing, stop and report; do not fall back
to older copies of the profile.

## Step 2 — Fold changes into the profile files

Read the three packs, then compare against and update each of these targets:

1. **`CLAUDE.md` → Candidate Profile section** — the compact always-loaded summary:
   identity, education, experience, skills, certifications, publications, awards,
   behavioral traits, target sectors, deal-breakers. Keep it a *summary*; the detail
   lives in the skill files below.
2. **`.claude/skills/job-application-assistant/01-candidate-profile.md`** — the full
   factual profile: contact details, education table, all experience entries with
   bullets, projects, itemized skills (from `usi-content.json` frontmatter),
   publications, awards, references.
3. **`.claude/skills/job-application-assistant/02-behavioral-profile.md`** — traits,
   working style, environment preferences, growth areas (from `traits/*` blocks and
   the positioning strategy).
4. **`.claude/skills/job-application-assistant/03-writing-style.md`** — only the
   **candidate-specific rules** section (positioning rules, framing suppressions,
   headline rules, voice notes from `usi-strategy.md`). Do not touch the framework's
   generic writing rules above that section.

Update rules:

- **The corpus wins.** Where a pack and a profile file disagree on a fact, the pack is
  correct. Update the file.
- **Audience control.** Content from `usi-strategy.md` marked `private` informs *how*
  to write (positioning, framing) but must never be quoted into CVs, cover letters, or
  any outgoing document. It may live in the skill files (they are local guidance), but
  mark it clearly as internal positioning guidance.
- **Surgical edits.** Change only what the corpus changed; preserve the files'
  structure and any framework boilerplate.
- **Report the diff.** After updating, summarize per file what changed (added /
  updated / removed facts) so the user can spot sync mistakes.

## Step 3 — Verify

- No `[PLACEHOLDER]` tokens remain in any of the four targets.
- Names, dates, titles, and metrics in the profile files match the packs exactly.
- Nothing marked `audience: private` is phrased as CV-ready copy.

## When to run

- After any edit to the USI corpus.
- Before a batch of `/apply` runs, if the corpus may have changed.
- Whenever the user says their profile information is out of date.
