# Decision Process

Run this process internally before generating each title.

---

## Step 1 — Read and Understand All Input

Before doing anything else, read all relevant input columns:

```
anchor text 1  → primary subject
anchor text 2  → supporting information or variant (if available)
brief          → topic context, angle, or promotional goal
mandatory      → constraints or emphasis relevant to the title
```

### Rules for Reading Brief and Mandatory

Take from brief and mandatory:
- topic category (e.g. Bisnis & Keuangan, Otomotif, Travel)
- brand or product context being promoted
- requested angle (e.g. soft selling, comparison, how-to guide)
- constraints that affect the title
- explicit instruction to include a specific brand or keyword in the title

Ignore from brief and mandatory:
- article structure instructions (H2, H3, paragraph count)
- instructions about specific facts or content the article must contain
- article writing style instructions

### Default: Soft Sell

**Soft selling is always the default**, regardless of the brief value — including briefs that indicate advertorial, paid content, or hard selling.

Brand names, platform names, and product keywords do **not** appear in the title unless there is an explicit instruction in brief or mandatory.

**The only exception — Explicit instruction in brief or mandatory**

| Situation | Brand in title? |
|---|---|
| Brief: `"Softsell"` | No |
| Brief: `"Advetorial"` | No |
| Brief: `"paid content"` / `"hard selling"` | No |
| Mandatory: brand name only (e.g. `"GoPay Games"`) | No |
| Anchor text 1 is a brand name | No |
| Brief/mandatory: `"sebutkan [brand] di judul"` | Yes |
| Brief/mandatory: `"judul harus mengandung nama brand"` | Yes |
| Brief/mandatory: `"keyword anchor wajib muncul di judul"` | Yes |

### Soft Sell: Prioritize Contextual Titles

When the soft-sell default applies, **prefer Contextual titles** over Direct ones.

Approach the anchor subject through the user's underlying need, experience, problem, or goal — not the product or service directly. The anchor subject enters the article body organically.

Examples across categories:

```
Anchor: top up ml
Direct (avoid):    5 Cara Top Up Mobile Legends dengan Mudah
Contextual (prefer): Push Rank MLBB Jadi Susah? Ini Equipment yang Sering Diabaikan

Anchor: tiket pesawat Jakarta-Jogja
Direct (avoid):    5 Tips Beli Tiket Pesawat Jakarta-Jogja Murah
Contextual (prefer): Liburan ke Jogja Tanpa Bikin Kantong Jebol, Ini Rahasianya

Anchor: Hyundai Palisade
Direct (avoid):    5 Kelebihan Hyundai Palisade yang Perlu Diketahui
Contextual (prefer): SUV Keluarga dengan Kabin Lega, Ini yang Bikin Road Trip Jadi Berbeda
```

A Direct title is acceptable when no strong Contextual angle is available, or when the brief suggests a more informational approach.

When in doubt: keep the title editorial. The brand or product is introduced inside the article body.

---

## Step 2 — Identify the Subject and Intent

Determine what the anchor text actually represents.

The anchor is not just a string of keywords — it represents:

```
entity       → product, brand, place, person
activity     → how-to, process, guide
problem      → risk, mistake, failure
intent       → purchase decision, comparison, exploration
concept      → investment, inflation, depreciation
```

Example:

```
Anchor: STARGAZER CARTENZ
  ↓
Entity: vehicle (MPV/SUV)
Intent: purchase decision, feature evaluation, financial assessment
```

```
Anchor: Harga baru Stargazer Cartenz
  ↓
Intent: price calculation, value comparison, financial consideration
```

---

## Step 3 — Determine Context from the Brief

After understanding the anchor, read the brief to strengthen context:

```
Brief: Bisnis & Keuangan — Kalkulasi Finansial MPV Baru
  ↓
Context:  financial angle, not just product features
Tone:     serious, analytical
Angle:    asset depreciation, feature-to-price ratio, ownership cost
```

---

## Step 4 — Generate Relationship Candidates

Evaluate all applicable relationship types:

```
Direct        → does a title about the anchor itself work naturally?
Contextual    → is there a related topic that serves the brief better?
Negative      → does a risk or problem angle produce a stronger title?
Causal        → does a cause-effect mechanism produce a stronger title?
Combination   → can two or more relationship types be combined?
```

Generate at least two candidates before selecting.

---

## Step 5 — Select the Strongest Relationship

Choose the relationship that:

1. Is semantically strongest
2. Produces the most natural article topic
3. Fits the brief and identified tone
4. Supports the commercial objective if one exists (soft selling, brand mention)
5. Can realistically become a complete article
6. Does not require fabricated facts

---

## Step 6 — Select a Title Format

Determine the most appropriate format:

```
Topic supports a list?       → Numbered format (5 / 7 / 8 / 10)
Topic is a guide?            → "Panduan ..."
Topic is a question?         → "Mengapa ..." / "Bagaimana ..."
Topic is a comparison?       → "[A] vs [B]: ..."
Topic is a process?          → "Cara ..." / "Langkah ..."
```

---

## Step 7 — Add a Hook (If Relevant)

Evaluate whether a hook strengthens the title:

```
Action hook        → if the article is actionable
Practical hook     → if the topic relates to efficiency or savings
Curiosity hook     → if the topic contains non-obvious information
Lifestyle hook     → if the topic is travel, personal experience, or lifestyle
```

Do not add a hook if:
- it makes the title sound exaggerated
- it introduces a claim the article cannot support
- the title is already strong without it

---

## Step 8 — Verify Supportability

Ask:

> "Can a writer produce a complete article from this title without fabricating facts?"

If yes → proceed.

If no → return to Step 6 and select a broader, safer structure.

Example:

```
Unsafe (requires specific unverified data):
"Stargazer Cartenz Terbukti Paling Irit di Kelasnya"

Safer (no specific claim required):
"5 Pertimbangan Finansial Sebelum Membeli MPV di Kelas Menengah"
```

---

## Step 9 — Verify Naturalness

Read the title mentally.

Does the title sound like:
- a real editorial article title? → proceed
- a stack of keywords? → revise
- advertising copy? → revise
- an overly long sentence? → trim

---

## Step 10 — Output the Title

### For free text input:
Return the title directly, without additional explanation unless requested.

### For table input:
Return the full table with the `title` column filled.

If the input contains multiple rows, process each row independently through Steps 1–9.

---

## Decision Process Summary

```
INPUT
  ↓
Step 1:  Read all input (anchor 1, anchor 2, brief, mandatory)
  ↓
Step 2:  Identify the anchor's subject and intent
  ↓
Step 3:  Determine context from the brief
  ↓
Step 4:  Generate relationship candidates (Direct / Contextual / Negative / Causal)
  ↓
Step 5:  Select the strongest relationship
  ↓
Step 6:  Select a title format
  ↓
Step 7:  Add a hook if relevant
  ↓
Step 8:  Verify supportability
  ↓
Step 9:  Verify naturalness
  ↓
OUTPUT: FINAL TITLE
```

---

## Final Checklist

Before returning a title, confirm all of the following:

### Relationship

- [ ] The title has a meaningful relationship with the anchor or brief
- [ ] The relationship type has been identified (Direct / Contextual / Negative / Causal / combination)
- [ ] Any Contextual relationship used is meaningful and logically explainable — not merely vague topical proximity

### Content

- [ ] The title represents an article that is realistic to write
- [ ] The title does not promise information the article cannot deliver
- [ ] Any number stated in the title can be fulfilled with genuinely distinct points

### Editorial

- [ ] The title is clear and easy to understand
- [ ] The title has one dominant editorial angle
- [ ] A hook is used only if it genuinely strengthens the title
- [ ] The title is engaging without being misleading

### Accuracy

- [ ] No unsupported factual claims
- [ ] No fabricated statistics
- [ ] No fabricated product attributes
- [ ] No unsupported guarantees
- [ ] No unsupported superiority claims

### Commercial (if a soft-selling brief is present)

- [ ] The title is editorial in nature, not openly promotional
- [ ] The anchor text does not need to appear literally
- [ ] The title can naturally support organic brand or product mention within the article

### Format

- [ ] Title length is within 7–12 words (or a maximum of 80 characters)
- [ ] Any number used is realistic to fulfill
- [ ] The title does not read as a stack of keywords

---

## Handling Ambiguous Input

### If anchor text is very short or generic (e.g. "hemat", "cuan", "motor"):

1. Read brief and mandatory for additional context
2. If the brief provides enough context → use it
3. If the brief provides no useful context → default to the broadest, safest angle for the topic
4. Do not stop the process — always produce the best title possible from the available input

### If anchor text 1 and anchor text 2 conflict or are unrelated:

1. Treat anchor text 1 as the primary subject
2. Use anchor text 2 as additional context only if it adds meaningful information
3. If anchor text 2 adds no meaningful information → ignore it

### If the brief contains instructions that conflict with good title principles:

1. Follow the parts of the brief relevant to the title (topic, context, tone)
2. Ignore the parts that relate to article structure or content
3. Do not produce a misleading title simply because the brief requests it