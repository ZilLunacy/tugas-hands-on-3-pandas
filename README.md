# Tugas Hands-On 3: Pandas Lanjutan - Student Performance Analysis

---
**Identitas Pemilik Tugas:**
* **Nama**  :   Muhammad Nazriel Zildjian
* **Kelas** :   TIF RM 24A CID
* **NIM** :   24552011331
---

Proyek ini merupakan bagian dari penugasan Hands-On 3 (Pandas Lanjutan, Data Cleaning, Time Series/Analisis Lanjutan, dan Machine Learning Preprocessing) menggunakan studi kasus **Kasus 08: Student Performance (EdTech)**.

## 📁 Struktur Direktori Proyek

```text
tugas-hands-on-3/
├── README.md                  # Dokumentasi dan ringkasan proyek
├── notebook.ipynb             # Jupyter Notebook / Google Colab (eksekusi dari atas ke bawah)
├── data/
│   └── case9_student_performance.csv    # Dataset mentah asli
└── output/
    ├── data_bersih.csv        # Hasil akhir pembersihan data
    └── kamus_data.csv         # Kamus data (tipe, missing, unik)

## 🛠️ Alur Pengerjaan (Pipeline)

1. **Audit Kualitas Data:** 
   - Memeriksa jumlah baris (800 baris, 19 kolom), duplikat, *missing value* (ditemukan 511 nilai kosong), serta potensi *outlier*.
2. **Pembersihan Data (Data Cleaning):**
   - Menghapus duplikat data.
   - Menangani *missing value* (imputasi median untuk kolom numerik dan modus untuk kolom kategorikal).
   - Menangani *outlier* menggunakan metode IQR (*Interquartile Range*) per grup.
3. **Analisis Lanjutan & Groupby:**
   - Melakukan agregasi data berdasarkan jenis kelamin dan akses internet untuk melihat pola waktu belajar siswa.
4. **Persiapan Model (Machine Learning Preprocessing):**
   - Memisahkan fitur ($X$) dan target ($y$), dengan kolom target **`status_kelulusan`**.
   - Melakukan pembagian data menggunakan `train_test_split` dengan parameter `stratify=y` untuk menjaga proporsi kelas biner.
   - Membangun `ColumnTransformer` (SimpleImputer + StandardScaler untuk numerik, SimpleImputer + OneHotEncoder untuk kategorikal) yang di-*fit* **hanya pada data train** untuk menghindari *data leakage*.

## 🔍 Temuan Utama yang Dapat Ditindaklanjuti

1. **Adopsi Internet yang Tinggi:** Sebagian besar siswa (baik laki-laki maupun perempuan) sudah memiliki akses internet yang memadai, sehingga program pembelajaran berbasis digital (*e-learning*) sangat potensial untuk dikembangkan.
2. **Kemandirian Belajar Tanpa Internet:** Siswa yang tidak memiliki akses internet justru menunjukkan rata-rata jam belajar mandiri per minggu yang sedikit lebih tinggi dibanding yang memiliki akses internet, menandakan tingginya kebutuhan terhadap modul/bahan ajar cetak atau offline yang berkualitas.
3. **Intervensi Kelompok Rentan:** Masih terdapat kelompok siswa (baik laki-laki maupun perempuan) yang belum terhubung dengan internet. Sekolah disarankan untuk menyediakan titik akses (*hotspot* area belajar) atau fasilitas penunjang khusus bagi kelompok ini.

## 🚀 Cara Menjalankan Notebook

1. Buka file **`notebook.ipynb`** di **Google Colab**.
2. Pastikan folder `data/` sudah tersedia dan file `case9_student_performance.csv` telah diunggah ke dalamnya.
3. Pilih menu **Runtime > Run all** untuk menjalankan seluruh sel kode secara berurutan dari atas ke bawah tanpa error.
4. Hasil pembersihan data dan kamus data akan otomatis tersimpan di dalam folder `output/`.
