# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

VARIABLE & METRIC DEFINITION

Research Question: Bagaimana kinerja sistem IoT berbasis ESP32 dan sensor DHT22 dalam menjaga kestabilan suhu ruang kelas berdasarkan metrik kestabilan suhu ruangan dibandingkan penggunaan kipas dan AC konvensional pada objek penelitian berupa ruang kelas?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
| Sistem kontrol suhu berbasis IoT menggunakan ESP32 dan DHT22 | IV | Sistem kontrol suhu otomatis berbasis IoT | Kecepatan respons sistem, akurasi pembacaan sensor, respons otomatis kipas/AC | Ratio dan Interval | Detik dan °C | Sensor DHT22 membaca suhu ruangan secara real-time lalu diproses ESP32 untuk mengaktifkan kipas atau AC otomatis | Digunakan untuk mengetahui kemampuan sistem IoT dalam merespons perubahan suhu ruangan secara otomatis |
| Kestabilan suhu ruang kelas | DV | Kenyamanan dan kestabilan suhu ruangan | Rata-rata suhu ruangan, perubahan suhu tiap interval waktu, kestabilan suhu | Interval | °C | Suhu ruangan dicatat secara berkala selama proses pembelajaran berlangsung | Digunakan untuk mengetahui apakah sistem mampu menjaga suhu ruang kelas tetap stabil dan nyaman |
| Kondisi ruang kelas selama pengujian | CV | Faktor lingkungan yang mempengaruhi hasil pengujian | Ukuran ruangan, jumlah pengguna ruangan, posisi sensor, durasi pengujian | Nominal | - | Kondisi ruang kelas dibuat tetap selama eksperimen berlangsung | Digunakan agar hasil pengujian tidak dipengaruhi faktor luar selain sistem IoT |

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [✓] Setiap langkah terdokumentasi
  [✓] Tidak ada "lompatan logis"
  [✓] Metrik mengukur apa yang dimaksud (construct validity)

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Bagaimana kinerja sistem IoT berbasis ESP32 dan sensor DHT22 dalam menjaga kestabilan suhu ruang kelas dibandingkan penggunaan kipas dan AC konvensional?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Sistem IoT ESP32 dan DHT22 | IV | Pengendalian suhu otomatis berbasis IoT | Respons otomatis kipas/AC dan akurasi sensor | Nominal dan Interval | °C dan detik |
| Kestabilan suhu ruang kelas | DV | Kenyamanan suhu ruangan | Rata-rata suhu dan perubahan suhu | Interval | °C |
| Kondisi ruang kelas | CV | Faktor lingkungan pengujian | Ukuran ruang, posisi sensor, jumlah pengguna | Nominal | - |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [✓] Tidak
> Jika ya, di mana? Karena seluruh variabel dan metrik masih berhubungan langsung dengan tujuan penelitian yaitu menjaga kestabilan suhu ruang kelas menggunakan sistem IoT.

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5 | Metrik kestabilan suhu secara langsung mewakili tujuan penelitian yaitu menjaga kenyamanan suhu ruang kelas |
| Sensitive | 4 | Perubahan suhu kecil masih dapat terdeteksi oleh sensor DHT22 sehingga cukup sensitif terhadap perubahan kondisi ruangan |
| Feasible | 5 | Data suhu dan respons sistem dapat dikumpulkan secara real-time menggunakan ESP32 dan DHT22 dengan biaya rendah |

**Apakah perlu secondary metric?** [✓] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Karena secondary metric digunakan adalah kelembapan ruangan dan kestabilan pembacaan sensor. Kelembapan digunakan sebagai data pendukung kondisi lingkungan ruang kelas, sedangkan kestabilan sensor digunakan untuk memastikan data suhu tetap konsisten selama pengujian.

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika suhu ruangan sudah stabil pada rentang tertentu dan sensor tidak menunjukkan perubahan signifikan, maka perbedaan performa antar sistem kontrol suhu menjadi sulit terlihat karena seluruh hasil terlihat hampir sama.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data point terkumpul? | Sebagian besar data suhu dan respons sistem dapat terkumpul selama pengujian | Melakukan monitoring berkala dan penyimpanan data otomatis |
| Consistency | Apakah ada kontradiksi internal? | Kemungkinan terdapat perbedaan pembacaan sensor akibat perubahan lingkungan | Melakukan kalibrasi sensor dan pengujian berulang |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Ya, karena sensor DHT22 digunakan langsung untuk membaca suhu ruang kelas | Membandingkan hasil sensor dengan termometer standar |
| Representativeness | Apakah sampel mewakili populasi target? | Pengujian dilakukan pada ruang kelas nyata dengan kondisi penggunaan harian | Pengujian dilakukan pada jam pembelajaran normal dan jumlah pengguna yang relatif tetap |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Memilih metrik setelah melihat data dianggap p-hacking karena peneliti dapat memilih hasil yang paling menguntungkan sehingga penelitian menjadi tidak objektif. Hal tersebut dapat menyebabkan kesimpulan penelitian menjadi bias dan kurang valid secara ilmiah.
> Sedangkan eksplorasi data yang sah dilakukan untuk memahami pola data tanpa mengubah hipotesis utama yang telah ditentukan sebelumnya. Metrik tambahan dari eksplorasi tetap boleh dilaporkan, tetapi harus dijelaskan sebagai hasil eksploratif dan bukan sebagai bukti utama penelitian.