# US Airbnb Data Warehouse & Analytics Pipeline (ETL vs ELT)

Project ini dibangun untuk memenuhi Tugas Besar UAS Mata Kuliah Big Data. Sistem ini mengintegrasikan data properti Airbnb di Amerika Serikat (US) dengan data demografi populasi kota dari API eksternal menggunakan dua pendekatan arsitektur pipa data: ETL (Extract-Transform-Load) dan ELT (Extract-Load-Transform).

## 🛠️ Struktur Repositori
Sesuai dengan standar perancangan data warehouse, repositori ini dibagi menjadi beberapa komponen utama:
* **ETL_pipeline/** : Berisi berkas skrip Python Notebook (`.ipynb`) untuk transformasi data berbasis memori Pandas.
* **ELT_pipeline/** : Berisi berkas skrip Python Notebook (`.ipynb`) untuk ekstraksi dan pemuatan data mentah langsung ke database, diikuti transformasi berbasis SQL Engine.
* **Data_Warehouse/** : Tempat penyimpanan berkas basis data relasional SQLite (`.db`) yang mengadopsi skema bintang (*Star Schema*).
* **Dashboard_Visual/** : Menyimpan aset dokumentasi hasil visualisasi berupa tautan interaktif dan tangkapan layar dasbor analitik.

## 🚀 Fitur Utama Sistem
1. **Multi-Source Ingestion**: Menggabungkan file lokal CSV (212.637 baris data Airbnb US) dengan data dinamis berformat JSON langsung dari Geonames API OpenDataSoft melalui jaringan internet.
2. **Data Cleaning & 6 Rules Validation**: Menjamin integritas data dari duplikasi ID, penanganan *outlier* harga dengan metode IQR, standarisasi teks, dan validasi batas logika kalender ketersediaan properti.
3. **Feature Engineering**: Penambahan 5 fitur bisnis turunan (Kategori Kelas Ekonomi, Kerapatan Ulasan Konsumen, Kesiapan Sewa Tahunan, Estimasi Omzet Kotor, dan Tingkat Dominansi Skala Bisnis Host).
4. **Normalisasi & Encoding**: Transformasi data numerik menggunakan teknik *Min-Max Scaling* ke skala 0-1 serta perubahan teks kategorikal menjadi kode ID angka demi optimalisasi performa database.
5. **Live Automated Dashboard**: Visualisasi interaktif yang menerapkan arsitektur *Live Connection* menggunakan sinkronisasi data bertahap (*chunking*) via Google Sheets API untuk menjamin data tetap *up-to-date*.

## 📊 Tautan Penting Project
* **Interactive Dashboard**: [Looker Studio Live Dashboard](https://datastudio.google.com/u/0/reporting/488ccb55-46df-40ee-ab08-4bb1bf3b50c6/page/FLD1F/edit)


## 💻 Cara Menjalankan Pipeline (Reproducible)
1. Buka folder `ETL_pipeline/` atau `ELT_pipeline/` lalu jalankan berkas `.ipynb` di Google Colab Anda.
2. Lakukan pengunggahan file dataset mentah asli `AB_US_2023.csv` ke menu folder penyimpanan sesi di sebelah kiri Google Colab.
3. Pilih menu **Runtime** -> **Jalankan semua** (Run All) pada Google Colab secara berurutan.
4. Pada bagian akhir skrip ELT, sistem akan meminta persetujuan otorisasi akun Google Anda untuk melakukan sinkronisasi data *live* otomatis langsung ke ekosistem awan (*cloud*).
