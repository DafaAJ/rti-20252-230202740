# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Cyber Security & Machine Learning
  Konteks  : Sistem deteksi intrusi jaringan berbasis CNN

System Context
  Input       : Data trafik jaringan
  Process     : Analisis dan klasifikasi trafik menggunakan CNN
  Output      : Prediksi trafik normal atau serangan
  Outcome     : Membantu mendeteksi serangan jaringan lebih cepat
  Constraints : Dataset tidak seimbang dan kebutuhan komputasi tinggi
  Stakeholders: Administrator jaringan, pengguna sistem, peneliti keamanan siber

Fenomena → Problem
  Fenomena yang diamati             : Serangan jaringan semakin kompleks dan sulit dideteksi
  Gejala (symptom) yang terukur     : Tingginya false positive dan false negative pada IDS tradisional
  Masalah yang didiagnosis          : Metode tradisional kurang efektif mengenali pola serangan modern
  Masalah riset (researchable)      : Belum diketahui seberapa efektif CNN dalam meningkatkan performa deteksi intrusi jaringan dibanding metode tradisional
  Variabel yang terukur             : Accuracy, precision, recall, F1-score, false positive rate

Problem Quality Check
  [✓] Clarity — Apakah satu orang membaca akan paham?
  [✓] Measurability — Apakah ada metrik kuantitatif?
  [✓] Relevance — Apakah penting untuk domain?
  [✓] Testability — Apakah bisa gagal?
  [✓] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
  Sistem Intrusion Detection System (IDS) tradisional masih memiliki keterbatasan dalam mendeteksi pola serangan jaringan modern sehingga menghasilkan false positive dan false negative yang cukup tinggi. Permasalahan ini menunjukkan perlunya metode yang mampu mengenali pola trafik jaringan secara lebih efektif. Oleh karena itu, penelitian ini bertujuan untuk menguji efektivitas metode Convolutional Neural Network (CNN) dalam mendeteksi intrusi jaringan berdasarkan data trafik dengan menggunakan metrik accuracy, precision, recall, F1-score, dan false positive rate.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Deteksi intrusi jaringan menggunakan CNN

| Tahap | Hasil |
|-------|-------|
| Reality | Banyak serangan jaringan sulit dideteksi |
| Observed Issue (Symptom) | IDS tradisional menghasilkan false positive tinggi |
| Diagnosed Problem (Root Cause) | Metode tradisional sulit mengenali pola serangan modern |
| Researchable Problem | Belum diketahui efektivitas CNN dalam meningkatkan performa IDS |
| Measurable Variable | Accuracy, precision, recall, F1-score |

**Apakah terjebak solution-first thinking?** [ ] Ya / [✓] Tidak
> Jika ya, kembali ke tahap mana? ________________________

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data trafik jaringan |
| Process | Analisis dan klasifikasi menggunakan CNN |
| Output | Prediksi normal atau serangan |
| Outcome | Meningkatkan efektivitas deteksi intrusi |
| Constraints | Dataset imbalance dan kebutuhan resource tinggi |
| Stakeholders | Administrator jaringan dan pengguna sistem |

**Komponen mana yang paling relevan dengan masalah riset?** Process (analisis dan klasifikasi menggunakan CNN)

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Problem statement jelas dan spesifik |
| Measurability | 5 | Menggunakan metrik evaluasi yang terukur |
| Relevance | 5 | Penting dalam keamanan jaringan modern |
| Testability | 5 | Dapat diuji menggunakan dataset IDS |
| Impact | 4 | Berpotensi meningkatkan performa deteksi jaringan |

**Skor total:** 24 / 25

**Problem statement versi final (1 paragraf):**
> Sistem Intrusion Detection System (IDS) tradisional masih memiliki keterbatasan dalam mendeteksi pola serangan jaringan modern sehingga menghasilkan false positive dan false negative yang cukup tinggi. Oleh karena itu, penelitian ini dilakukan untuk menguji efektivitas metode Convolutional Neural Network (CNN) dalam mendeteksi intrusi jaringan berdasarkan data trafik dengan menggunakan accuracy, precision, recall, dan F1-score sebagai indikator performa model.

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah saat coding biasanya berhubungan dengan bug, error, atau fitur yang tidak berjalan sehingga fokusnya adalah memperbaiki sistem. Sedangkan masalah riset berfokus pada pembuktian ilmiah terhadap suatu gap pengetahuan menggunakan metode yang terukur dan dapat diuji. Dalam riset, keberhasilan tidak hanya dilihat dari sistem yang berjalan, tetapi juga dari validitas hasil dan kontribusi pengetahuan yang dihasilkan.
