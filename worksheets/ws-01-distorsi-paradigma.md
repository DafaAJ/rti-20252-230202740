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
Tanggal          : 10/05/2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Bagaimana metode pengujian sensor dan sistem IoT dilakukan?.
   - Data yang dibutuhkan untuk verifikasi: Data suhu, response time sistem, akurasi sensor, dan hasil monitoring suhu ruangan.

2. Posisi paradigma:
   - Pendekatan: [✓] Positivis  [ ] Interpretivis  [✓] Design Science  [ ] Mixed
   - Alasan: Penelitian menggunakan eksperimen sensor dan membangun prototype smart room berbasis ESP32 sebagai artefak penelitian.

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Sensor DHT11/DHT22 selalu memberikan pembacaan suhu yang akurat.
   - Sumber bias potensial: Posisi sensor, suhu lingkungan, dan delay pembacaan data.
   - Langkah mitigasi: Melakukan kalibrasi sensor dan pengujian pada beberapa kondisi ruangan.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Seluruh hasil pembacaan sensor dan hasil pengujian sistem.
   - Batasan yang diakui sejak awal: Pengujian hanya dilakukan pada ruang kelas tertentu.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

> **Panduan pencarian paper:** Gunakan [IEEE Xplore](https://ieeexplore.ieee.org), [ACM Digital Library](https://dl.acm.org), atau Google Scholar. Pilih paper **tahun 2020 ke atas**, di topik yang Anda minati: deteksi anomali, klasifikasi citra, NLP, keamanan siber, IoT, dsb.
>
> **Contoh domain TI:** "Deteksi anomali lalu-lintas jaringan menggunakan CNN — akurasi meningkat 94% vs baseline SVM 87%." Distorsi potensial: apakah dataset normal/anomali seimbang? Apakah hanya diuji pada satu vendor traffic?

**Paper yang dipilih:**
> Judul: PERANCANGAN DAN IMPLEMENTASI KIPAS ANGIN OTOMATIS BERBASIS ESP32 DAN DHT11 UNTUK PENGENDALIAN SUHU RUANGAN  
> Penulis (Tahun): Radhitya Mugi Pradana, Rico Pahlevi Siregar, Fauzan Ario Bagaskoro, Deni Eka Putra, dan Susilawati (2026)  
> Sumber/Link DOI: https://doi.org/10.23960/jitet.v14i2.9074

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Sensor DHT11 membaca suhu ruangan | Sensor hanya dipasang pada satu titik ruangan |
| Data → Processing | ESP32 memproses data suhu dan mengontrol kipas otomatis | Delay pembacaan sensor dapat memengaruhi respon sistem |
| Processing → Analysis | Analisis performa sistem berdasarkan perubahan suhu | Pengujian dilakukan pada kondisi lingkungan terbatas |
| Analysis → Inference | Menyimpulkan sistem mampu menjaga suhu ruangan | Belum dibandingkan dengan metode kontrol lain |
| Inference → Knowledge | Sistem dianggap efektif untuk smart room | Belum diuji pada ukuran ruangan dan kondisi berbeda |

**Distorsi paling besar di tahap:** Reality → Data

**Dua distorsi spesifik yang teridentifikasi:**
1. Sensor DHT11 hanya membaca suhu pada satu titik sehingga belum merepresentasikan keseluruhan kondisi ruangan.
2. Pengujian sistem dilakukan pada lingkungan terbatas sehingga hasil belum tentu dapat digeneralisasi ke semua ruang kelas.

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Hasil dengan dan tanpa outlier harus tetap dilaporkan |
| Transparansi | Harus dijelaskan apakah outlier merupakan error sensor atau bagian dari data normal |
| Peer review | Reviewer dapat mencurigai manipulasi data jika outlier dihapus tanpa alasan ilmiah |

**Keputusan akhir dan justifikasi:**
> Outlier tidak boleh dihapus tanpa alasan yang jelas dan dapat dipertanggungjawabkan. Peneliti harus menampilkan kedua hasil agar penelitian tetap transparan, valid, dan dapat direplikasi oleh peneliti lain.  

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Rancang Bangun Smart Room Berbasis IoT untuk Kontrol Suhu Ruang Kelas Menggunakan ESP32 dan Sensor DHT22

> **Skala 1–5:** 1 = tidak sesuai sama sekali dengan topik ini, 5 = sangat sesuai dan dominan digunakan pada riset bertopik serupa.

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 — berbasis eksperimen dan data sensor | 1 — tidak fokus pada makna sosial | 5 — membangun prototype smart room |
| Jenis data yang dikumpulkan | Data suhu, kelembapan, response time | Wawancara pengguna | Hasil performa prototype |
| Limitasi paradigma | Tidak menangkap pengalaman pengguna secara mendalam | Bersifat subjektif | Bergantung pada kualitas sensor dan pengujian |

**Paradigma yang dipilih:** Positivis + Design Science Research
**Alasan:** Penelitian berfokus pada pembangunan prototype smart room berbasis IoT dan pengujian performa sistem menggunakan data sensor secara kuantitatif.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?  

**Jawaban:**
> Sebelum mempelajari materi ini, saya cenderung langsung percaya pada klaim performa sistem IoT. Setelah memahami adanya distorsi penelitian, saya menyadari bahwa hasil pengujian dapat dipengaruhi oleh posisi sensor, kondisi lingkungan, dan metode pengambilan data. Oleh karena itu, saya akan lebih kritis dalam melihat validitas data, metode pengujian, dan generalisasi hasil penelitian IoT.  
