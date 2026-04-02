---
description: "Workspace instructions for ai-terms-and-myths project. Use when contributing to AI glossary entries or myth debunking content. Ensures consistent tone, structure, and level of precision across edits and new entries."
---

# AI Terms & Myths — Workspace Instructions

## Project

This workspace contains two reference documents for practitioners navigating AI/ML terminology and misconceptions:

- **`ai-terms-glossary.md`** — Precise, jargon-free definitions of 100+ AI/ML terms
- **`ai-myths-busted.md`** — Common misconceptions about AI, with reality checks and practical implications

**Audience:** Engineers, product managers, technical leaders, and anyone building or evaluating AI systems.

**Distribution:** Open for community contributions (GitHub).

---

## Tone & Principles

### Tone

- **Precision over accessibility**: Use technical terms correctly. Avoid "hand-waving."
- **No jargon inflation**: Do not say "leverage," "unlock," "seamlessly," "robust," "empower." Say what you mean.
- **Practitioner-first voice**: Write for people building systems, not academics writing papers.
- **Confidence in uncertainty**: When something is unsolved research, say so explicitly.

### Key Principles

1. **Reality first** — Always start with what is actually happening, not what sounds intuitive.
2. **Why it matters** — Every claim should include the practical consequence: Why does this distinction change how you building or operate systems?
3. **Cite when credible** — If you reference a paper (e.g., Chinchilla, "Attention Is All You Need"), name it. If you're not sure of the source, hedge with phrases like "Research suggests" instead of stating it as established fact.
4. **Depth without tangents** — Explain enough for a practitioner to make informed decisions. Do not rabbit-hole into adjacent concepts unless they affect the decision.

---

## Glossary Entries (`ai-terms-glossary.md`)

### Structure

```markdown
### Term Name
[1–3 sentence definition explaining what the term is and why it matters]

[1–2 sentences of additional context, nuance, or common misconception]

[If applicable: brief note on usage in practice or relationship to other terms]
```

### Guidelines

- **Alphabetized by first letter**, with leading articles ignored (e.g., "A Technique" goes under T).
- **One entry per subsection.** Do not nest subsections.
- **Definition should be self-contained** — a reader should understand the term without reading adjacent entries.
- **Related terms**: If a term builds on another (e.g., Autograd builds on Backpropagation), mention the relationship but don't require readers to jump around.
- **Length**: 3–6 sentences per term. More often signals that the term is too complex or should be split.

### What Constitutes a New Term

Add a new term if:
- It appears in research papers, ML framework documentation, or serious industry discussions.
- A practitioner would encounter it and need to understand its exact meaning.
- It fills a gap (e.g., if we explain Attention but not Self-Attention, add Self-Attention).

Do not add:
- Marketing jargon (e.g., "AI-powered" is not a term to define).
- Acronyms that are just expansions (e.g., BERT is useful because it's the architecture; "BERT stands for Bidirectional Encoder Representations from Transformers" belongs in context, not standalone).
- Deprecated or obsolete techniques unless they help explain modern variants (e.g., LSTMs are worth keeping because they explain why transformers are better).

---

## Myths (`ai-myths-busted.md`)

### Structure

```markdown
## "Quote the myth as people state it"

**Reality:** [What is actually happening, with specifics. 2–4 sentences.]

**Why it matters:** [1–2 sentences on the practical consequence. How does getting this wrong change what you build or how you operate?]
```

### Guidelines

- **Title format**: Quote the myth as practitioners actually state it (not over-intellectualized).
- **Reality section**: Start with the true mechanism. Provide specifics or a concrete example (e.g., cite the Chinchilla paper, reference a specific model like Phi-2, name techniques like gradient analysis).
- **Why it matters**: Connect to real decisions (architecture choices, model selection, system design, hiring, scope). Avoid abstract arguments.
- **Length**: Keep myth + reality + impact to ~250 words. Brevity forces clarity.

### What Constitutes a Myth Worth Debunking

Add a myth if:
- It is **widely believed** by a meaningful segment of practitioners or decision-makers.
- Getting it **wrong changes real decisions** (what model you choose, how you build, what you hire for).
- The **reality is counterintuitive** or distinct enough to warrant explanation.
- It is **not already documented** in the myths file.

Do not add:
- Straw men or fringe beliefs no one actually holds.
- Myths that are trivial (e.g., a simple fact rather than a misconception).
- Myths about news events or transient market claims — these age poorly.

---

## Editing & Contributing

### Before Adding or Updating

- **Tone check**: Read a nearby entry in the same document. Match that voice and density.
- **Precision check**: Does every claim hold up under scrutiny? If you're hedging, make the hedge explicit.
- **Practical check**: Could a practitioner use this to make a real decision? If not, rethink.
- **Links & references**: Keep them minimal (within the markdown file, use headers as anchors if needed; do not over-link). External links are acceptable for papers but should be rare.

### Common Corrections

| Avoid | Instead |
|-------|---------|
| "Basically X is a technique that..." | "X is [specific definition]. [Why it matters]." |
| "Some research shows..." | Name the paper or hedge with "Research suggests..." |
| "It's important that..." [without why] | "This matters because..." [concrete consequence] |
| Sentences > 30 words | Shorten. Complexity buries practitioners. |
| Orphaned acronyms | Expand on first use. Expand again in separate section. |

---

## Scope & Scale

- **Glossary**: Expect 100–150 terms total. Do not add every variant or compound term, only those that practitioners ask for.
- **Myths**: Expect 10–15 core myths, with occasional additions. Be selective; each myth should earn its place through frequency and impact.
- **No interactive tools or code examples** in these documents. This is prose reference material.

---

## Consistency Checks for AI Contributors

When editing or suggesting changes:

1. **Read the existing entry** in the same document (or a neighboring entry).
2. **Match the tone**: Precise, concise, no filler language.
3. **Include "why it matters"**: For myths, this is non-negotiable. For glossary entries, acceptable if implied and clear.
4. **Check references**: If citing a paper or specific model, verify it's real and relevant.
5. **Avoid speculation**: Stick to established facts. If emerging research, hedge explicitly.
6. **Proofread deeply**: Typos erode credibility in reference material.

---

## When to Ask for Clarification

Do not proceed if:
- You are unsure whether a claim is accurate (ask in a comment or PR rather than guessing).
- A myth or glossary entry duplicates or overlaps significantly with existing content.
- The reality or consequence of a myth is genuinely unclear.
- You are adding a term or myth that seems marginal — it may not meet the criteria above.

---

## Resources

- **Active file locations**: `ai-terms-glossary.md`, `ai-myths-busted.md`
- **GitHub issues or PRs**: The source of truth for new contributions. Open issues to propose myths or glossary additions before writing.
