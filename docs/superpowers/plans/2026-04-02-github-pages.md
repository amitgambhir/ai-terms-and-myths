# GitHub Pages Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish ai-terms-and-myths as a GitHub Pages site using MkDocs Material with auto-deploy on push.

**Architecture:** MkDocs Material serves the existing markdown files via symlinks in a `docs/` folder. A GitHub Actions workflow builds and deploys on every push to `main`. No content duplication — root-level files remain the source of truth.

**Tech Stack:** MkDocs, mkdocs-material, GitHub Actions, GitHub Pages

---

### Task 1: Create requirements.txt

**Files:**
- Create: `requirements.txt`

- [ ] **Step 1: Create the file**

```text
mkdocs-material==9.6.12
```

- [ ] **Step 2: Commit**

```bash
git add requirements.txt
git commit -m "chore: add requirements.txt for mkdocs-material"
```

---

### Task 2: Create mkdocs.yml

**Files:**
- Create: `mkdocs.yml`

- [ ] **Step 1: Create the MkDocs configuration**

```yaml
site_name: AI Terms & Myths
site_description: A practitioner's reference for AI/ML terminology and the misconceptions that won't die.
site_url: https://amitgambhir.github.io/ai-terms-and-myths/
repo_url: https://github.com/amitgambhir/ai-terms-and-myths
repo_name: amitgambhir/ai-terms-and-myths

theme:
  name: material
  palette:
    - scheme: default
      primary: indigo
      accent: indigo
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode
    - scheme: slate
      primary: indigo
      accent: indigo
      toggle:
        icon: material/brightness-4
        name: Switch to light mode
  features:
    - navigation.instant
    - navigation.tabs
    - navigation.top
    - search.highlight
    - search.suggest
    - toc.follow

plugins:
  - search

nav:
  - Home: index.md
  - Glossary: glossary.md
  - Myths Busted: myths.md
  - Contributing: contributing.md

markdown_extensions:
  - toc:
      permalink: true
  - tables
```

- [ ] **Step 2: Commit**

```bash
git add mkdocs.yml
git commit -m "chore: add mkdocs.yml with Material theme config"
```

---

### Task 3: Create docs/ directory with symlinks and landing page

**Files:**
- Create: `docs/index.md`
- Create: `docs/glossary.md` (symlink to `../ai-terms-glossary.md`)
- Create: `docs/myths.md` (symlink to `../ai-myths-busted.md`)
- Create: `docs/contributing.md` (symlink to `../CONTRIBUTE.md`)

- [ ] **Step 1: Create symlinks**

```bash
cd docs
ln -s ../ai-terms-glossary.md glossary.md
ln -s ../ai-myths-busted.md myths.md
ln -s ../CONTRIBUTE.md contributing.md
cd ..
```

- [ ] **Step 2: Create docs/index.md**

Adapted from README.md for the site landing page. Removes badges and GitHub-specific sections, adds links to site pages instead of raw files.

```markdown
# AI Terms & Myths

**A practitioner's reference for AI/ML terminology and the misconceptions that won't die.**

---

## What This Is

Two reference documents for engineers, product managers, and technical leaders navigating the AI landscape:

| Document | What's Inside |
|----------|--------------|
| [Glossary](glossary.md) | 80+ AI/ML terms defined with precision and practical context |
| [Myths Busted](myths.md) | 20+ common misconceptions debunked with evidence and consequences |

Every entry follows a strict format. Glossary terms are self-contained 3–6 sentence definitions. Myths include a **Reality** section with named papers, models, or techniques — and a **Why it matters** section that connects to decisions you actually make.

---

## How to Use

Browse the [Glossary](glossary.md) or [Myths Busted](myths.md) directly, or use the **search bar** at the top to find any term or misconception instantly.

---

## Contributing

This is an open reference. Contributions go through an issue-first workflow — see the [Contributing](contributing.md) guide for criteria and process.

---

## Why This Is Different

- **No filler** — banned words include "leverage", "unlock", "seamlessly", "robust", and "empower"
- **Practitioner-first** — every entry is written for people building systems, not writing papers
- **Evidence-backed** — myths cite specific papers, models, and techniques by name

---

*Built for the people who need to know what the words actually mean before they ship.*
```

- [ ] **Step 3: Verify symlinks resolve correctly**

Run: `ls -la docs/`

Expected: `glossary.md -> ../ai-terms-glossary.md`, `myths.md -> ../ai-myths-busted.md`, `contributing.md -> ../CONTRIBUTE.md`

- [ ] **Step 4: Commit**

```bash
git add docs/
git commit -m "feat: add docs/ with landing page and symlinks to content files"
```

---

### Task 4: Create GitHub Actions deploy workflow

**Files:**
- Create: `.github/workflows/deploy-pages.yml`

- [ ] **Step 1: Create the workflow file**

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.12'

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Deploy to GitHub Pages
        run: mkdocs gh-deploy --force
```

- [ ] **Step 2: Commit**

```bash
git add .github/workflows/deploy-pages.yml
git commit -m "ci: add GitHub Actions workflow for auto-deploy to Pages"
```

---

### Task 5: Add site/ to .gitignore

**Files:**
- Modify: `.gitignore`

- [ ] **Step 1: Append MkDocs build output to .gitignore**

Add the following to the end of `.gitignore`:

```text
# MkDocs
site/
```

- [ ] **Step 2: Commit**

```bash
git add .gitignore
git commit -m "chore: add site/ to .gitignore"
```

---

### Task 6: Test locally

- [ ] **Step 1: Install mkdocs-material locally**

Run: `pip install mkdocs-material`

- [ ] **Step 2: Serve the site locally**

Run: `mkdocs serve`

Expected: Site available at `http://127.0.0.1:8000/`. Verify:
- Home page renders with landing content
- Glossary page shows all terms with working TOC sidebar
- Myths page shows all myths with working TOC sidebar
- Contributing page renders correctly
- Search bar finds terms (try "RAG", "hallucination")
- Dark/light mode toggle works
- Navigation tabs show: Home | Glossary | Myths Busted | Contributing

- [ ] **Step 3: Stop the server (Ctrl+C)**

---

### Task 7: Update CLAUDE.md

**Files:**
- Modify: `CLAUDE.md`

- [ ] **Step 1: Update Project Overview**

In the Project Overview section, after "No code, no build system, no tests. All contributions are markdown prose.", change to:

```
Published as a GitHub Pages site via MkDocs Material. Content files at the repo root are the source of truth — `docs/` contains symlinks to them.
```

- [ ] **Step 2: Add GitHub Pages section before Key Files**

Add the following section before the "Key Files" section:

```markdown
## GitHub Pages Site

The site is built with MkDocs Material and auto-deploys on push to `main` via GitHub Actions.

**Local development:**

```bash
pip install -r requirements.txt
mkdocs serve                    # http://127.0.0.1:8000/
```

**Content strategy:** Files at the repo root (`ai-terms-glossary.md`, `ai-myths-busted.md`, `CONTRIBUTE.md`) are the source of truth. The `docs/` folder contains symlinks to these files — never edit the symlinks directly. `docs/index.md` is the only non-symlink in `docs/` (landing page with different content from README).

**Deploy:** Automatic on push to `main`. The workflow in `.github/workflows/deploy-pages.yml` runs `mkdocs gh-deploy --force` which builds and pushes to the `gh-pages` branch.
```

- [ ] **Step 3: Update Key Files table**

Add these rows to the Key Files table:

```markdown
| `mkdocs.yml` | MkDocs site configuration (nav, theme, plugins) |
| `docs/` | Site source — symlinks to root content files + `index.md` landing page |
| `requirements.txt` | Pins mkdocs-material version for CI |
| `.github/workflows/deploy-pages.yml` | GitHub Actions auto-deploy workflow |
```

- [ ] **Step 4: Commit**

```bash
git add CLAUDE.md
git commit -m "docs: add GitHub Pages section to CLAUDE.md"
```

---

### Task 8: Update .github/copilot-instructions.md

**Files:**
- Modify: `.github/copilot-instructions.md`

- [ ] **Step 1: Add GitHub Pages note to the Scope & Scale section**

After the line "**No interactive tools or code examples** in these documents. This is prose reference material.", add:

```markdown

### GitHub Pages Site

The project is published as a GitHub Pages site using MkDocs Material. The `docs/` folder contains symlinks to the root-level content files — **never edit the symlinks directly**. Always edit the source files at the repo root (`ai-terms-glossary.md`, `ai-myths-busted.md`, `CONTRIBUTE.md`). The site auto-deploys on push to `main`.
```

- [ ] **Step 2: Commit**

```bash
git add .github/copilot-instructions.md
git commit -m "docs: add GitHub Pages note to copilot-instructions.md"
```

---

### Task 9: Update README.md

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Add Live Site link after badges**

After the badges block and before the `---` separator, add:

```markdown

**[Browse the site](https://amitgambhir.github.io/ai-terms-and-myths/)** — searchable, with dark mode
```

- [ ] **Step 2: Update Built On section**

Add this line to the Built On list:

```markdown
- **MkDocs Material** — documentation site with built-in search, dark/light toggle, auto-deployed via GitHub Actions
```

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "docs: add live site link and MkDocs to README"
```

---

### Task 10: Final verification

- [ ] **Step 1: Run mkdocs build to verify no errors**

Run: `mkdocs build --strict`

Expected: Build completes with no warnings or errors. `site/` directory is created.

- [ ] **Step 2: Clean up build output**

Run: `rm -rf site/`

- [ ] **Step 3: Verify git status is clean**

Run: `git status`

Expected: Nothing to commit, working tree clean.
