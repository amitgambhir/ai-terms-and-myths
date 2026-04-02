# Contributing to AI Terms & Myths

We welcome contributions from practitioners who encounter terminology gaps or persistent misconceptions in the AI/ML space.

---

## Before You Start

Read the existing entries in both documents to understand:

- **Tone**: Direct, no filler. We say "X is" not "X basically is." No jargon inflation like "leverage" or "empower."
- **Depth**: Enough detail for practitioners to make real decisions. No academic tangents.
- **Why it matters**: Every claim should include the practical consequence. Why does this distinction change how you build or operate?

---

## Adding a Glossary Term

### Criteria

Add a term only if:
- It appears in research papers, ML framework documentation, or serious industry discussions
- A practitioner would encounter it and need to understand its exact meaning
- It fills a gap (e.g., if we cover Attention but not Self-Attention, add Self-Attention)

Do **not** add:
- Marketing jargon (e.g., "AI-powered")
- Acronyms that are just expansions (unless the acronym itself is the term)
- Deprecated techniques unless they help explain modern variants

### Process

1. **Open an issue** titled `[GLOSSARY] Suggest: [Term Name]` with your proposed definition and rationale
2. **Include**:
   - The term name (exactly as you'd capitalize it)
   - A 3–6 sentence definition
   - Why a practitioner needs to know this
   - Any citations (papers, frameworks, tools where you've encountered it)
3. **Wait for feedback** — we'll discuss consistency and fit before you write the PR
4. **Submit a PR** once approved, formatted as:

```markdown
### Term Name
[1–3 sentence definition]

[1–2 sentences of context or nuance]

[If applicable: usage note or relationship to other terms]
```

Place it alphabetically (ignoring leading articles). Verify it doesn't duplicate existing terms.

---

## Debunking a Myth

### Criteria

Add a myth only if:
- It is **widely believed** by a meaningful segment of practitioners or decision-makers
- Getting it **wrong changes real decisions** (model choice, architecture, hiring, scope)
- The **reality is counterintuitive** or distinct enough to warrant explanation
- It is **not already in the document**

Do **not** add:
- Straw men or fringe beliefs
- Trivial facts masquerading as misconceptions
- Myths about transient events or market claims (they age poorly)

### Process

1. **Open an issue** titled `[MYTH] Debunk: "[Common misconception]"` with your proposed reality and impact
2. **Include**:
   - The myth as practitioners actually state it (quote or paraphrase)
   - What is actually happening (specific mechanisms, not hand-waving)
   - Why getting this wrong matters (concrete consequences)
   - Any citations (papers, models, techniques that demonstrate the reality)
3. **Wait for feedback** — we'll validate frequency, accuracy, and fit
4. **Submit a PR** once approved, formatted as:

```markdown
## "Quote the myth as people state it"

**Reality:** [What is actually happening, with specifics. 2–4 sentences.]

**Why it matters:** [1–2 sentences on the practical consequence.]
```

Keep the total under ~250 words. Brevity forces clarity.

---

## Precision Checklist

Before submitting your PR:

- [ ] I've read nearby entries and matched their tone and density
- [ ] Every claim holds up under scrutiny — no hand-waving
- [ ] I've cited papers or models where referenced (or hedged with "Research suggests...")
- [ ] Sentences are under 30 words on average
- [ ] All acronyms are expanded on first use
- [ ] I've checked for duplicates or near-duplicates in the existing content
- [ ] The entry would help a practitioner make a real decision

---

## Review & Merge

Once submitted:
- We review for accuracy, fit, and tone alignment
- We may suggest edits for precision or brevity
- Merging happens when consensus is reached

---

## Questions?

Open an issue to ask. We're here to keep this reference accurate and useful.
