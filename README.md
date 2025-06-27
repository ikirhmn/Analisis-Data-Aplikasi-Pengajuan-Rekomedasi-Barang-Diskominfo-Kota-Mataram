# Analisis Data: Aplikasi Pengajuan Rekomendasi Barang Diskominfo Mataram

[![Python](https://img.shields.io/badge/Python-3.8-3776AB?logo=python)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.x-150458?logo=pandas)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-890F02?logo=matplotlib)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.12-3572B2?logo=seaborn)](https://seaborn.pydata.org/)

## 📝 Ringkasan Proyek

Ini adalah proyek **analisis data eksplorasi (Exploratory Data Analysis - EDA)** yang dilakukan sebagai bagian dari program Praktik Kerja Lapangan (PKL). Proyek ini menganalisis data historis dari aplikasi pengajuan rekomendasi pengadaan barang dan jasa di lingkungan Pemerintah Kota Mataram.

Tujuan utama dari analisis ini adalah untuk mengidentifikasi pola, tren, dan anomali dalam data pengajuan untuk memberikan wawasan yang dapat digunakan sebagai dasar pengambilan keputusan strategis dan operasional oleh Diskominfo Kota Mataram.

## 🎯 Pertanyaan Bisnis & Tujuan Analisis

Analisis ini dirancang untuk menjawab serangkaian pertanyaan bisnis yang terstruktur sebagai berikut:

#### Pertanyaan Umum
1.  Perangkat daerah mana yang paling banyak mengajukan rekomendasi pengadaan?
2.  Jenis rekomendasi apa yang paling umum diajukan?
3.  Paket (jenis barang) apa yang paling banyak diajukan?
4.  Berapa harga rata-rata suatu paket berdasarkan pagu anggaran yang diajukan?

#### Pertanyaan Strategis
1.  Apakah perangkat daerah tertentu cenderung mengajukan lebih banyak unit dibanding lainnya?
2.  Perangkat daerah mana yang paling sering mengajukan anggaran tinggi?
3.  Apakah terdapat kecenderungan waktu tertentu (tahun anggaran) ketika pengajuan rekomendasi meningkat signifikan?

#### Pertanyaan Operasional
1.  Berapa rata-rata waktu pemrosesan dari pengajuan hingga persetujuan?
2.  Apakah jenis rekomendasi tertentu diproses lebih cepat dibanding lainnya?
3.  Apakah jumlah dokumen mempengaruhi waktu proses pemeriksaan?

## 📊 Dataset

Dataset yang digunakan berasal dari file `.xlsx` yang merupakan ekspor data dari aplikasi rekomendasi. Data ini terdiri dari **3208 baris** dan **16 kolom** awal yang mencakup informasi seperti:
- `Perangkat Daerah`: Instansi yang mengajukan.
- `Jenis rekomendasi`: Pengadaan Barang/Jasa atau Aplikasi.
- `Paket`: Jenis barang yang diajukan (contoh: Laptop, Printer).
- `Jumlah` & `Satuan`: Kuantitas barang.
- `Pagu anggaran`: Nilai anggaran yang diajukan.
- `Tanggal Pengajuan`: Waktu pengajuan dibuat.
- `Status`: Status terakhir dari pengajuan (contoh: Ditolak, Terbit).
- `Dokumen`: Berkas pendukung dalam format JSON.

## 🛠️ Metodologi Analisis

Proses analisis data mengikuti langkah-langkah berikut:
1.  **Data Gathering**: Memuat data dari file Excel.
2.  **Data Assessing**: Mengevaluasi kualitas data, memeriksa tipe data, dan mengidentifikasi nilai yang hilang (*missing values*).
3.  **Data Cleaning**:
    - Menghapus kolom yang tidak relevan untuk analisis (`Spesifikasi`, `No. HP/WA`, dll.).
    - Menangani baris dengan nilai `Jumlah` yang kosong.
    - Membersihkan dan mengonversi kolom `Pagu anggaran` dari format string (Rp.) ke tipe numerik (integer).
    - Mengonversi kolom tanggal (`Tanggal Pengajuan`, `Tanggal Pemeriksaan`) ke format `datetime`.
4.  **Feature Engineering**:
    - Membuat kolom `Durasi Proses` dengan menghitung selisih antara `Tanggal Pemeriksaan` dan `Tanggal Pengajuan`.
    - Membuat kolom target `klasifikasi` (Logis, Diatas Rata-rata, Dibawah Rata-rata) berdasarkan perbandingan harga per unit dengan harga rata-rata per paket.
5.  **Exploratory Data Analysis (EDA) & Visualisasi**: Melakukan analisis dan membuat visualisasi untuk menjawab setiap pertanyaan bisnis yang telah didefinisikan.

## 📈 Temuan Kunci & Visualisasi

Berikut adalah beberapa temuan utama dari analisis data ini.

#### 1. Perangkat Daerah Pengaju Terbanyak
Analisis menunjukkan bahwa **Pemerintah Daerah** adalah kategori pengaju terbanyak, disusul oleh **Pendidikan** dan **Pemerintah Wilayah**. Secara spesifik, **Dinas Komunikasi dan Informatika** menjadi instansi paling aktif.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6ed8c119-0e08-4718-aec7-5ad31e107002" width="700" alt="Grafik Pengajuan per Perangkat Daerah">
</p>

#### 2. Barang Paling Sering Diajukan
**Printer** dan **Laptop** adalah dua jenis barang (paket) yang paling sering diajukan untuk pengadaan, menunjukkan kebutuhan operasional kantor yang tinggi terhadap kedua perangkat ini.

<p align="center">
  <img src="https://github.com/user-attachments/assets/bbaa13ae-9c22-4b57-b1ce-2c5c3b621d0e" width="700" alt="Grafik Barang Terbanyak">
</p>

#### 3. Tren Pengajuan per Tahun
Terdapat tren penurunan jumlah pengajuan yang signifikan di setiap tahunnya (2022, 2023, 2024).

<p align="center">
  <img src="https://github.com/user-attachments/assets/8f527c7a-a48a-4f9a-9edd-5eca22775468" width="700" alt="Grafik Tren Pengajuan Tahunan">
</p>

#### 4. Rata-rata Durasi Proses
Rata-rata waktu yang dibutuhkan dari sebuah pengajuan dibuat hingga diperiksa (approval) adalah sekitar **37.77 hari**.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e9f78fba-e9c6-40ad-a9c9-60ddc9d35f5a
" width="700" alt="Grafik Durasi Proses">
</p>

## 💻 Teknologi & Library

Proyek ini sepenuhnya dikerjakan menggunakan **Python** di dalam lingkungan **Jupyter Notebook**. Library utama yang digunakan adalah:
- **Pandas**: Untuk manipulasi dan analisis data.
- **NumPy**: Untuk komputasi numerik.
- **Matplotlib & Seaborn**: Untuk visualisasi data.

## 🚀 Cara Menjalankan Proyek

Untuk mereplikasi analisis ini di komputer lokal, ikuti langkah-langkah berikut:

1.  **Clone Repository**
    ```bash
    git clone https://github.com/ikirhmn/Analisis-Data-Aplikasi-Pengajuan-Rekomedasi-Barang-Diskominfo-Kota-Mataram.git
    ```

2.  **Buat Virtual Environment** (direkomendasikan)
    ```bash
    python -m venv venv
    source venv/bin/activate  # Untuk Windows: venv\Scripts\activate
    ```

3.  **Install Dependensi**
    *Pastikan Anda sudah membuat file `requirements.txt` dengan menjalankan `pip freeze > requirements.txt` di terminal Anda.*
    ```bash
    pip install -r requirements.txt
    ```

4.  **Jalankan Jupyter Notebook**
    ```bash
    jupyter notebook
    ```
    Buka file `Diskominfo.ipynb` dan jalankan sel-selnya secara berurutan.

## 👥 Kontributor

- **I Gede Manik Ariyasa** (F1D022046)
- **Lalu Olfata Vedora Zurji** (F1D022046)
- **Rizki Rahman Maulana** (F1D022046)
