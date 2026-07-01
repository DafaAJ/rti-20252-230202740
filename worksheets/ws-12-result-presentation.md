# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question : Bagaimana kinerja sistem monitoring dan pengendalian suhu ruang kelas berbasis ESP32, sensor DHT22, relay, dan Telegram Bot dalam memonitor suhu serta mengendalikan kipas secara otomatis?  
Metrik Utama      : 
  1. Suhu (°C)  
  2. Kelembapan (%)  
  3. Status Kipas (ON/OFF)
```

Tabel Hasil:
| Skenario | Metrik 1 (mean ± std) | Metrik 2 (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Sistem Monitoring ESP32 + DHT22 + Telegram Bot | 29,8 ± 3,19 | 50,8 ± 1,30 | 5 |

Visualisasi yang Direncanakan:
| # | Jenis Grafik | Pesan Utama | Metrik |
|---|-------------|-------------|--------|
| 1 | Line Chart | Menampilkan perubahan suhu pada setiap run eksperimen | Suhu |
| 2 | Bar Chart | Menampilkan status kipas berdasarkan suhu yang terbaca | Status Kipas (ON/OFF) |

```
Bias Check:
  [✓] Y-axis mulai dari 0 (atau dijustifikasi)
  [✓] Error bar/CI ditampilkan
  [✓] Semua data disertakan (tidak cherry-picked)
  [✓] Tidak menggunakan 3D tanpa alasan
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Skenario | Metrik 1 (mean ± std) | Metrik 2 (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Sistem Monitoring ESP32, DHT22, Relay dan Telegram Bot | 29,8 ± 3,19 | 50,8 ± 1,30 | 5 |  

**Checklist tabel:**
- [✓] Self-contained (judul jelas, satuan ada, N tercantum)
- [✓] Mean ± std (bukan single number)
- [✓] Diurutkan berdasarkan metrik utama
- [✓] Format konsisten di semua baris

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| # | Jenis Grafik | Pesan | Data yang Digunakan |
|---|-------------|-------|---------------------|
| 1 | Line Chart | Menampilkan perubahan suhu pada setiap run eksperimen | Data suhu 5 run |
| 2 | Bar Chart | Menampilkan kondisi kipas berdasarkan suhu | Status Kipas ON/OFF |
| 3 | Bar Chart + Error Bar | Menampilkan rata-rata suhu beserta variasinya | Mean Suhu ± Std |

---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah Y-axis menyesatkan? | Tidak. Sumbu Y menggunakan skala yang sesuai sehingga tidak memperbesar perbedaan antar data. |
| Apakah error bar ditampilkan? | Ya. Error bar menggunakan standar deviasi untuk menunjukkan variasi hasil pengukuran. |
| Apakah semua kondisi ditampilkan? | Ya. Seluruh hasil dari lima kali pengujian digunakan tanpa menghilangkan data tertentu. |
| Apa solusinya? | Menggunakan skala sumbu yang konsisten, menampilkan seluruh data, serta menambahkan error bar agar variasi data terlihat secara objektif. |

**Evaluasi grafik Anda sendiri dari Latihan 2:**
- [✓] Semua bias check lulus
- [ ] Ada yang perlu diperbaiki: Tidak ada
---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

> Tabel dan grafik memiliki fungsi yang saling melengkapi dalam penyajian hasil penelitian. Tabel menyajikan data secara rinci dan presisi sehingga setiap nilai dapat diketahui dengan jelas, sedangkan grafik membantu memperlihatkan pola, tren, dan hubungan antar data sehingga hasil penelitian lebih mudah dipahami. Dengan adanya kedua bentuk penyajian tersebut, pembaca dapat melihat data secara numerik maupun visual.  

> Selama penelitian ini saya belum pernah dengan sengaja membuat grafik yang menyesatkan. Namun saya memahami bahwa penggunaan skala sumbu yang tidak tepat, penghilangan sebagian data, atau tidak menampilkan variasi data dapat menyebabkan kesimpulan yang keliru. Oleh karena itu, seluruh data hasil eksperimen ditampilkan secara lengkap, menggunakan skala yang konsisten, serta dilengkapi nilai rata-rata (mean) dan standar deviasi (standard deviation) agar hasil penelitian lebih objektif, transparan, dan dapat dipertanggungjawabkan secara ilmiah.