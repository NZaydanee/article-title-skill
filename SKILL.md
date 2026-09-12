---
name: article-title
description: Generate specific, high-value article titles from briefs and anchor texts. Use when the user requests article-title generation.
---
# Article Title Skills

## Description

This skill generates article titles from anchor text, briefs, topics, or keywords.

Titles are produced by analyzing the meaningful relationship between the input and a viable article topic — not by copying or paraphrasing the anchor text literally.

---

## How to Load This Pack

Load files in this order:

```
1. SKILL.md          ← this file (always load first)
2. relationships.md  ← always load
3. title-craft.md    ← always load
4. process.md        ← always load
5. examples.md       ← load for batch tasks or when reference examples are needed
6. anti-patterns.md  ← load when output needs additional quality validation
```

For simple tasks (1 title, clear input):
→ Load: SKILL.md + relationships.md + title-craft.md + process.md

For batch tasks (multi-row table):
→ Load: all files

For validating existing titles:
→ Load: process.md + anti-patterns.md

---

## Accepted Input Formats

### Format 1 — Free Text

```
Anchor Text: [value]
Brief: [value]
```

### Format 2 — Markdown Table (Primary Format)

```
| id | anchor text 1 | anchor text 2 | brief | mandatory | title | source |
```

Column handling rules:

| Column | Handling |
|---|---|
| `id` | Read as row identifier for output |
| `anchor text 1` | Primary input — always read |
| `anchor text 2` | Supporting input — read if it adds meaningful information |
| `brief` | Partially read — see rules below |
| `mandatory` | Partially read — see rules below |
| `title` | Output column — filled by this skill |
| `source` | **Always ignored** |

---

## Rules for Reading Brief and Mandatory

Brief and mandatory columns are **not always followed in full**.

Read brief and mandatory only for:
- article topic or category (e.g. "Bisnis & Keuangan", "Lifestyle")
- brand or product context being promoted
- requested angle or perspective (e.g. comparison, soft selling, how-to)
- content constraints that are relevant to the title

Ignore from brief and mandatory:
- article structure instructions (H2, H3, paragraph count)
- instructions about facts or specific content the article must contain
- instructions about writing style within the article

The principle: **brief and mandatory inform the title — they do not instruct the article.**

---

## Output Format

### For free text input

Return the title directly:

```
5 Hal yang Perlu Diketahui Sebelum Membeli Honda Beat
```

### For table input

Return the full table with the `title` column filled:

```markdown
| id | anchor text 1 | anchor text 2 | brief | mandatory | title | source |
|----|---------------|---------------|-------|-----------|-------|--------|
| 1  | ...           | ...           | ...   | ...       | [GENERATED TITLE] | |
```

The `source` column is always left empty in the output.

---

## Output Language

Generate titles in **Bahasa Indonesia** by default.

If anchor text, brief, or mandatory consistently use another language, follow that language.

If input is mixed, prioritize Bahasa Indonesia.

---

## Skill Boundaries

This skill does **not**:
- research facts or verify data
- write the article
- create outlines or content points
- invent statistics or new claims

Generated titles must be supportable by a realistic article. When the required facts are unavailable, use a broad, safe title structure.

---

## Files in This Pack

| File | Contents |
|---|---|
| `SKILL.md` | Entry point, input/output rules, load guide |
| `relationships.md` | 4-type relationship framework + examples + decision rules |
| `title-craft.md` | Title formats, hooks, tone, length, safe framing |
| `process.md` | Step-by-step decision process + final checklist |
| `examples.md` | Example library: single, batch, soft selling, multi-anchor |
| `anti-patterns.md` | Bad title patterns to avoid |
