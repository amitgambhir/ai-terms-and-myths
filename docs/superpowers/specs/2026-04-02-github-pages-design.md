# GitHub Pages Site — Design Spec

**Date:** 2026-04-02
**Status:** Approved

---

## Goal

Publish the AI Terms & Myths reference as a GitHub Pages website using MkDocs + Material theme. Auto-deploy on push to `main`. Clean navigation, built-in search, dark/light toggle.

---

## Site Structure

```
mkdocs.yml                          # Site config, nav, theme, search
docs/
  index.md                          # Landing page (adapted from README.md)
  glossary.md -> ../ai-terms-glossary.md   # Symlink
  myths.md -> ../ai-myths-busted.md        # Symlink
  contributing.md -> ../CONTRIBUTE.md      # Symlink
requirements.txt                    # Pins mkdocs-material for CI
.github/
  workflows/
    deploy-pages.yml                # GitHub Actions: build + deploy on push
```

### Content Strategy

- Existing markdown files at repo root remain the source of truth
- `docs/` folder uses symlinks pointing to root-level files — no duplication
- `docs/index.md` is a new file adapted from `README.md` for the landing page (not a symlink — different content needs)

---

## Navigation

Top nav bar with four items:

```
Home | Glossary | Myths Busted | Contributing
```

Each page gets an auto-generated table of contents sidebar from its headings.

---

## Theme Configuration

| Setting | Value |
|---------|-------|
| Theme | `material` |
| Color scheme | Light default with dark mode toggle |
| Font | Default Material (Roboto) |
| Search | Built-in (indexes all content, no plugins needed) |
| TOC sidebar | Enabled per page |
| Footer nav | Previous/Next page links |
| Repository link | Show GitHub repo link in header |

---

## Deploy Pipeline

**Trigger:** Push to `main` branch

**Workflow steps:**
1. Checkout repo
2. Set up Python
3. Install `mkdocs-material` from `requirements.txt`
4. Run `mkdocs gh-deploy --force`

**GitHub repo settings required:**
- Enable Pages
- Set source to `gh-pages` branch (created automatically by `mkdocs gh-deploy`)

---

## New Files

| File | Purpose |
|------|---------|
| `mkdocs.yml` | Site configuration — nav, theme, plugins, metadata |
| `docs/index.md` | Landing page adapted from README (not a symlink) |
| `docs/glossary.md` | Symlink to `../ai-terms-glossary.md` |
| `docs/myths.md` | Symlink to `../ai-myths-busted.md` |
| `docs/contributing.md` | Symlink to `../CONTRIBUTE.md` |
| `requirements.txt` | `mkdocs-material` version pin |
| `.github/workflows/deploy-pages.yml` | Auto-deploy workflow |

---

## Updates to Existing Files

| File | Change |
|------|--------|
| `CLAUDE.md` | Add GitHub Pages section: site commands (`mkdocs serve`, `mkdocs build`), docs/ symlink strategy, deploy pipeline |
| `.github/copilot-instructions.md` | Add note about docs/ symlinks and that content files at root are the source of truth |
| `README.md` | Add "Live Site" section with URL placeholder, update "Built On" with MkDocs Material |
| `.gitignore` | Add `site/` (MkDocs build output) |

---

## What Stays the Same

- `ai-terms-glossary.md` and `ai-myths-busted.md` untouched at repo root
- Contribution workflow unchanged
- Issue templates unaffected
- SKILL.md unaffected

---

## Out of Scope

- Custom CSS or JavaScript
- Analytics or tracking
- Custom domain (can be added later in repo settings)
- Interactive features beyond built-in search
