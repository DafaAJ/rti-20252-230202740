# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

**Perbandingan pendekatan Author-centric vs Concept-centric:**

| Aspek | Author-centric (Hindari) | Concept-centric (Gunakan) |
|-------|--------------------------|---------------------------|
| Struktur | Per penulis/paper ("Rahman et al. menyatakan...") | Per konsep/metode ("Pendekatan berbasis transformer") |
| Tujuan | Ringkasan isi paper | Perbandingan metode & identifikasi gap |
| Contoh paragraph | "Rahman (2023) pakai CNN. Lee (2022) pakai LSTM. Zhang (2021) pakai RF." | "Tiga pendekatan dominan: CNN digunakan oleh 4 paper untuk representasi fitur visual; LSTM untuk data sekuensial; RF sebagai baseline klasik." |
| Hasil akhir | Daftar paper | Peta pengetahuan + gap yang teridentifikasi |

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database utama**: IEEE Xplore, ACM DL, Scopus
   - Akses IEEE/ACM melalui jaringan kampus atau VPN institusi
   - Alternatif bebas biaya: Google Scholar, ResearchGate ([researchgate.net](https://www.researchgate.net)), arXiv ([arxiv.org](https://arxiv.org))
2. **Boolean query** yang terdokumentasi eksplisit
   - Contoh: `("anomaly detection" OR "intrusion detection") AND ("deep learning" OR "neural network") NOT ("medical imaging")`
   - Gunakan tanda kutip untuk frasa eksak; AND/OR/NOT mengontrol scope
3. **Snowballing** — dua arah:
   - **Backward snowballing**: buka daftar referensi di paper kunci → telusuri paper yang dikutip
   - **Forward snowballing**: di Google Scholar, klik "Cited by" di bawah paper kunci → temukan paper yang mengutipnya
   - Ulangi 1–2 tingkat untuk membangun cakupan komprehensif
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Sistem Pengendalian Suhu Ruangan Otomatis Berbasis IoT Menggunakan ESP32 dan DHT22
Database   : Google Scholar dan ResearchGate
Query      : ("IoT smart fan" OR "automatic fan control") AND ("ESP32" OR "DHT22") AND ("temperature monitoring")
Tahun      : 2025–2026
Hasil awal : 5 paper → Screening → 5 paper final
```

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
| Said et al. | 2025 | Menggunakan ESP32, sensor DS18B20, relay, dan Blynk untuk sistem kipas otomatis berbasis suhu | Data suhu ruangan, konsumsi energi, dan waktu respons sistem | Sistem mampu menghemat energi sekitar 17,5% dengan respons 1,7–2,2 detik | Sistem masih memakai kontrol ON/OFF sederhana dan bergantung pada koneksi Wi-Fi |
| Roihan et al. | 2025 | Menggunakan ESP32, DHT22, MQTT, relay, dashboard web, dan MySQL untuk monitoring lingkungan | Data suhu, kelembapan, status kipas, dan komunikasi MQTT | Monitoring dan kontrol berjalan stabil dengan waktu respons ±760 ms | Pengontrolan kipas masih threshold sederhana dan keamanan MQTT belum dibahas |
| Setia et al. | 2025 | Menggunakan ESP32, DHT22, MQ-2, fuzzy logic, dan Blynk untuk kontrol exhaust fan otomatis | Data suhu, kelembapan, kadar gas, dan konsumsi daya listrik | Sistem berhasil menghemat energi sebesar 24,6% dan monitoring berjalan real-time | Pengujian masih skala kecil dan bergantung pada kestabilan jaringan Wi-Fi |
| Wulandari et al. | 2026 | Menggunakan ESP32, DHT22, Telegram Bot, dan Blynk untuk monitoring laboratorium | Data suhu, kelembapan, dan notifikasi Telegram | Sistem monitoring bekerja stabil dengan delay notifikasi sekitar 3,2 detik | Sistem hanya monitoring tanpa kontrol otomatis terhadap kipas atau AC |
| Pradana et al. | 2026 | Menggunakan ESP32, DHT11, relay, LCD, dan Telegram Bot dengan metode hysteresis control | Data suhu, kelembapan, dan status kipas otomatis | Sistem mampu mengontrol kipas otomatis dengan respons cepat dan notifikasi real-time | Sensor DHT11 kurang akurat dan threshold suhu masih hardcoded |

```
Pola yang ditemukan:
  Metode dominan     : Sebagian besar penelitian menggunakan ESP32 sebagai mikrokontroler utama dengan sensor DHT22 atau DHT11 serta metode kontrol otomatis berbasis threshold suhu.
  Dataset umum       : Data yang digunakan berupa suhu ruangan, kelembapan, status kipas atau AC, response time sistem, dan data monitoring IoT secara real-time.
  Limitasi berulang  : Kontrol sistem masih sederhana berbasis ON/OFF, ketergantungan pada koneksi Wi-Fi, pengujian masih dalam skala prototipe, dan efisiensi energi belum diuji secara mendalam.

GAP IDENTIFICATION

Gap 1: [Jenis: method]
  Deskripsi    : Sebagian besar penelitian masih menggunakan metode kontrol ON/OFF sederhana dengan threshold suhu hardcoded.
  Bukti        : Ditemukan pada penelitian Said et al. (2025), Roihan et al. (2025), dan Pradana et al. (2026).
  Signifikansi : Sistem menjadi kurang adaptif terhadap perubahan suhu ruangan sehingga efisiensi energi belum optimal.

Gap 2: [Jenis: context]
  Deskripsi    : Penelitian masih banyak diuji pada skala prototipe atau smart home dan belum banyak diterapkan pada ruang kelas nyata.
  Bukti        : Ditemukan pada penelitian Roihan et al. (2025), Setia et al. (2025), dan Wulandari et al. (2026).
  Signifikansi : Performa sistem pada lingkungan pendidikan nyata belum terbukti stabil dan efektif.
```

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|----------|-----------|---------------|--------|
| Sistem kontrol kipas otomatis berbasis ESP32 dan DHT22 | Menggunakan ESP32 dan DHT22 untuk monitoring suhu serta kontrol kipas otomatis seperti penelitian yang dikembangkan | Banyak digunakan pada penelitian smart room dan IoT monitoring suhu | Roihan et al., 2025 |
| Sistem kipas otomatis berbasis ESP32 dan Telegram Bot | Menggunakan Telegram Bot untuk monitoring dan kontrol suhu secara real-time | Merepresentasikan implementasi IoT monitoring sederhana berbasis Telegram | Pradana et al., 2026 |

```
---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan database akademik.

> **Panduan pencarian:**
> - Database: IEEE Xplore, ACM DL, Google Scholar, atau ResearchGate
> - Tulis query Boolean yang digunakan: contoh `("object detection" OR "image classification") AND ("edge computing") NOT ("medical")`. Dokumentasikan query secara eksplisit.
> - Akses gratis: buka Google Scholar → cari judul paper → klik [PDF] jika tersedia, atau akses lewat campus VPN

**Topik riset:** Sistem Pengendalian Suhu Ruangan Otomatis Berbasis IoT Menggunakan ESP32 dan Sensor DHT22
**Query pencarian:** ("IoT smart fan" OR "automatic fan control") AND ("ESP32" OR "DHT22") AND ("temperature monitoring" OR "smart room")
**Database:** Google Scholar dan ResearchGate
```

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | Said et al. — Design and Development of an Automated IoT Smart Fan System Using a Digital Temperature Sensor | 2025 | ESP32, sensor DS18B20, relay, Blynk, kontrol otomatis berbasis threshold suhu | Data suhu ruangan real-time, konsumsi energi, dan waktu respons sistem | Sistem berhasil menghemat energi sebesar 17,5% dan waktu respons stabil 1,7–2,2 detik | Bergantung pada Wi-Fi, hanya memakai sensor suhu tanpa kelembapan, kontrol masih ON/OFF sederhana |
| 2 | Roihan et al. — Integrasi Sensor–Aktuator Berbasis IoT untuk Pengaturan Kipas Otomatis dan Monitoring Lingkungan pada Rumah Pintar | 2025 | ESP32, DHT22, MQTT, relay, dashboard web, MySQL | Data suhu, kelembapan, status kipas, dan komunikasi MQTT real-time | Sistem monitoring dan kontrol berjalan stabil dengan waktu respons ±760 ms | Kontrol kipas masih ON/OFF, keamanan MQTT belum dibahas, pengujian masih skala prototipe |
| 3 | Setia et al. — Perancangan Sistem Kendali Exhaust Fan Berbasis IoT dengan Sensor MQ-2 dan DHT22 untuk Optimalisasi Konsumsi Energi | 2025 | ESP32, DHT22, MQ-2, fuzzy logic, Blynk | Data suhu, kelembapan, gas, daya listrik, dan kecepatan fan | Sistem mampu menghemat energi sebesar 24,6% dan monitoring real-time berjalan baik | Ketergantungan Wi-Fi, sensor MQ-2 membutuhkan preheating lama, pengujian masih skala kecil |
| 4 | Wulandari et al. — Sistem Monitoring Suhu dan Kelembapan Berlebih di Ruangan Laboratorium Komputer Berbasis IoT Menggunakan ESP32 dan DHT22 | 2026 | ESP32, DHT22, Blynk, Telegram Bot, LED indikator | Data suhu dan kelembapan laboratorium, validasi sensor, data notifikasi Telegram dan monitoring Blynk | Sistem monitoring berjalan stabil dengan delay notifikasi ±3,2 detik dan akurasi sensor cukup baik | Sistem hanya monitoring tanpa kontrol otomatis kipas/AC, masih bergantung pada Wi-Fi dan listrik utama |
| 5 | Pradana et al. — Perancangan dan Implementasi Sistem Kipas Angin Otomatis Berbasis ESP32 dan Sensor DHT11 untuk Pengendalian Suhu dan Kelembaban Ruangan | 2026 | ESP32, DHT11, relay, Telegram Bot, LCD 16x2, hysteresis control | Data suhu dan kelembapan real-time, status kipas, response time Telegram Bot, monitoring 14 hari | Sistem berhasil mengontrol kipas otomatis dengan response time cepat dan keberhasilan notifikasi >95% | Akurasi sensor DHT11 masih rendah, threshold suhu masih hardcoded, pengujian jangka panjang masih terbatas|

```
**Pola yang terlihat — Metode dominan:** Sebagian besar penelitian menggunakan ESP32 sebagai mikrokontroler utama, sensor DHT22 atau DHT11 untuk monitoring suhu dan kelembapan, serta metode kontrol otomatis berbasis threshold suhu dengan platform IoT seperti Blynk, MQTT, dan Telegram Bot.
**Limitasi yang berulang:** Sebagian besar penelitian masih menggunakan kontrol ON/OFF sederhana, bergantung pada koneksi Wi-Fi, pengujian masih dalam skala prototipe, serta belum banyak melakukan evaluasi efisiensi energi dan pengujian pada lingkungan nyata seperti ruang kelas.
```

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [✓] Ya / [ ] Tidak | Beberapa penelitian belum menguji efisiensi energi dan kestabilan suhu ruangan secara optimal dalam penggunaan jangka panjang. |
| Method Gap | [✓] Ya / [ ] Tidak | Sebagian besar penelitian masih menggunakan metode kontrol ON/OFF sederhana dengan threshold suhu hardcoded dan belum menerapkan kontrol adaptif antara kipas atau AC secara otomatis. |
| Data Gap | [✓] Ya / [ ] Tidak | Sebagian besar penelitian hanya menggunakan data suhu dan kelembapan dalam skala kecil dan waktu pengujian terbatas sehingga belum merepresentasikan kondisi penggunaan nyata dalam jangka panjang. |
| Context Gap | [✓] Ya / [ ] Tidak | Mayoritas penelitian masih diuji pada skala prototipe atau rumah pintar dan belum banyak diterapkan pada ruang kelas atau ruangan berukuran besar dengan kondisi penggunaan nyata. |

**Gap utama yang dipilih:** Method Gap dan Context Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Karena sistem kontrol suhu ruangan yang masih menggunakan metode sederhana menyebabkan penggunaan energi menjadi kurang efisien dan suhu ruangan kurang stabil. Selain itu, minimnya pengujian pada ruang kelas nyata membuat performa sistem IoT belum terbukti optimal untuk mendukung kenyamanan belajar dan efisiensi penggunaan listrik pada lingkungan pendidikan.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | Sistem kontrol kipas otomatis berbasis ESP32 dan DHT22 | Karena menggunakan komponen dan tujuan sistem yang sama yaitu kontrol suhu ruangan otomatis berbasis IoT | Karena banyak penelitian smart room menggunakan ESP32 dan DHT22 sebagai standar monitoring suhu dan kelembapan | Tidak sepenuhnya, tetapi masih umum digunakan pada penelitian IoT | Roihan et al., 2025 |
| 2 | Sistem monitoring suhu dan kelembapan laboratorium berbasis ESP32 dan DHT22 | Karena sistem monitoring suhu dan kelembapan laboratorium berbasis ESP32 dan DHT22 | Karena merepresentasikan implementasi IoT pada lingkungan ruangan nyata| Ya, termasuk penelitian terbaru tahun 2026 | Wulandari et al., 2026 |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [✓] Tidak
> Justifikasi: Baseline dipilih karena memiliki kesamaan perangkat utama, metode monitoring IoT, dan konteks pengendalian suhu ruangan sehingga perbandingan dilakukan secara adil dan relevan terhadap penelitian yang dikembangkan.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Perbedaan antara pernyataan “belum ada yang meneliti ini” dengan research gap yang valid terletak pada bukti pendukungnya. Research gap tidak hanya berdasarkan pendapat pribadi, tetapi harus diperkuat melalui analisis dari beberapa penelitian sebelumnya. Gap penelitian biasanya muncul karena masih ada keterbatasan, kekurangan, atau masalah yang belum diselesaikan pada penelitian terdahulu. Cara membuktikan adanya gap dapat dilakukan dengan membandingkan metode, hasil penelitian, dan keterbatasan dari beberapa paper yang memiliki topik serupa. Dari perbandingan tersebut biasanya akan terlihat pola kekurangan yang sama, misalnya sistem kontrol suhu yang masih sederhana, pengujian yang belum diterapkan pada kondisi ruang kelas secara langsung, atau pembahasan mengenai efisiensi energi yang masih kurang mendalam.