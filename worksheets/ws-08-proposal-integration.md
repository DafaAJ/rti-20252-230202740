# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment). Setiap section menjawab pertanyaan yang diangkat section sebelumnya dan memunculkan pertanyaan baru.
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

**Operasionalisasi Red Thread** (benang merah):
```
Bab 2 (Problem) → | memperkenalkan masalah X + evidensi |
                          ↓ menimbulkan pertanyaan: "apa akar gap-nya?"
Bab 3 (Gap)     → | menjawab pertanyaan tadi + membuka "lalu apa yang perlu diteliti?" |
                          ↓
Bab 4 (RQ/H)    → | menjawab gap dengan pertanyaan spesifik + prediksi terukur |
                          ↓
Bab 5-7 (Method)→ | menjawab RQ melalui desain eksperimen yang tepat |
```
Jika ada lompatan (section B tidak menjawab pertanyaan section A), red thread putus.

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [✓] Problem → Gap: masalah terdokumentasi di literatur
  [✓] Gap → RQ: pertanyaan menjawab gap spesifik
  [✓] RQ → Hypothesis: hipotesis memprediksi jawaban
  [✓] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [✓] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [✓] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [✓] Istilah sama di semua bagian
  [✓] Variabel di RQ = variabel di hipotesis = metrik di desain
  [✓] Scope tidak berubah dari masalah ke eksperimen

Cognitive Trap Checklist:
  [✓] Tidak ada paragraf "promosi" di pendahuluan (hanya data & gap)
  [✓] Metodologi disesuaikan ke RQ, bukan copy-paste textbook
  [ ] Timeline sudah ditambah buffer 30-50% dari estimasi awal
  [✓] Proposal mengakui kemungkinan H0 tidak ditolak (honest uncertainty)
  [✓] Tidak ada klaim "pasti berhasil" atau "meningkatkan signifikan"
```

Rubrik Self-Assessment:
| Kriteria     | 1 (Lemah)                                        | 2 (Cukup)                                     | 3 (Baik)                                           | Skor |
|------------- |--------------------------------------------------|-----------------------------------------------|----------------------------------------------------|------|
| Koherensi    | >2 koneksi vertikal terputus                     | 1-2 koneksi lemah, argumen masih bisa diikuti | Semua 6 koneksi terhubung, red thread jelas        | 3 |
| Specificity  | Variabel/metrik masih abstrak, tidak ada angka   | Sebagian metrik terdefinisi numerik           | Semua metrik + threshold + unit pengukuran jelas   | 3 |
| Feasibility  | Timeline >6 bulan tanpa memperhitungkan sumber   | Timeline 3-6 bulan dengan asumsi tertentu     | Timeline 1-3 bulan realistis dengan rencana detail | 3 |
| Rigor        | Baseline tidak jelas atau straw man              | 1-2 baseline dengan justifikasi partial       | 2+ baseline SOTA + justifikasi pemilihan lengkap   | 2 |

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| Problem Statement | WS-02 | Suhu ruang kelas yang tidak stabil dapat mengurangi kenyamanan belajar. Pengaturan kipas atau AC secara manual sering terlambat merespons perubahan suhu ruangan. |
| Gap | WS-03 | Sebagian besar penelitian masih menggunakan kontrol suhu ON/OFF sederhana dan belum banyak diuji pada ruang kelas nyata sebagai lingkungan pembelajaran. |
| RQ | WS-04 | Apakah sistem IoT berbasis ESP32 dan sensor DHT22 mampu menjaga kestabilan suhu ruang kelas lebih baik dibanding pengendalian kipas atau AC secara manual? |
| Hipotesis | WS-04 | H₁: Sistem IoT berbasis ESP32 dan DHT22 menghasilkan suhu ruang kelas yang lebih stabil dibanding sistem manual. |
| Variabel & Metrik | WS-05 | IV = metode pengendalian suhu; DV = kestabilan suhu ruangan; CV = kondisi ruang kelas. Metrik utama berupa rata-rata suhu dan variasi suhu. |
| Sistem | WS-06 | Sistem terdiri dari ESP32, sensor DHT22, relay, kipas/AC, dan Telegram Bot untuk monitoring suhu secara real-time. |
| Desain Eksperimen | WS-07 | Eksperimen dilakukan dengan membandingkan sistem manual dan sistem otomatis pada kondisi ruang kelas yang sama menggunakan metrik kestabilan suhu. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap | ✅ | Gap ditemukan dari beberapa penelitian yang masih menggunakan kontrol sederhana dan belum banyak diuji pada ruang kelas. |
| Gap → RQ | ✅ | RQ dirancang untuk menjawab kebutuhan sistem kontrol suhu yang lebih baik pada ruang kelas. |
| RQ → Hypothesis | ✅ | Hipotesis memprediksi bahwa sistem IoT menghasilkan suhu lebih stabil dibanding sistem manual. |
| Hypothesis → Metric | ✅ | Kestabilan suhu diukur menggunakan rata-rata suhu dan variasi suhu ruangan. |
| Metric → System | ✅ | Sensor DHT22 dan ESP32 menghasilkan data suhu yang digunakan sebagai metrik penelitian. |
| System → Experiment | ✅ | Sistem digunakan langsung sebagai alat eksperimen pada kondisi kontrol dan treatment. |

**Koneksi mana yang paling lemah?** Tidak ada yang terlalu lemah, tetapi hubungan antara gap dan RQ masih dapat diperkuat dengan menambahkan referensi penelitian yang khusus membahas ruang kelas.
**Bagaimana cara memperkuatnya?**
> Menambahkan lebih banyak literatur mengenai implementasi sistem kontrol suhu pada lingkungan pendidikan atau ruang kelas.

**Konsistensi horizontal — apakah istilah dan scope konsisten?** [✓] Ya / [ ] Tidak
> Jika tidak, di bagian mana terjadi inkonsistensi? _________

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| Koherensi | 3 | Semua komponen dari problem hingga eksperimen saling terhubung. |
| Specificity | 3 | Variabel, metrik, dan komponen sistem telah dijelaskan secara spesifik. |
| Feasibility | 3 | Sistem dapat direalisasikan menggunakan ESP32, DHT22, relay, dan Telegram Bot dengan biaya relatif rendah. |
| Rigor | 2 | Sudah memiliki baseline dari literatur, tetapi jumlah baseline masih terbatas. |

**Skor total:** 11 / 12

**Apakah proposal siap untuk fase eksekusi?** [✓] Ya / [ ] Belum
> Jika belum, apa yang perlu diperbaiki? Menambah referensi yang lebih spesifik terkait implementasi smart room pada ruang kelas dan memperjelas jumlah sampel pengujian.

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** Menentukan desain sistem karena komponen yang digunakan seperti ESP32, DHT22, relay, dan Telegram Bot sudah banyak digunakan pada penelitian IoT.
**Bagian tersulit:** Menentukan research gap karena harus membaca dan membandingkan beberapa penelitian sebelumnya untuk menemukan kekurangan yang benar-benar relevan dengan topik penelitian.
**Yang akan dilakukan berbeda:**
> Jika mengulang dari awal, pencarian literatur akan dilakukan lebih sistematis dengan mendokumentasikan query pencarian dan memilih paper yang lebih dekat dengan topik ruang kelas. Selain itu, variabel dan metrik penelitian akan ditentukan lebih awal agar proses penyusunan proposal menjadi lebih terarah.