# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

EXECUTION PLAN

| Run # | Skenario | Seed | Parameter | Status | Waktu | Output File |
|-------|----------|------|-----------|--------|-------|-------------|
| 1 | Suhu tinggi (32°C) | N/A | Batas 30°C | Selesai | 10 menit | run1.xlsx |
| 2 | Suhu normal (25°C) | N/A | Batas 30°C | Selesai | 10 menit | run2.xlsx |
| 3 | Suhu tinggi (33°C) | N/A | Batas 30°C | Selesai | 10 menit | run3.xlsx |
| 4 | Suhu normal (28°C) | N/A | Batas 30°C | Selesai | 10 menit | run4.xlsx |
| 5 | Suhu tinggi (31°C) | N/A | Batas 30°C | Selesai | 10 menit | run5.xlsx |

```
Jumlah runs per skenario : 5
Total runs               : 5

DATA LOG (per run):
  Run ID    : RUN-001  
  Timestamp : 29-06-2026  
  Skenario  : Suhu awal 32°C  
  Input     : DHT22 membaca suhu ruang  
  Output    : Relay aktif, kipas menyala  
  Anomali   : Tidak ada  
  Catatan   : Sistem bekerja normal  

  Run ID    : RUN-002  
  Timestamp : 29-06-2026  
  Skenario  : Suhu awal 25°C  
  Input     : DHT22 membaca suhu ruang normal  
  Output    : Relay mati, kipas mati  
  Anomali   : Tidak ada  
  Catatan   : Sistem bekerja normal  

  Run ID    : RUN-003  
  Timestamp : 29-06-2026  
  Skenario  : Suhu awal 33°C  
  Input     : DHT22 membaca suhu ruang panas 
  Output    : Relay aktif, kipas menyala  
  Anomali   : Tidak ada  
  Catatan   : Sistem bekerja normal  

  Run ID    : RUN-004  
  Timestamp : 29-06-2026  
  Skenario  : Suhu awal 28°C  
  Input     : DHT22 membaca suhu ruang normal  
  Output    : Relay mati, kipas mati  
  Anomali   : Tidak ada  
  Catatan   : Sistem bekerja normal  

  Run ID    : RUN-005  
  Timestamp : 29-06-2026  
  Skenario  : Suhu awal 31°C  
  Input     : DHT22 membaca suhu ruang panas  
  Output    : Relay aktif, kipas menyala  
  Anomali   : Tidak ada  
  Catatan   : Sistem bekerja normal  
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| 1 | Suhu tinggi (32°C) | N/A | Batas suhu 30°C | Selesai |
| 2 | Suhu rendah (25°C) | N/A | Batas suhu 30°C | Selesai |
| 3 | Suhu tinggi (33°C) | N/A | Batas suhu 30°C | Selesai |
| 4 | Suhu normal (28°C) | N/A | Batas suhu 30°C | Selesai |
| 5 | Suhu tinggi (31°C) | N/A | Batas suhu 30°C | Selesai |

**Total skenario:** 1
**Run per skenario:** 5
**Total run keseluruhan:** 5

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID | run-001 |
| Timestamp | 2026-06-28 09:00 |
| Skenario | Suhu tinggi |
| Durasi | 10 menit |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Threshold | 30°C |
| DHT22 GPIO | 13 |
| Relay GPIO | 26 |
| Framework | Arduino |
| Platform | PlatformIO |
| Code Version | main.cpp v1.0 |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Suhu | Float | 0–80°C |
| Kelembapan | Float | 0–100% |
| Status Relay | Boolean | ON/OFF |
| Notifikasi Telegram | Boolean | Berhasil/Gagal |
| Waktu Respon | Integer | Detik |

**Format output:** [✓] CSV / [ ] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Sensor gagal membaca | Nilai NaN | Membaca ulang sensor |
| WiFi terputus | Telegram gagal | Reconnect WiFi |
| Data ekstrem | Suhu > 80°C | Catat dan abaikan data |
| Waktu respon lambat | Delay tinggi | Ulang pengujian |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Sebelumnya pengujian sistem hanya dilakukan satu kali sehingga hasil yang diperoleh belum dapat menunjukkan konsistensi sistem secara menyeluruh.  
**Yang akan dilakukan berbeda:**
> Penelitian ini menggunakan multiple run untuk mengetahui kestabilan sistem. Pengujian berulang meningkatkan kepercayaan terhadap hasil karena sistem diuji pada berbagai kondisi suhu.