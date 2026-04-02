---
name: ai-glossary-and-myths
description: "Use when adding a glossary entry or debunking a myth. Ensures consistency with project tone, structure, and accuracy standards. Supports both `/add-glossary-entry` and `/debunk-myth` workflows."
---

# AI Terms & Myths — Contribution Skills

Focused workflows for adding glossary entries and debunking myths in the AI Terms & Myths project.

## `/add-glossary-entry` — Add a New Glossary Term

Use this when proposing a new AI/ML term for the glossary.

### Pre-Flight Checks

Before starting:
- [ ] The term appears in research papers, ML framework docs, or serious industry discussion
- [ ] A practitioner would encounter it and need to understand its exact meaning
- [ ] It fills a gap (doesn't overlap significantly with existing entries)
- [ ] It's not marketing jargon, an acronym expansion, or a deprecated technique

### Workflow

1. **Propose the term** (in an issue or directly)
   - Term name (exact capitalization)
   - Why practitioners need to know it
   - Where you've encountered it

2. **Let the agent draft**
   - Agent reads nearby existing entries for tone reference
   - Agent drafts a 3–6 sentence entry following the structure
   - Agent checks for duplicates and placement (alphabetical, ignoring articles)

3. **Review the draft**
   - Does it match the tone of similar entries?
   - Is every claim defensible and precise?
   - Does it include practical relevance?
   - Are citations included where appropriate?

4. **Refine and submit**
   - Make final edits for precision
   - Insert into the glossary at the correct alphabetical location
   - Submit as a PR

### Entry Structure

```markdown
### Term Name
[1–3 sentence definition explaining what it is and why it matters]

[1–2 sentences of additional context, nuance, or common misconception]

[If applicable: brief note on usage in practice or relationship to other terms]
```

### Tone Reference

Read entries like "Adam (Optimizer)", "Attention", or "Autoregressive" to match voice and density.

---

## `/debunk-myth` — Debunk an AI Misconception

Use this when proposing a myth about AI/ML that deserves a reality check.

### Pre-Flight Checks

Before starting:
- [ ] The myth is widely believed by practitioners or decision-makers
- [ ] Getting it wrong changes real decisions (model choice, architecture, hiring, scope)
- [ ] The reality is counterintuitive or distinct enough to merit explanation
- [ ] It's not already covered in the myths file

### Workflow

1. **Propose the myth** (in an issue or directly)
   - The myth as practitioners state it (quote or paraphrase)
   - Evidence that it's widespread
   - Your proposed reality and why it matters

2. **Let the agent draft**
   - Agent reads nearby existing myths for tone and specificity
   - Agent drafts the Reality section with concrete examples (papers, models, techniques)
   - Agent drafts the Why It Matters section tied to real decisions

3. **Review the draft**
   - Is the reality grounded in specifics (not hand-waving)?
   - Are citations accurate and relevant?
   - Does "Why It Matters" address concrete consequences?
   - Is the total length ~250 words or less?

4. **Refine and submit**
   - Make final edits for precision and brevity
   - Ensure the myth title reflects how practitioners actually say it
   - Submit as a PR

### Myth Structure

```markdown
## "Quote the myth as people state it"

**Reality:** [What is actually happening, with specifics. 2–4 sentences.]

**Why it matters:** [1–2 sentences on the practical consequence.]
```

### Reality Section Guidelines

- Start with the mechanism, not the misconception
- Include specific examples: name papers (Chinchilla), models (Phi-2), techniques (gradient analysis)
- Avoid "basically" or other filler
- If hedging, do it explicitly: "Research suggests..." not "Some research shows..."

### Tone Reference

Read myths like "More parameters means a smarter model" or "Fine-tuning teaches the model new facts" to match voice and specificity level.

---

## Quality Checklist (Both Workflows)

Before submitting any PR:

- [ ] **Precision**: Every claim holds up under scrutiny. No hedging without explicit language.
- [ ] **Fit**: Tone and density match neighboring entries in the same document.
- [ ] **Practical**: A practitioner could use this to make a real decision.
- [ ] **Citations**: Papers, models, and techniques are named when referenced. No orphaned "research shows..."
- [ ] **Brevity**: Glossary entries 3–6 sentences; myths ~250 words total.
- [ ] **No duplicates**: I've confirmed this doesn't overlap significantly with existing content.
- [ ] **Proofreading**: No typos or grammatical errors.

---

## Common Pitfalls

| Mistake | Fix |
|---------|-----|
| "Basically X is a technique that..." | "X is [specific definition]." |
| "Some research shows..." (no source) | Name the paper or hedge: "Research suggests..." |
| Sentences > 30 words | Break into shorter sentences. |
| Orphaned acronyms | Expand on first use and in context. |
| "It's important that..." (no why) | "This matters because [concrete consequence]." |
| Myth is trivial (not a misconception) | Does it change actual decisions? If no, reconsider. |
| Term overlaps with existing entry | Merge into existing entry or narrow scope. |

---

## When to Skip

**Don't add a glossary term if:**
- It's marketing jargon ("AI-powered", "next-gen")
- It's just an acronym expansion
- It's deprecated unless it helps explain modern variants

**Don't add a myth if:**
- It's a straw man no one actually believes
- It's about transient market news (ages poorly)
- Getting it wrong doesn't change any real decisions
- It's already in the file (even if worded differently)

---

## Resources

- `CONTRIBUTE.md` — Guide for non-Copilot contributors
- `.github/ISSUE_TEMPLATE/glossary-term.md` — Issue template for proposing terms
- `.github/ISSUE_TEMPLATE/myth.md` — Issue template for proposing myths
- `.github/copilot-instructions.md` — Full workspace instructions (detailed guidelines)
