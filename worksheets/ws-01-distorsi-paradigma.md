# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (DSR). Penting untuk membedakan keduanya:

| Paradigma | Cara Kerja | Contoh di TI |
|-----------|-----------|---------------|
| **Positivis** | Uji hipotesis dengan eksperimen terkontrol | Apakah CNN lebih akurat dari RF pada dataset X? |
| **Design Science Research** | Bangun artefak (sistem/model/framework) untuk menguji proposisi | Dapatkah arsitektur hybrid CNN+LSTM membuktikan peningkatan recall ≥5%? |
| **Interpretivis** | Pahami makna melalui konteks & kualitatif | Bagaimana peneliti manafsirkan anomali data sensor IoT? |

Dalam DSR, artefak **bukan tujuan akhir** — ia adalah instrumen untuk menghasilkan pengetahuan. Pertanyaan riset tetap harus difalsifikasi.

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Dafa Afriza Julianto
Tanggal          : 01/05/2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Apakah akurasi tersebut dari data training atau testing?.
   - Data yang dibutuhkan untuk verifikasi: Confusion matrix, precision, recall, dan distribusi kelas dataset.

2. Posisi paradigma:
   - Pendekatan: [✓] Positivis  [ ] Interpretivis  [✓] Design Science  [ ] Mixed
   - Alasan: Penelitian menggunakan eksperimen (uji model CNN) dan juga membangun model sebagai artefak.

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Dataset seperti NSL-KDD dan UNSW-NB15 mewakili kondisi nyata.
   - Sumber bias potensial: Class imbalance dan distribusi data tidak merata.
   - Langkah mitigasi: Gunakan beberapa dataset dan analisis confusion matrix.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Seluruh hasil eksperimen termasuk yang performanya rendah.
   - Batasan yang diakui sejak awal: Dataset memiliki keterbatasan distribusi dan representasi.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

> **Panduan pencarian paper:** Gunakan [IEEE Xplore](https://ieeexplore.ieee.org), [ACM Digital Library](https://dl.acm.org), atau Google Scholar. Pilih paper **tahun 2020 ke atas**, di topik yang Anda minati: deteksi anomali, klasifikasi citra, NLP, keamanan siber, IoT, dsb.
>
> **Contoh domain TI:** "Deteksi anomali lalu-lintas jaringan menggunakan CNN — akurasi meningkat 94% vs baseline SVM 87%." Distorsi potensial: apakah dataset normal/anomali seimbang? Apakah hanya diuji pada satu vendor traffic?

**Paper yang dipilih:**
> Judul: A Convolutional Neural Network for Improved Anomaly-Based Network Intrusion Detection  
> Penulis (Tahun): Isra Al-Turaiki &  Najwa Altwaijry (2021)  
> Sumber/Link DOI: https://doi.org/10.1089/big.2020.0263

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Menggunakan dataset NSL-KDD dan UNSW-NB15 | NSL-KDD adalah dataset lama, tidak sepenuhnya mencerminkan kondisi modern |
| Data → Processing | Feature engineering dan preprocessing | Transformasi fitur bisa menghilangkan informasi penting |
| Processing → Analysis | Training CNN (BCNN, MCNN) | Model bisa bias terhadap kelas dominan |
| Analysis → Inference | Evaluasi dengan accuracy, precision, recall | Performa multiclass lebih rendah karena imbalance |
| Inference → Knowledge | Menyimpulkan model lebih unggul dari metode lain | Generalisasi terbatas karena dataset tertentu |

**Distorsi paling besar di tahap:** Reality → Data

**Dua distorsi spesifik yang teridentifikasi:**
1. Class imbalance pada dataset  
   Contoh: kelas U2R hanya 0.04% sedangkan kelas lain jauh lebih besar
2. Bias prediksi model ke kelas tertentu  
   Confusion matrix menunjukkan model sering hanya mengenali beberapa kelas dominan

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Hasil dengan dan tanpa outlier harus dilaporkan |
| Transparansi | Harus dijelaskan apakah outlier adalah error atau bagian dari data |
| Peer review | Reviewer akan mencurigai manipulasi jika outlier dihapus tanpa alasan |

**Keputusan akhir dan justifikasi:**
> Outlier tidak boleh dihapus tanpa alasan kuat. Kedua hasil harus tetap ditampilkan agar penelitian transparan dan dapat direplikasi. Ini penting untuk menjaga validitas dan integritas ilmiah.  

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Deteksi anomali jaringan menggunakan CNN

> **Skala 1–5:** 1 = tidak sesuai sama sekali dengan topik ini, 5 = sangat sesuai dan dominan digunakan pada riset bertopik serupa.

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 — berbasis eksperimen dan metrik | 1 — tidak fokus pada makna | 5 — membangun model CNN |
| Jenis data yang dikumpulkan | Accuracy, precision, recall, confusion matrix | Wawancara | Hasil performa model |
| Limitasi paradigma | Tidak menangkap konteks dunia nyata | Subjektif | Bergantung pada kualitas dataset |

**Paradigma yang dipilih:** Positivis + Design Science Research
**Alasan:** Penelitian menguji performa model secara kuantitatif dan membangun sistem CNN sebagai artefak untuk membuktikan peningkatan performa.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?  

**Jawaban:**
> Sebelum mempelajari materi ini, saya cenderung langsung percaya pada angka akurasi tinggi. Namun setelah memahami adanya distorsi, saya menyadari bahwa akurasi saja tidak cukup. Saya akan mempertanyakan apakah data seimbang, bagaimana distribusi kelas, dan apakah model benar-benar mampu mengenali semua kategori, bukan hanya sebagian. Saya juga akan melihat confusion matrix untuk memahami performa sebenarnya.  
