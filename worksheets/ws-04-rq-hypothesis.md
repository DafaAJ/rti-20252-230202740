# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Sebagian besar penelitian sistem kontrol suhu berbasis IoT masih menggunakan metode ON/OFF sederhana dengan threshold suhu tetap serta belum banyak diuji pada ruang kelas nyata untuk menjaga kestabilan suhu ruangan secara optimal.

Research Question:
  Tipe         : [✓] Comparison  [ ] Improvement  [ ] Exploratory
  Formulasi    : Bagaimana kinerja sistem IoT berbasis ESP32 dan sensor DHT22 dalam menjaga kestabilan suhu ruang kelas dibandingkan penggunaan kipas dan AC konvensional berdasarkan metrik kestabilan suhu ruangan dan waktu respons sistem?
  Variabel IV  : Sistem kontrol suhu berbasis IoT menggunakan ESP32 dan sensor DHT22
  Variabel DV  : Kestabilan suhu ruang kelas
  Metrik       : Rata-rata suhu ruangan, perubahan suhu dalam interval waktu tertentu, kestabilan suhu ruangan, dan waktu respons sistem
  Dataset      : Data suhu dan kelembapan ruang kelas yang diperoleh secara real-time menggunakan sensor DHT22 pada jam kegiatan belajar mengajar
  Baseline     : Penggunaan kipas dan AC konvensional tanpa sistem IoT otomatis

Quality Check RQ:
  [✓] Variabel spesifik
  [✓] Metrik jelas
  [✓] Baseline ada
  [✓] Konteks disebutkan
  [✓] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : Penelitian ini memberikan bukti mengenai kemampuan sistem IoT berbasis ESP32 dan DHT22 dalam menjaga kestabilan suhu ruang kelas secara otomatis dibandingkan sistem pendingin konvensional.
  Jenis kontribusi        : [ ] Improvement  [✓] Comparison  [ ] Novel approach
  Gap yang diisi          : Method gap dan context gap pada penelitian sistem kontrol suhu berbasis IoT untuk ruang kelas nyata.

Hypothesis Pair:
  H₀ : Tidak terdapat perbedaan signifikan dalam kestabilan suhu ruang kelas antara sistem IoT berbasis ESP32 dan sensor DHT22 dengan penggunaan kipas dan AC konvensional.
  H₁ : Terdapat perbedaan signifikan dalam kestabilan suhu ruang kelas antara sistem IoT berbasis ESP32 dan sensor DHT22 dengan penggunaan kipas dan AC konvensional.

  Threshold              : Perbedaan rata-rata suhu ≥ 1°C dan waktu respons sistem lebih cepat dibanding sistem konvensional.
  Justifikasi threshold  : Perbedaan suhu sebesar 1°C sudah cukup memengaruhi kenyamanan ruangan kelas dan dapat digunakan untuk melihat efektivitas sistem kontrol suhu otomatis.
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Sebagian besar penelitian masih menggunakan metode kontrol suhu ON/OFF sederhana dan belum banyak diuji pada ruang kelas nyata untuk menjaga kestabilan suhu secara otomatis.

**RQ versi pertama (tulis bebas):**
> Bagaimana kinerja sistem IoT berbasis ESP32 dan sensor DHT22 dalam menjaga kestabilan suhu ruang kelas dibandingkan penggunaan kipas dan AC konvensional?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Ya | Sistem IoT berbasis ESP32 dan sensor DHT22 |
| Metrik terukur | Ya | Kestabilan suhu ruangan dan waktu respons |
| Baseline | Ya | Kipas dan AC konvensional |
| Dataset/konteks | Ya | Data suhu ruang kelas |

**Tipe RQ:** [✓] Comparison / [ ] Improvement / [ ] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Bagaimana kinerja sistem IoT berbasis ESP32 dan sensor DHT22 dalam menjaga kestabilan suhu ruang kelas dibandingkan penggunaan kipas dan AC konvensional berdasarkan rata-rata suhu ruangan dan waktu respons sistem?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak terdapat perbedaan signifikan dalam kestabilan suhu ruang kelas antara sistem IoT berbasis ESP32 dan DHT22 dengan sistem pendingin konvensional |
| H₁ | Terdapat perbedaan signifikan dalam kestabilan suhu ruang kelas antara sistem IoT berbasis ESP32 dan DHT22 dengan sistem pendingin konvensional |
| Metrik | Rata-rata suhu ruangan, perubahan suhu, dan waktu respons sistem |
| Threshold | Perbedaan rata-rata suhu ≥ 1°C |
| Justifikasi threshold | Perbedaan suhu 1°C cukup memengaruhi kenyamanan ruang kelas dan menunjukkan perubahan performa sistem |

**Apakah hipotesis ini falsifiable?** [✓] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Dengan melakukan pengujian dan membandingkan hasil suhu ruangan antara sistem IoT dan sistem konvensional. Jika tidak ada perbedaan signifikan, maka H₁ ditolak dan H₀ diterima.

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Bagaimana kinerja sistem IoT berbasis ESP32 dan sensor DHT22 dalam menjaga kestabilan suhu ruang kelas dibandingkan penggunaan kipas dan AC konvensional? |
| Variable (IV) | Sistem kontrol suhu berbasis IoT menggunakan ESP32 dan sensor DHT22 |
| Variable (DV) | Kestabilan suhu ruang kelas |
| Metric | Rata-rata suhu ruangan, perubahan suhu, dan waktu respons |
| Data source | Data sensor DHT22 pada ruang kelas secara real-time |
| Analysis method | Perbandingan hasil pengukuran suhu dan analisis rata-rata perubahan suhu |

**Apakah rantai lengkap?** [✓] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? Tidak ada, karena seluruh komponen sudah saling terhubung.

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Perancangan Sistem Kendali Exhaust Fan Berbasis IoT dengan Sensor MQ-2 dan DHT22 untuk Optimalisasi Konsumsi Energi  
**RQ yang diekstrak:** Bagaimana kinerja sistem exhaust fan berbasis IoT menggunakan ESP32, sensor MQ-2, dan DHT22 dalam mengontrol suhu dan kadar gas secara otomatis untuk meningkatkan efisiensi energi?  
**Komponen yang hilang:** Penelitian tersebut sudah menjelaskan metode, konteks, dan metrik seperti konsumsi energi serta respons sistem, tetapi belum memiliki baseline pembanding yang dijelaskan secara rinci terhadap metode kontrol lain sehingga perbandingan performa sistem belum sepenuhnya kuat secara penelitian.  