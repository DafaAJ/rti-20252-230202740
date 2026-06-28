# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

> **Mengapa reproducibility penting?** Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. _Replicability crisis_ yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: **dokumentasi environment = snapshot kredibilitas riset Anda.**

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
   - **Docker** = teknologi container yang "membungkus" aplikasi beserta seluruh dependency-nya dalam satu unit terisolasi. Hasilnya: kode berjalan identik di laptop, server, maupun reviewer lain. Intro singkat: `docker run -v $(pwd):/workspace environment-image python run_experiment.py`
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Dependency Locking

Mengandalkan "install library terbaru" berbahaya: versi berbeda = perilaku berbeda = hasil tidak reproducible. Praktik:
- **Python**: buat `requirements.txt` dengan versi eksplisit: `scikit-learn==1.3.2`, lalu kunci dengan `pip freeze > requirements.txt`
- **Conda**: gunakan `conda env export > environment.yml` untuk snapshot lengkap
- **Node.js/R/Julia**: gunakan `package-lock.json` / `renv.lock` / `Project.toml` — semua fungsi serupa: lock versi + hash

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : AMD Ryzen 3 7320U (4 cores, 8 thread)
  RAM     : 8 GB LPDDR5
  GPU     : AMD Radeon 610M 2 GB
  Storage : SSD 512 GB 

Software:
  OS        : Windows 11 Home Single Language
  Runtime   : PlatformIO
  Framework : Arduino Framework
  Simulator : Wokwi
  IDE       : Visual Studio Code
```

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
| DHT Sensor Library | 1.4.7 | Adafruit | Membaca sensor DHT22 |
| UniversalTelegramBot | 1.3.0 | Witnessmenow | Komunikasi Telegram |
| WiFi | ESP32 Core | Arduino ESP32 | Koneksi WiFi |
| WiFiClientSecure | ESP32 Core | Arduino ESP32 | Koneksi HTTPS Telegram |
| ArduinoJson | 7.4.3 | ArduinoJson | Pemrosesan data JSON |

```
Konfigurasi:
  Config file     : platformio.ini dan private.ini
  Random seed     : Tidak digunakan
  Hyperparameters : 
    - Suhu maksimum = 30°C
    - Interval sensor = 2 detik
    - Interval Telegram = 5 detik
    - Delay antrian Telegram = 1,5 detik

Reproducibility Check:
  [✓] Dependency terdokumentasi (requirements.txt / lock file)
  [ ] Seed ditetapkan di semua level (Python, NumPy, framework)
  [✓] Config di version control
  [✓] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | AMD Ryzen 3 7320U (4 Core, 8 Thread) |
| RAM | 8 GB LPDDR5 |
| GPU | AMD Radeon 610M 2 GB |
| OS | Windows 11 Home Single Language |
| Runtime | PlatformIO |
| Framework | Arduino Framework |
| Random Seed | Tidak digunakan |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| DHT Sensor Library | 1.4.7 | Membaca suhu dan kelembapan |
| UniversalTelegramBot | 1.3.0 | Monitoring Telegram |
| WiFi | ESP32 Core | Koneksi internet |
| WiFiClientSecure | ESP32 Core | HTTPS Telegram API |
| ArduinoJson | 7.4.3 | Parsing data Telegram |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | Tidak digunakan | Status kipas pada suhu 32°C | — |
| 2 | Tidak digunakan | | [✓] Ya / [ ] Tidak |
| 3 | Tidak digunakan | Kipas menyala kembali pada suhu 33°C | [✓] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**

> Penyebab umum non-repeatability:
> - **Perubahan suhu lingkungan** — kondisi ruangan, cuaca, atau jumlah orang di ruangan berbeda saat pengujian.  
> - **Koneksi WiFi tidak stabil** — menyebabkan keterlambatan pengiriman notifikasi Telegram.  
> - **Toleransi sensor DHT22** — sensor memiliki error pengukuran sekitar ±0,5°C.  
> - **Perbedaan interval pembacaan** — waktu sampling sensor yang berbeda dapat menghasilkan data yang berbeda.  
> - **Gangguan catu daya atau perangkat** — tegangan tidak stabil dapat memengaruhi pembacaan sensor dan relay.  

___________________________________________________

**Checklist kontrol yang sudah diterapkan:**
- [✓] Random seed di-set di semua level (tidak diperlukan pada sistem IoT ini)  
- [✓] Tidak ada background process yang mengganggu  
- [ ] Cache dibersihkan antar-run (tidak relevan pada ESP32)    
- [✓] Config file yang sama untuk semua run  
- [✓] Kode program tidak diubah selama pengujian  
- [✓] Batas suhu tetap 30°C pada seluruh pengujian  
- [✓] Environment pengujian dibuat semirip mungkin  

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Sistem Monitoring dan Pengendalian Suhu Ruang Kelas Berbasis ESP32, Sensor DHT22, dan Telegram Bot

## 1. Environment
CPU: AMD Ryzen 3 7320U
RAM: 8 GB
OS: Windows 11
Framework: Arduino Framework
Platform: PlatformIO
Simulator: Wokwi

## 2. Installation
1. Install Visual Studio Code.
2. Install ekstensi PlatformIO.
3. Clone repository GitHub.
4. Install seluruh library.
5. Konfigurasikan private.ini.

## 3. Data
Data yang dihasilkan berupa:
- Suhu (°C)
- Kelembapan (%)
- Status relay
- Status kipas
- Notifikasi Telegram

## 4. Execution
- Jalankan simulasi Wokwi.
- Build project menggunakan PlatformIO.
- Upload program ke ESP32.
- Buka Serial Monitor.

## 5. Configuration
- DHT22 pada GPIO 13.
- Relay pada GPIO 26.
- Batas suhu 30°C.
- Interval pembacaan 2 detik.

## 6. Expected Output
- Suhu tampil pada Serial Monitor.
- Kipas menyala saat suhu ≥ 30°C.
- Kipas mati saat suhu < 30°C.
- Telegram menerima notifikasi.
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [✓] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> Repository GitHub publik, dokumentasi pengujian pada perangkat ESP32 fisik, dan dokumentasi hasil pengujian dalam bentuk tabel atau grafik.