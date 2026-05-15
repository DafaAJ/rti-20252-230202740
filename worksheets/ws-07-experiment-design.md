# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

EXPERIMENT DESIGN

Research Question : Apakah sistem kontrol suhu otomatis berbasis ESP32 dan sensor DHT22 mampu menjaga kestabilan suhu ruang kelas lebih baik dibandingkan pengendalian kipas atau AC secara manual berdasarkan metrik kestabilan suhu dan waktu respons sistem?  
Hypothesis        :  
H₀ : Tidak terdapat perbedaan signifikan pada kestabilan suhu ruang kelas antara sistem otomatis berbasis ESP32 dan DHT22 dengan sistem pendingin manual.  
H₁ : Sistem otomatis berbasis ESP32 dan DHT22 mampu menjaga kestabilan suhu ruang kelas lebih baik dibandingkan sistem pendingin manual.  
Tipe Eksperimen   : [✓] Comparison  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Penggunaan kipas atau AC secara manual tanpa sistem IoT | Sistem manual | Ukuran ruang kelas tetap, posisi sensor tetap, jumlah pendingin tetap, waktu pengujian sama |
| Treatment | Penggunaan sistem otomatis berbasis ESP32 dan DHT22 | Sistem IoT otomatis | Ukuran ruang kelas tetap, posisi sensor tetap, jumlah pendingin tetap, waktu pengujian sama |

Fairness Checklist:
  [✓] Dataset identik untuk semua kondisi
  [✓] Preprocessing setara
  [✓] Tuning effort setara
  [✓] Environment identik
  [✓] Metrik evaluasi sama

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    | Jumlah orang dalam kelas berubah-ubah sehingga memengaruhi suhu | Pengujian dilakukan pada jam dan kondisi kelas yang relatif sama |
| External    | Hasil pengujian hanya dilakukan pada satu ruang kelas | Pengujian dilakukan beberapa kali pada kondisi suhu berbeda |
| Construct   | Sensor DHT22 memiliki keterbatasan akurasi pembacaan | Kalibrasi sensor sebelum pengujian dan membandingkan hasil dengan termometer digital |
| Conclusion  | Jumlah data pengujian terlalu sedikit | Pengambilan data dilakukan 5–10 kali agar hasil lebih konsisten |

Statistical Plan:
  Uji statistik   : Perbandingan rata-rata suhu dan waktu respons  
  Justifikasi      : Digunakan untuk melihat perbedaan performa antara sistem manual dan sistem otomatis  
  Alpha            : 0,05  
  Effect size min  : Perbedaan suhu minimal 1–2°C  

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Apakah sistem kontrol suhu otomatis berbasis ESP32 dan sensor DHT22 mampu menjaga kestabilan suhu ruang kelas lebih baik dibandingkan pengendalian kipas atau AC secara manual?
**Tipe eksperimen:** [✓] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Pendingin ruangan dikontrol manual | Manual | Ruang kelas, posisi sensor, waktu pengujian, dan jumlah pendingin dibuat sama |
| Treatment | Pendingin ruangan dikontrol otomatis oleh ESP32 dan DHT22 | Sistem otomatis IoT | Ruang kelas, posisi sensor, waktu pengujian, dan jumlah pendingin dibuat sama |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | ✓ | Data suhu diambil dari ruang kelas yang sama |
| Preprocessing setara | ✓ | Data suhu dicatat dengan interval waktu yang sama |
| Tuning effort setara | ✓ | Semua pengujian menggunakan konfigurasi sensor yang sama |
| Environment identik | ✓ | Pengujian dilakukan pada kondisi ruang kelas yang sama |
| Metrik evaluasi sama | ✓ | Menggunakan metrik kestabilan suhu dan waktu respons |

**Ada yang tidak fair?** [ ] Ya / [✓] Tidak
> Jika ya, bagaimana cara memperbaikinya? ________________

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Perubahan jumlah siswa dalam kelas memengaruhi suhu ruangan | Pengujian dilakukan pada jumlah pengguna ruang kelas yang relatif sama |
| External | Pengujian hanya dilakukan pada satu jenis ruang kelas | Pengujian dilakukan beberapa kali pada kondisi berbeda |
| Construct | Pembacaan sensor DHT22 dapat mengalami delay atau error | Kalibrasi sensor dan pengambilan data berulang |
| Conclusion | Jumlah sampel data kurang banyak | Menambah jumlah pengujian dan durasi pengambilan data |

**Ancaman mana yang paling sulit dimitigasi?** External validity  
**Mengapa?**
> Karena kondisi setiap ruang kelas berbeda-beda, seperti ukuran ruangan, ventilasi, dan jumlah pengguna ruangan sehingga hasil penelitian belum tentu sama pada semua lingkungan.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah semua baseline diuji pada kondisi dan lingkungan yang sama?  
2. Apakah metrik evaluasi yang digunakan sesuai dan adil untuk semua metode?  
3. Apakah jumlah data dan pengujian yang dilakukan cukup untuk membuktikan hasil penelitian?  