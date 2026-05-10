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
  Domain   : Internet of Things (IoT)
  Konteks  : Smart Room untuk kontrol suhu ruang kelas berbasis ESP32 dan DHT22

System Context
  Input       : Data suhu ruangan dari sensor DHT22
  Process     : Monitoring suhu dan kontrol otomatis kipas/AC menggunakan ESP32
  Output      : Kipas atau AC menyala otomatis sesuai suhu ruangan
  Outcome     : Suhu ruang kelas lebih stabil dan penggunaan listrik lebih efisien
  Constraints : Keterbatasan sensor, kestabilan koneksi, dan akurasi pembacaan suhu
  Stakeholders: Siswa, guru, pengelola sekolah, dan pengguna ruangan

Fenomena → Problem
  Fenomena yang diamati             : Suhu ruang kelas sering terasa panas dan tidak stabil
  Gejala (symptom) yang terukur     : Kipas atau AC sering terlambat dinyalakan atau dimatikan
  Masalah yang didiagnosis          : Pengaturan pendingin ruangan masih dilakukan secara manual
  Masalah riset (researchable)      : Belum diketahui efektivitas sistem smart room berbasis IoT dalam mengontrol suhu ruang kelas secara otomatis dan real-time
  Variabel yang terukur             : Suhu ruangan, response time sistem, dan efisiensi penggunaan listrik

Problem Quality Check
  [✓] Clarity — Apakah satu orang membaca akan paham?
  [✓] Measurability — Apakah ada metrik kuantitatif?
  [✓] Relevance — Apakah penting untuk domain?
  [✓] Testability — Apakah bisa gagal?
  [✓] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
  Pengaturan suhu ruang kelas yang masih dilakukan secara manual menyebabkan kondisi ruangan sering tidak stabil karena kipas atau AC terlambat dinyalakan maupun dimatikan. Selain itu, penggunaan pendingin ruangan yang tidak terkontrol dapat menyebabkan pemborosan energi listrik. Permasalahan ini terjadi karena belum adanya sistem monitoring dan kontrol suhu otomatis berbasis IoT yang mampu bekerja secara real-time. Oleh karena itu, penelitian ini bertujuan untuk menguji efektivitas sistem smart room berbasis ESP32 dan sensor DHT22 dalam mengontrol suhu ruang kelas secara otomatis guna meningkatkan kenyamanan ruangan dan efisiensi penggunaan listrik.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Deteksi intrusi jaringan menggunakan CNN

| Tahap | Hasil |
|-------|-------|
| Reality | Suhu ruang kelas sering terasa panas dan tidak nyaman |
| Observed Issue (Symptom) | Kipas atau AC sering terlambat dinyalakan |
| Diagnosed Problem (Root Cause) | Pengaturan suhu ruangan masih dilakukan secara manual |
| Researchable Problem | Belum diketahui efektivitas sistem smart room berbasis IoT dalam mengontrol suhu ruang kelas secara otomatis |
| Measurable Variable | Suhu ruangan, response time, efisiensi listrik |

**Apakah terjebak solution-first thinking?** [ ] Ya / [✓] Tidak
> Jika ya, kembali ke tahap mana? ________________________

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data suhu dari sensor DHT22 |
| Process | ESP32 memproses data suhu dan mengontrol kipas/AC |
| Output | Kipas atau AC aktif otomatis sesuai suhu |
| Outcome | Ruangan lebih nyaman dan penggunaan listrik lebih efisien |
| Constraints | Akurasi sensor dan kestabilan sistem IoT |
| Stakeholders | Siswa, guru, dan pengelola sekolah |

**Komponen mana yang paling relevan dengan masalah riset?** Process (monitoring suhu dan kontrol otomatis menggunakan ESP32)

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | Problem statement jelas dan mudah dipahami |
| Measurability | 5 | Menggunakan variabel yang dapat diukur |
| Relevance | 5 | Penting untuk kenyamanan dan efisiensi energi |
| Testability | 5 | Sistem dapat diuji secara langsung |
| Impact | 5 | Berpotensi meningkatkan kenyamanan dan efisiensi listrik |

**Skor total:** 25 / 25

**Problem statement versi final (1 paragraf):**
> Pengaturan suhu ruang kelas yang masih dilakukan secara manual menyebabkan kondisi ruangan sering tidak stabil karena kipas atau AC terlambat dinyalakan maupun dimatikan. Selain mengurangi kenyamanan belajar, kondisi tersebut juga menyebabkan penggunaan energi listrik menjadi kurang efisien. Oleh karena itu, penelitian ini dilakukan untuk menguji efektivitas sistem smart room berbasis ESP32 dan sensor DHT22 dalam melakukan monitoring dan kontrol suhu ruang kelas secara otomatis dan real-time.

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah saat coding biasanya berkaitan dengan error program atau fitur yang tidak berjalan sehingga fokus utamanya adalah memperbaiki sistem agar dapat berfungsi kembali. Sedangkan masalah riset berfokus pada identifikasi akar masalah dan pembuktian ilmiah terhadap suatu fenomena menggunakan metode yang terukur dan dapat diuji. Dalam riset, keberhasilan tidak hanya dilihat dari sistem yang berjalan, tetapi juga dari validitas hasil dan kontribusi pengetahuan yang dihasilkan.
