# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A prose-only reference containing two documents for AI/ML practitioners:

- **`ai-terms-glossary.md`** — 100+ alphabetized AI/ML term definitions
- **`ai-myths-busted.md`** — Common AI misconceptions debunked with evidence

Published as a GitHub Pages site via MkDocs Material. Content files at the repo root are the source of truth — `docs/` contains symlinks to them.

**Audience:** Engineers, product managers, and technical leaders building or evaluating AI systems.

## Content Structure

### Glossary entries

```markdown
### Term Name
[1-3 sentence definition]

[1-2 sentences context/nuance]

[Optional: usage note or relationship to other terms]
```

- Alphabetized by first letter (ignore leading articles)
- 3-6 sentences per term
- Self-contained definitions — no requirement to read adjacent entries
- Related terms: mention the relationship but don't require readers to jump around
- Tone reference: read "Adam (Optimizer)", "Attention", or "Autoregressive" to calibrate voice and density

### Myth entries

```markdown
## "Quote the myth as people state it"

**Reality:** [What is actually happening. 2-4 sentences with specifics.]

**Why it matters:** [1-2 sentences on practical consequence.]
```

- Total length ~250 words max
- "Why it matters" is non-negotiable — every myth must connect to real decisions
- Reality section: start with the mechanism, not the misconception
- Tone reference: read "More parameters means a smarter model" or "Fine-tuning teaches the model new facts" to calibrate

## Writing Standards

**Tone:** Precise, practitioner-first, no filler. Write for people building systems.

**Key principles:**

- **Reality first** — start with what is actually happening, not what sounds intuitive
- **Why it matters** — every claim includes the practical consequence
- **Depth without tangents** — enough for a practitioner to decide, no rabbit-holing into adjacent concepts
- **Confidence in uncertainty** — when something is unsolved research, say so explicitly

**Banned words:** "leverage", "unlock", "seamlessly", "robust", "empower", "basically"

**Sentences:** Under 30 words on average.

**Citations:** Name specific papers (Chinchilla), models (Phi-2), or techniques (gradient analysis). Never write "some research shows" — either name the source or hedge with "Research suggests..."

**Acronyms:** Expand on first use.

### Common Corrections

| Avoid | Instead |
| ------- | --------- |
| "Basically X is a technique that..." | "X is [specific definition]. [Why it matters]." |
| "Some research shows..." | Name the paper or hedge with "Research suggests..." |
| "It's important that..." (without why) | "This matters because [concrete consequence]." |
| Sentences > 30 words | Shorten. Complexity buries practitioners. |
| Orphaned acronyms | Expand on first use. Expand again in separate sections. |

## Scope

- **Glossary**: 100-150 terms total. Only add terms practitioners actually ask about.
- **Myths**: 10-15 core myths. Each earns its place through frequency and impact.
- **No code examples** in these documents. This is prose reference material.

## When to Stop

Do not proceed if:

- You are unsure whether a claim is accurate
- A myth or glossary entry duplicates or overlaps significantly with existing content
- The reality or consequence of a myth is genuinely unclear
- A term or myth seems marginal — it may not meet the inclusion criteria

## Contribution Workflow

1. Open an issue using templates in `.github/ISSUE_TEMPLATE/` (prefix: `[GLOSSARY]` or `[MYTH]`)
2. Wait for feedback before writing PR
3. Match tone/density of neighboring entries in the same document
4. Run through the precision checklist in `CONTRIBUTE.md` before submitting

## GitHub Pages Site

The site is built with MkDocs Material and auto-deploys on push to `main` via GitHub Actions.

**Local development:**

```bash
pip install -r requirements.txt
mkdocs serve                    # http://127.0.0.1:8000/
```

**Content strategy:** Files at the repo root (`ai-terms-glossary.md`, `ai-myths-busted.md`, `CONTRIBUTE.md`) are the source of truth. The `docs/` folder contains symlinks to these files — never edit the symlinks directly. `docs/index.md` is the only non-symlink in `docs/` (landing page with different content from README).

**Deploy:** Automatic on push to `main`. The workflow in `.github/workflows/deploy-pages.yml` runs `mkdocs gh-deploy --force` which builds and pushes to the `gh-pages` branch.

## Key Files

| File | Purpose |
|------|---------|
| `ai-terms-glossary.md` | The glossary |
| `ai-myths-busted.md` | The myths document |
| `CONTRIBUTE.md` | Contribution guide with criteria and precision checklist |
| `.github/copilot-instructions.md` | Detailed workspace instructions (tone, structure, common corrections) |
| `.github/skills/ai-glossary-and-myths/SKILL.md` | Copilot skill definitions for `/add-glossary-entry` and `/debunk-myth` |
| `mkdocs.yml` | MkDocs site configuration (nav, theme, plugins) |
| `docs/` | Site source — symlinks to root content files + `index.md` landing page |
| `requirements.txt` | Pins mkdocs-material version for CI |
| `.github/workflows/deploy-pages.yml` | GitHub Actions auto-deploy workflow |
