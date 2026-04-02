# 📖 AI Terms & Myths

**A practitioner's reference for AI/ML terminology and the misconceptions that won't die.**

![Markdown](https://img.shields.io/badge/format-Markdown-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange)

---

## The Problem

AI/ML conversations are drowning in vague terminology and confident misconceptions. Engineers hear "just fine-tune it" without understanding what that means mechanically. Decision-makers assume more parameters equals smarter. Teams ship RAG systems without knowing what hallucination actually is.

The result: bad architectural decisions, wasted compute, and products built on assumptions that sound right but aren't.

---

## What It Does

Two reference documents, maintained by practitioners, designed to be read when you need a precise answer — not a tutorial, not a textbook, not a blog post.

| Document | What's Inside | Scale |
|----------|--------------|-------|
| [ai-terms-glossary.md](ai-terms-glossary.md) | 80+ AI/ML terms defined with precision and practical context | A–Z, alphabetized |
| [ai-myths-busted.md](ai-myths-busted.md) | 20+ common misconceptions debunked with evidence and consequences | Each tied to real decisions |

Every entry follows a strict format. Glossary terms are self-contained 3–6 sentence definitions. Myths include a **Reality** section with named papers, models, or techniques — and a **Why it matters** section that connects to decisions you actually make.

---

## Demo

**Glossary entry:**

```text
### Retrieval-Augmented Generation (RAG)
A technique where an LLM is given relevant documents retrieved from an external
knowledge base before generating a response. The model does not "know" the
retrieved information — it uses it as in-context evidence for that specific query.
RAG reduces hallucination by grounding generation in source material, but does
not eliminate it.
```

**Myth entry:**

```text
## "More parameters means a smarter model"

Reality: A smaller model trained on high-quality data with good techniques can
significantly outperform a much larger model trained on poor data. The Chinchilla
paper demonstrated that most large models were over-parameterized relative to
their training data. Microsoft's Phi-2 (2.7B parameters) outperformed models
many times its size on several benchmarks simply due to better data curation.

Why it matters: Default to the model that fits your task, latency, and cost
requirements — not the largest one available.
```

---

## Built On

- **Markdown** — plain text, no build step, readable anywhere, diffs cleanly in PRs
- **GitHub Issues + Templates** — structured contribution workflow with pre-flight checklists
- **Community review** — every entry is validated for accuracy, tone, and practical relevance before merge

---

## Quickstart

```bash
git clone https://github.com/amitgambhir/ai-terms-and-myths
cd ai-terms-and-myths
```

Open `ai-terms-glossary.md` or `ai-myths-busted.md` in any markdown viewer. That's it.

---

## Contributing

Every contribution goes through an issue-first workflow:

1. Open an issue using the templates in `.github/ISSUE_TEMPLATE/`
   - Glossary terms: prefix with `[GLOSSARY] Suggest: [Term Name]`
   - Myths: prefix with `[MYTH] Debunk: "[Misconception]"`
2. Wait for feedback before writing a PR
3. Match the tone and density of neighboring entries
4. Run through the precision checklist in [CONTRIBUTE.md](CONTRIBUTE.md)

### What gets in

- Terms that appear in research papers, framework docs, or serious industry discussion
- Myths that are widely believed and change real decisions when wrong
- Entries where every claim holds up under scrutiny

### What doesn't

- Marketing jargon, straw men, or trivial facts
- Entries that duplicate existing content
- Anything that ages poorly (transient news, market claims)

---

## Why This Is Different

- **No filler** — banned words include "leverage", "unlock", "seamlessly", "robust", and "empower"
- **Practitioner-first** — every entry is written for people building systems, not writing papers
- **Evidence-backed** — myths cite specific papers, models, and techniques by name — no "some research shows"

---

*Built for the people who need to know what the words actually mean before they ship.*
