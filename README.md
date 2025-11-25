# Bitcoin & Macroeconomic Correlation Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)

> **Analisis Historis:** Studi kuantitatif mengenai pengaruh indikator makroekonomi (Inflasi, Suku Bunga, GDP) dan pasar global terhadap pergerakan harga aset kripto.

## Daftar Isi
- [Tentang Proyek](#-tentang-proyek)
- [Metodologi & Flowchart](#%EF%B8%8F-metodologi--flowchart)
- [Kamus Data](#-kamus-data)
- [Teknologi](#-teknologi)
- [Cara Penggunaan](#-cara-penggunaan)
- [Hasil Analisis](#-hasil-analisis)
- [Kontributor](#-kontributor)

---

## Tentang Proyek
Proyek ini menerapkan pipeline ETL (Extract, Transform, Load) sederhana untuk mengumpulkan data ekonomi historis dari berbagai sumber API. Tujuannya adalah membentuk dataset terpadu yang memungkinkan analisis korelasi antara aset berisiko tinggi (Bitcoin/Altcoins) dengan indikator ekonomi makro Amerika Serikat dan pasar tradisional.

## ️ Metodologi & Flowchart
Berikut adalah diagram alur dalam proyek ini, mulai dari ekstraksi hingga visualisasi:

![Flowchart Pipeline Project](FLOWCHART_BTC_MACRO.png)

**Penjelasan Langkah:**
1.  **Data Extraction:** Mengambil data time-series historis melalui API (FRED St. Louis, Yahoo Finance, dan Binance).
2.  **Preprocessing:** Pembersihan data `NaN` menggunakan metode *forward-fill/backward-fill* dan penyesuaian format tanggal agar seragam.
3.  **Resampling:** Menyamakan frekuensi data menjadi tiga timeframe (Harian, Bulanan, Kuartalan) untuk memastikan analisis korelasi yang valid.
4.  **Visualization:** Pembuatan Heatmap Korelasi dan plot Time Series untuk interpretasi data.

## Kamus Data
Variabel-variabel yang digunakan dalam analisis ini dikelompokkan berdasarkan sumbernya:

### 1. Indikator Makroekonomi (via FRED St. Louis)
| Ticker | Variabel | Freq Asli | Deskripsi |
| :--- | :--- | :--- | :--- |
| **DTWEXBGS** | Indeks Dolar | Harian | Indeks kekuatan USD terhadap mata uang global. |
| **FEDFUNDS** | Suku Bunga AS | Bulanan | Suku bunga acuan The Fed (Benchmark Interest Rate). |
| **CPIAUCSL** | Inflasi (CPI) | Bulanan | Indeks Harga Konsumen untuk mengukur inflasi. |
| **UNRATE** | Pengangguran | Bulanan | Persentase tingkat pengangguran di AS. |
| **PPIACO** | PPI | Bulanan | Indeks Harga Produsen (biaya produksi). |
| **RSXFS** | Retail Sales | Bulanan | Total penjualan ritel dan layanan makanan. |
| **INDPRO** | Industrial Prod. | Bulanan | Output total sektor industri. |
| **HOUST** | Housing Starts | Bulanan | Proyek pembangunan rumah baru. |
| **M2SL** | Money Supply M2 | Bulanan | Jumlah uang beredar (likuiditas ekonomi). |
| **GDP** | GDP AS | Kuartalan | Produk Domestik Bruto (Pertumbuhan Ekonomi). |

### 2. Pasar Tradisional (via Yahoo Finance)
| Ticker | Variabel | Kategori | Deskripsi |
| :--- | :--- | :--- | :--- |
| **GC=F** | Emas (Gold) | Komoditas | Aset Safe Haven. |
| **SI=F** | Perak (Silver) | Komoditas | Logam mulia industri & investasi. |
| **CL=F** | Minyak WTI | Komoditas | Biaya energi (Energy Costs). |
| **^GSPC** | S&P 500 | Saham | Tolak ukur pasar saham AS. |
| **^DJI** | Dow Jones | Saham | Indeks 30 industri utama AS. |
| **^IXIC** | Nasdaq | Saham | Indeks saham sektor teknologi (Risk-on). |
| **USDIDR=X**| USD/IDR | Forex | Nilai tukar Rupiah terhadap Dolar. |

### 3. Aset Kripto (via Binance)
| Ticker | Aset | Kategori |
| :--- | :--- | :--- |
| **BTC** | Bitcoin | Market Mover / Store of Value |
| **ETH** | Ethereum | Smart Contract Platform |
| **BNB** | BNB | Exchange Utility |
| **SOL** | Solana | Layer 1 Blockchain |
| **DOGE** | Dogecoin | Meme Coin |
| **ADA** | Cardano | Layer 1 Blockchain |
| **XLM** | Stellar | Payment Network |

## Teknologi
* **Language:** Python 3.8+
* **Data Fetching:** `fredapi`, `yfinance`, `python-binance`
* **Data Manipulation:** `pandas`, `numpy`
* **Visualization:** `seaborn`, `matplotlib`

## Cara Penggunaan

1.  **Clone repositori:**
    ```bash
    git clone https://github.com/rafaelhartono8/bitcoin-macro-analysis.git
    ```
2.  **Install library:**
    ```bash
    pip install fredapi python-binance yfinance pandas seaborn matplotlib
    ```
3.  **Setup API Key:**
    * Dapatkan Key gratis di [FRED St. Louis](https://fredaccount.stlouisfed.org/apikeys).
    * Masukkan key Anda ke dalam variabel `FRED_API_KEY` di notebook.
4.  **Jalankan Analisis:**
    Buka file `bitcoin-macro-analysis.ipynb` dan jalankan sel secara berurutan untuk menarik data historis terbaru dan menghasilkan visualisasi.

## Hasil Analisis

### 1. Matriks Korelasi (Correlation Heatmap)
Visualisasi hubungan antar variabel. Warna **merah/gelap** menunjukkan korelasi positif kuat, sedangkan **biru/terang** menunjukkan korelasi negatif.

| 1. Korelasi Harian (Daily) | 2. Korelasi Bulanan (Monthly) | 3. Korelasi Kuartalan (Quarterly) |
| :---: | :---: | :---: |
| ![Daily Heatmap](CORRELATION%20MATRIX/correlation_matrix_daily.png) | ![Monthly Heatmap](CORRELATION%20MATRIX/correlation_matrix_monthly.png) | ![Quarterly Heatmap](CORRELATION%20MATRIX/correlation_matrix_quarterly.png) |
| *Korelasi positif tertinggi pada ETH 0.80 & Korelasi negatif tertinggi pada Index Dolar -0.16.* | *Korelasi positif tertinggi pada ETH 0.79 & Korelasi negatif tertinggi pada Index Dolar -0.33.* | *Korelasi positif tertinggi pada ETH 0.92 & Korelasi negatif tertinggi pada USD to IDR -0.42.* |

### 2. Tren Pergerakan Harga (Time Series)
Grafik pergerakan harga aset dan indikator makro dari waktu ke waktu untuk melihat tren historis.

| 1. Tren Harian (Daily) | 2. Tren Bulanan (Monthly) | 3. Tren Kuartalan (Quarterly) |
| :---: | :---: | :---: |
| ![Daily TS](MARKET%20PRICE%20IN%20TIME%20SERIES/daily_time_series.png) | ![Monthly TS](MARKET%20PRICE%20IN%20TIME%20SERIES/month_time_series.png) | ![Quarterly TS](MARKET%20PRICE%20IN%20TIME%20SERIES/Q_time_series.png) |
| *Grafik memiliki banyak noise.* | *Grafik lebih bersih karena konversi tanggal ke bulan dengan mean.* | *Pertumbuhan ekonomi tiap Q terlihat lebih jelas.* |

> **Insight Utama:**
> * **Bitcoin vs Nasdaq:** Terlihat korelasi positif yang semakin menguat pada timeframe Bulanan dibandingkan Harian.
> * **Bitcoin vs Suku Bunga AS:** Konsisten menunjukkan korelasi negatif ketika Dolar menguat, Bitcoin cenderung melemah.
> * **Bitcoin & Rupiah:** Dampak terlihat lebih signifikan pada data Kuartalan, memiliki korelasi negatif yang tertinggi. Jadi ketika Bitcoin NAIK mata uang Rupiah akan TURUN. Begitu juga sebaliknya, Apabila Bitcoin TURUN, maka Rupiah akan NAIK

## Kontributor
* **Rafael Hartono** (166)
* **Nabil Putra Yuan** (126)
