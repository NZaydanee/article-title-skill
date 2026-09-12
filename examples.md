# Examples Library

Reference examples for various input scenarios.

---

## Section 1 — Single Input (Free Text)

---

### Example 1.1 — Direct

**Input:**
```
Anchor Text: Adidas Adizero Evo SL
```

**Reasoning:**
```
Entity:       running shoe product
Intent:       product evaluation
Relationship: Direct
Format:       numbered (product advantages)
```

**Output:**
```
5 Kelebihan yang Ditawarkan Adidas Adizero Evo SL
```

---

### Example 1.2 — Direct

**Input:**
```
Anchor Text: cara daftar paspor online
```

**Reasoning:**
```
Entity:       administrative process
Intent:       step-by-step guide
Relationship: Direct
Format:       "hal yang perlu disiapkan" (preparation angle — more natural than a plain guide)
```

**Output:**
```
5 Hal yang Perlu Disiapkan Sebelum Daftar Paspor Secara Online
```

---

### Example 1.3 — Direct

**Input:**
```
Anchor Text: harga Honda Beat
```

**Reasoning:**
```
Entity:       motorcycle product
Intent:       purchase consideration
Relationship: Direct (same subject even though "harga" is not repeated in title)
Format:       numbered (things to know before buying)
```

**Output:**
```
5 Hal yang Perlu Diketahui Sebelum Membeli Honda Beat
```

---

### Example 1.4 — Contextual

**Input:**
```
Anchor Text: tiket pesawat Jakarta-Palembang
```

**Reasoning:**
```
Entity:       transportation / airline ticket
Intent:       travel to Palembang
Relationship: Contextual — ticket buyer is naturally interested in destinations at the travel endpoint
Strength:     Strong
Format:       numbered (tourist destinations)
```

**Output:**
```
7 Destinasi Wisata di Kota-Kota Sekitar Palembang yang Bisa Anda Kunjungi
```

---

### Example 1.5 — Contextual

**Input:**
```
Anchor Text: kredit rumah KPR
```

**Reasoning:**
```
Entity:       financial product (home loan)
Intent:       home ownership
Relationship: Contextual — KPR → ownership → house → renovation → unexpected costs
Format:       numbered (costs that surprise homeowners)
Hook:         none needed, framing is already strong
```

**Output:**
```
5 Biaya Renovasi Rumah yang Sering Membengkak Tiba-Tiba
```

---

### Example 1.6 — Direct + Negative

**Input:**
```
Anchor Text: investasi saham pemula
```

**Reasoning:**
```
Entity:       investment activity for beginners
Intent:       guide or warning
Relationship: Direct + Negative
Format:       numbered (mistakes)
Hook:         "Fatal" + "Bikin Buntung" — strong but realistic for investment content
```

**Output:**
```
7 Kesalahan Fatal Investasi Saham Pemula yang Bikin Buntung
```

---

### Example 1.7 — Causal

**Input:**
```
Anchor Text: pola makan tinggi garam
```

**Reasoning:**
```
Entity:       dietary habit
Causal chain: high-salt diet → body mechanism → blood pressure rises
Format:       causal question (Mengapa ... ?)
```

**Output:**
```
Mengapa Tekanan Darah Anda Naik? Ini Mekanisme Tubuh Saat Memproses Natrium
```

---

### Example 1.8 — Causal + Negative

**Input:**
```
Anchor Text: kurang tidur
```

**Reasoning:**
```
Entity:       condition / habit
Causal chain: sleep deprivation → concentration impairment (negative effect)
Format:       causal question
```

**Output:**
```
Mengapa Kurang Tidur Bisa Membuat Konsentrasi Menurun?
```

---

## Section 2 — Multi-Anchor Input

---

### Example 2.1 — Soft Selling with Two Anchors

**Input:**
```
Anchor Text 1: Tengah Bulan Cuan
Anchor Text 2: Blibli
Brief:         Soft Selling Guest Post to promote Blibli
```

**Reasoning:**
```
Anchor 1:     mid-month financial condition (money running low)
Anchor 2:     e-commerce platform
Brief:        soft selling → title must be editorial, not visibly promotional
Relationship: Contextual — cuan at mid-month → budget → smart shopping → e-commerce
Format:       numbered (ways to shop smart)
Hook:         "Tetap Cuan" — answers anchor 1 naturally
```

**Output:**
```
5 Cara Belanja Hemat agar Tetap Cuan di Tengah Bulan
```

Relationship bridge:
```
cuan
 ↓
mid-month budget
 ↓
smart shopping
 ↓
e-commerce
 ↓
Blibli (mentioned inside the article, not in the title)
```

---

### Example 2.2 — Product + Price as Two Anchors

**Input:**
```
Anchor Text 1: STARGAZER CARTENZ
Anchor Text 2: Harga baru Stargazer Cartenz
Brief:         (Bisnis & Keuangan): Kalkulasi Finansial MPV Baru: Skema Penyusutan
               Nilai Aset dan Rasio Fitur terhadap Harga Beli
Mandatory:     Bahas mobil Hyundai sesuai dengan anchor text dalam H2 terpisah.
               Maksimal 3 paragraf
```

**Reasoning:**
```
Anchor 1:     specific vehicle product (Hyundai MPV)
Anchor 2:     price → financial / purchase-decision intent

From brief — taken for title:
  ✓ Category: Bisnis & Keuangan
  ✓ Angle: financial calculation, asset depreciation, feature-to-price ratio

From mandatory — ignored for title:
  ✗ "dalam H2 terpisah" → article structure instruction
  ✗ "Maksimal 3 paragraf" → article length instruction

Relationship: Direct (same product) + Causal (purchase decision → long-term financial implications)
Format:       numbered (financial considerations)
Tone:         serious, analytical
```

**Output:**
```
5 Pertimbangan Finansial Sebelum Membeli Hyundai Stargazer Cartenz
```

Alternative (if asset depreciation angle is prioritized):
```
5 Faktor yang Memengaruhi Nilai Jual Kembali MPV Baru dalam 3 Tahun Pertama
```

---

## Section 3 — Batch Table Input

### Input Table

```markdown
| id | anchor text 1         | anchor text 2                | brief                                                                                                            | mandatory                                                                                   | title | source |
|----|----------------------|------------------------------|------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|-------|--------|
| 1  | STARGAZER CARTENZ    | Harga baru Stargazer Cartenz | (Bisnis & Keuangan): Kalkulasi Finansial MPV Baru: Skema Penyusutan Nilai Aset dan Rasio Fitur terhadap Harga Beli | Bahas mobil Hyundai sesuai anchor text dalam H2 terpisah. Maksimal 3 paragraf              |       |        |
| 2  | kredit rumah KPR     | simulasi KPR BCA             | (Properti): Panduan mengajukan KPR untuk pertama kali                                                            | Sertakan perbandingan bunga minimal 2 bank                                                  |       |        |
| 3  | Tengah Bulan Cuan    | Tengah Bulan Cuan            | Soft Selling Guest Post untuk mempromosikan Blibli                                                               | Promosi Blibli harus masuk secara natural                                                   |       |        |
| 4  | tiket pesawat murah  | promo Garuda Indonesia       | (Travel): Artikel inspirasi perjalanan domestik                                                                  | Sebutkan minimal 3 destinasi lokal                                                          |       |        |
```

### Output Table

```markdown
| id | anchor text 1         | anchor text 2                | brief                                                                                                            | mandatory                                                                                   | title                                                                               | source |
|----|----------------------|------------------------------|------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|--------|
| 1  | STARGAZER CARTENZ    | Harga baru Stargazer Cartenz | (Bisnis & Keuangan): Kalkulasi Finansial MPV Baru: Skema Penyusutan Nilai Aset dan Rasio Fitur terhadap Harga Beli | Bahas mobil Hyundai sesuai anchor text dalam H2 terpisah. Maksimal 3 paragraf              | 5 Pertimbangan Finansial Sebelum Membeli Hyundai Stargazer Cartenz                  |        |
| 2  | kredit rumah KPR     | simulasi KPR BCA             | (Properti): Panduan mengajukan KPR untuk pertama kali                                                            | Sertakan perbandingan bunga minimal 2 bank                                                  | 5 Hal yang Perlu Disiapkan Sebelum Mengajukan KPR untuk Pertama Kali               |        |
| 3  | Tengah Bulan Cuan    | Tengah Bulan Cuan            | Soft Selling Guest Post untuk mempromosikan Blibli                                                               | Promosi Blibli harus masuk secara natural                                                   | 5 Cara Belanja Hemat agar Tetap Cuan di Tengah Bulan                               |        |
| 4  | tiket pesawat murah  | promo Garuda Indonesia       | (Travel): Artikel inspirasi perjalanan domestik                                                                  | Sebutkan minimal 3 destinasi lokal                                                          | 7 Destinasi Domestik yang Bisa Dijangkau dengan Tiket Pesawat Terjangkau           |        |
```

### Batch Processing Notes

- Each row is processed independently through the same decision process
- The `source` column is always left empty in the output
- `mandatory` and `brief` are read only for topic context and title angle
- Article-level instructions in `mandatory` (paragraph count, H2 structure, etc.) are ignored entirely when generating titles

---

## Section 4 — Handling Brief with Article-Level Instructions

**Input:**
```
Anchor Text 1: STARGAZER CARTENZ
Anchor Text 2: Harga baru Stargazer Cartenz
Brief:         Kalkulasi Finansial MPV Baru: Skema Penyusutan Nilai Aset dan Rasio Fitur
               terhadap Harga Beli
Mandatory:     Bahas mobil Hyundai sesuai dengan anchor text dalam H2 terpisah.
               Maksimal 3 paragraf
```

**What is extracted from brief for the title:**
```
✓ "Kalkulasi Finansial"           → financial / calculation angle
✓ "Penyusutan Nilai Aset"         → asset depreciation, resale value
✓ "Rasio Fitur terhadap Harga Beli" → feature-to-price ratio
```

**What is ignored from mandatory:**
```
✗ "dalam H2 terpisah"    → article structure instruction
✗ "Maksimal 3 paragraf"  → article length instruction
```

**Output:**
```
5 Pertimbangan Finansial Sebelum Membeli Hyundai Stargazer Cartenz
```

---

## Section 5 — Alternative Angles for the Same Anchor

A single anchor can generate multiple titles with different angles.
Use this section as reference when multiple title options are requested.

**Anchor:**
```
kredit rumah KPR
```

| Relationship | Title |
|---|---|
| Direct | 5 Syarat Utama Pengajuan KPR yang Perlu Dipersiapkan |
| Direct + Negative | 5 Kesalahan Saat Mengajukan KPR yang Bikin Pengajuan Ditolak |
| Contextual | 5 Biaya Renovasi Rumah yang Sering Membengkak Tiba-Tiba |
| Causal | Mengapa Cicilan KPR Bisa Terasa Semakin Berat dari Tahun ke Tahun? |
| Contextual + Causal | 5 Faktor yang Memengaruhi Kemampuan Membayar Cicilan KPR Jangka Panjang |

Select according to the brief. If no brief provides direction, choose the angle that is most natural and editorially strongest.
