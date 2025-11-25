# bitcoin-macro-analysis
Python ETL pipeline integrating FRED (US Macro), Yahoo Finance (Global Markets), and Binance data to analyze historical correlations and Bitcoin price drivers


# 📈 Bitcoin & Macroeconomic Correlation Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Status](https://img.shields.io/badge/Status-Active-green)

> Analisis mendalam mengenai pengaruh indikator makroekonomi (Inflasi, Suku Bunga, GDP) dan data pasar global terhadap pergerakan harga Bitcoin.

## 📋 Daftar Isi
- [Tentang Proyek](#-tentang-proyek)
- [Fitur Utama](#-fitur-utama)
- [Data yang Digunakan](#-data-yang-digunakan)
- [Teknologi & Library](#-teknologi--library)
- [Cara Menjalankan](#-cara-menjalankan)
- [Hasil Analisis](#-hasil-analisis)
- [Kontributor](#-kontributor)

## 📖 Tentang Proyek
Proyek ini bertujuan untuk menganalisis korelasi antara pergerakan harga aset kripto (terutama Bitcoin) dengan berbagai indikator ekonomi global. Dengan menggunakan data historis, kita dapat melihat bagaimana faktor eksternal seperti kebijakan The Fed atau harga komoditas mempengaruhi pasar kripto.

## ✨ Fitur Utama
- **Otomatisasi Data Fetching:** Mengambil data terbaru secara otomatis menggunakan API.
- **Multi-Source Analysis:** Menggabungkan data dari:
  - **FRED (Federal Reserve Economic Data)** untuk data ekonomi AS.
  - **Yahoo Finance** untuk pasar saham dan komoditas.
  - **Binance** untuk data harga mata uang kripto.
- **Timeframe Structuring:** Resampling data ke format Harian, Bulanan, dan Kuartalan untuk analisis yang lebih akurat.
- **Correlation Visualization:** Heatmap korelasi untuk melihat hubungan antar variabel.

## 📊 Data yang Digunakan
Analisis ini mencakup variabel-variabel berikut:

1.  **Indikator Makro (via FRED):**
    * Suku Bunga AS (FEDFUNDS)
    * Inflasi (CPIAUCSL)
    * Pengangguran (UNRATE)
    * GDP AS, M2 Money Supply, dll.
2.  **Pasar Tradisional (via Yahoo Finance):**
    * Emas (GC=F), Perak (SI=F), Minyak (CL=F)
    * Indeks Saham: S&P 500, Dow Jones, Nasdaq
    * Kurs: USD/IDR
3.  **Pasar Kripto (via Binance):**
    * BTC, ETH, BNB, SOL, DOGE, ADA, XLM

## 🛠 Teknologi & Library
Project ini dibangun menggunakan Python dengan library berikut:
* `pandas` & `numpy`: Manipulasi data.
* `fredapi`: Mengakses database ekonomi FRED.
* `yfinance`: Data pasar saham/komoditas.
* `python-binance`: Data historis kripto.
* `seaborn` & `matplotlib`: Visualisasi data.

## 🚀 Cara Menjalankan

1.  **Clone repositori ini:**
    ```bash
    git clone [https://github.com/username-anda/nama-repo.git](https://github.com/username-anda/nama-repo.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install fredapi python-binance yfinance pandas seaborn matplotlib
    ```
3.  **Konfigurasi API Key:**
    Dapatkan API Key dari [FRED St. Louis Fed](https://fredaccount.stlouisfed.org/apikeys).
    Buka notebook dan ganti bagian berikut:
    ```python
    FRED_API_KEY = "MASUKKAN_API_KEY_ANDA_DISINI"
    ```
4.  **Jalankan Notebook:**
    Buka `bitcoin-macro-analysis.ipynb` dan jalankan semua cell.

## 📉 Hasil Analisis (Preview)
Berikut adalah contoh matriks korelasi yang dihasilkan oleh proyek ini:

*(Saran: Ambil screenshot dari output "Correlation Matrix" di notebook Anda dan tempel gambarnya di sini)*
![Correlation Heatmap](link-ke-gambar-heatmap-anda.png)

> **Insight Singkat:**
> * Bitcoin menunjukkan korelasi positif kuat dengan... (isi berdasarkan hasil Anda)
> * Suku bunga The Fed memiliki korelasi negatif dengan... (isi berdasarkan hasil Anda)

## 👥 Kontributor
* **Rafael Hartono** (166)
* **Nabil Putra Yuan** (126)

---
*Dibuat untuk memenuhi tugas [Nama Mata Kuliah/Organisasi] atau sebagai Proyek Portofolio Data Science.*
