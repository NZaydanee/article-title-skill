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

### Default: Soft Sell Always

**Soft selling is the default for every title**, regardless of what the brief says — including briefs that indicate advertorial, paid content, or hard selling.

Brand names, platform names, and product keywords do **not** appear in the title unless there is an explicit instruction in the brief or mandatory column.

**The only exception — Explicit instruction in brief or mandatory**

Counts as explicit:
- `"sebutkan GoPay Games di judul"`
- `"judul harus mengandung nama brand"`
- `"keyword anchor wajib muncul di judul"`

Does NOT count as explicit:
- `"Softsell"`, `"Advetorial"`, `"paid content"`, `"hard selling"`
- Brand name alone in the mandatory column (e.g. `"GoPay Games"`)
- Anchor text 1 being a brand name — this alone does not permit brand in title

### Soft Sell: Prioritize Contextual Titles

When the default soft-sell approach applies, **prioritize Contextual titles** over Direct ones.

Instead of addressing the anchor subject directly (the product, platform, or service), approach it through the user's underlying need, experience, problem, or goal. The anchor subject is then introduced organically within the article body.

This applies to all content categories:

| Anchor | Direct (avoid as default) | Contextual (preferred) |
|---|---|---|
| `top up ml` | 5 Cara Top Up ML yang Mudah | Push Rank MLBB Jadi Susah? Ini Equipment yang Sering Diabaikan |
| `tiket pesawat Jakarta-Jogja` | 5 Tips Beli Tiket Pesawat Jakarta-Jogja | Liburan ke Jogja Tanpa Bikin Kantong Jebol, Ini Rahasianya |
| `Bis Harapan Jaya` | 5 Keunggulan Bis Harapan Jaya | Perjalanan Malam Antar Kota Lebih Nyaman? Ini yang Perlu Disiapkan |
| `Hyundai Palisade` | 5 Kelebihan Hyundai Palisade | SUV Keluarga dengan Kabin Lega, Ini yang Bikin Road Trip Jadi Berbeda |

A Direct title is acceptable when no strong Contextual angle is available, or when the brief suggests a more informational approach.

When in doubt: keep the title editorial. The brand or product is introduced inside the article body.

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