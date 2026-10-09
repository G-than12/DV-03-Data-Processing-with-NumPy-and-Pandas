# DV-03-Data-Processing-with-NumPy-and-Pandas

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243.svg?logo=numpy&logoColor=white)](https://numpy.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)](#)

Repositori ini berisi pengerjaan **Tugas Praktikum 2 - Pertemuan 3** pada mata kuliah **Visualisasi Data** dengan topik **Pengolahan Data dengan NumPy dan Pandas**. Seluruh kode, langkah pembersihan data (*data cleaning*), latihan mandiri, dan jawaban pertanyaan diskusi diimplementasikan secara interaktif dalam Jupyter Notebook.

---

## 👤 Identitas Mahasiswa

| Atribut | Keterangan |
| :--- | :--- |
| **Nama Mahasiswa** | Gathan Hilabi |
| **NIM** | 059 |
| **Mata Kuliah** | Visualisasi Data |
| **Pertemuan** | 3 (Tiga) |
| **Topik** | Pengolahan Data dengan NumPy dan Pandas |
| **Dataset** | Titanic Dataset (seaborn-data public repository) |

---

## 📁 Struktur Direktori

```text
DV-03-Data-Processing-with-NumPy-and-Pandas/
├── Praktikum3_GathanHilabi_60324059.ipynb   # Notebook utama praktikum (lengkap dengan output)
├── PANDUAN_NUMPY_PANDAS.md                 # Panduan komprehensif & cheatsheet NumPy dan Pandas
├── titanic_bersih.csv                      # Dataset hasil pembersihan (clean data)
└── README.md                               # Dokumentasi lengkap repositori
```

> 📖 **Panduan Pembelajaran:** Untuk penjelasan mendalam mengenai konsep, arsitektur, perbedaan, serta cheatsheet sintaks lengkap NumPy dan Pandas, silakan pelajari dokumen [PANDUAN_NUMPY_PANDAS.md](PANDUAN_NUMPY_PANDAS.md).

---

## 🎯 Tujuan Praktikum

1. Menggunakan array **NumPy** untuk komputasi dan operasi numerik dasar.
2. Memuat dataset tabular (CSV) ke dalam **DataFrame Pandas** serta melakukan eksplorasi data awal (*Exploratory Data Analysis* - EDA).
3. Mengakses, memfilter (*boolean indexing*), dan memanipulasi kolom serta baris data.
4. Mendeteksi dan menangani *missing value* (nilai kosong) dan duplikasi data secara tepat.
5. Menyimpan data yang telah dibersihkan agar siap digunakan pada tahap visualisasi data.

---

## 🛠️ Ringkasan Alur Praktikum (Langkah 1 - 10)

1. **Menyiapkan Notebook & Import Library**: Mengimpor pustaka fundamental `numpy` (alias `np`) dan `pandas` (alias `pd`).
2. **Dasar Array NumPy**: Membuat larik `nilai_ujian = np.array([78, 85, 90, 65, 72])` serta menghitung rata-rata (78.0), maksimum (90), minimum (65), dan standar deviasi (8.67).
3. **Membaca Dataset**: Membaca dataset Titanic langsung dari repositori publik GitHub menggunakan `pd.read_csv()` dan menginspeksi 5 baris teratas dengan `.head()`.
4. **Eksplorasi Awal**:
   - Meninjau dimensi dataset dengan `df.shape` (891 baris, 15 kolom).
   - Melihat daftar kolom dengan `df.columns`.
   - Menginspeksi tipe data dan hitungan non-null melalui `df.info()`.
   - Menganalisis statistik deskriptif numerik melalui `df.describe()`.
5. **Mengakses Kolom & Baris**:
   - Ekstraksi kolom tunggal `df['age']`.
   - Ekstraksi multi-kolom `df[['age', 'sex', 'survived']]`.
   - *Filtering* data penumpang anak (`df['age'] < 18`), menghasilkan **113 penumpang anak**.
6. **Mendeteksi Missing Value**: Menggunakan `df.isnull().sum()`. Ditemukan nilai kosong pada kolom `age` (177), `embarked` (2), `deck` (688), dan `embark_town` (2).
7. **Menangani Missing Value**:
   - *Strategi 1 (Imputasi)*: Mengisi missing value numerik pada kolom `age` dengan nilai rata-rata (`df['age'].mean()`).
   - *Strategi 2 (Eliminasi)*: Menghapus baris yang memiliki nilai kosong pada kolom kategorikal penting `embarked` (`df.dropna(subset=['embarked'])`).
8. **Mendeteksi & Menghapus Duplikasi**:
   - Memeriksa jumlah baris sebelum pembersihan duplikasi (889 baris).
   - Mendeteksi 111 baris data duplikat (`df.duplicated().sum()`).
   - Menghapus duplikasi dengan `df.drop_duplicates()`, menghasilkan 778 baris bersih.
9. **Menyimpan Dataset Bersih**: Menyimpan DataFrame bersih ke file `titanic_bersih.csv` tanpa menyertakan indeks (`index=False`).
10. **Dokumentasi Proses**: Mendokumentasikan ringkasan angka perubahan data secara rinci pada sel Markdown.

### 📊 Rangkuman Metrik Pembersihan Data

| Tahapan / Parameter | Sebelum Pembersihan | Sesudah Pembersihan | Keterangan Tindakan |
| :--- | :---: | :---: | :--- |
| **Total Baris Data** | 891 baris | 778 baris | 2 baris dihapus (embarked kosong), 111 baris duplikat dihapus |
| **Total Kolom** | 15 kolom | 15 kolom | Struktur atribut dipertahankan |
| **Missing Value `age`** | 177 | 0 | Diimputasi menggunakan nilai mean (~29.70 tahun) |
| **Missing Value `embarked`** | 2 | 0 | Baris dengan nilai kosong di-drop |
| **Baris Duplikat** | 111 baris | 0 baris | Dihapus menggunakan `df.drop_duplicates()` |

---

## 📝 Penyelesaian Latihan Mandiri

### Latihan 1: Eksplorasi Baris Data
- **Perintah**: Menampilkan 10 baris pertama (`df.head(10)`) dan 5 baris terakhir (`df.tail(5)`).
- **Hasil**: Data baris teratas dan terbawah berhasil diekstrak dan divisualisasikan dalam bentuk tabel tabular interaktif.

### Latihan 2: Perbandingan Rata-rata Usia (NumPy vs Pandas)
- **Perintah**: Menghitung rata-rata usia dengan `np.mean(df['age'])` dan `df['age'].mean()`.
- **Hasil**:
  - Rata-rata NumPy: `29.699118`
  - Rata-rata Pandas: `29.699118`
  - **Kesimpulan**: Keduanya bernilai sama persis (*identical*). Pandas dibangun di atas arsitektur NumPy sehingga metode komputasi numeriknya menghasilkan ketepatan yang setara.

### Latihan 3: Filtering Penumpang Kelas 1 yang Selamat
- **Perintah**: Memfilter data dengan kondisi ganda `(df['pclass'] == 1) & (df['survived'] == 1)`.
- **Hasil**: Ditemukan sebanyak **122 penumpang** yang berada di Kelas 1 dan berhasil selamat.

### Latihan 4: Imputasi Modus pada Kolom Kategorikal
- **Perintah**: Mengisi nilai kosong kolom `embarked` dengan nilai modus menggunakan `df['embarked'].mode()[0]`.
- **Hasil**: Nilai modus untuk kolom `embarked` adalah `'S'` (Southampton). Teknik ini merupakan *best practice* untuk data bertipe kategorikal tanpa merusak distribusi kategori mayoritas.

### Latihan 5: Persentase Penumpang yang Selamat
- **Perintah**: Menghitung persentase kelulusan hidup menggunakan `df['survived'].mean() * 100`.
- **Hasil**: Persentase keselamatan penumpang pada dataset bersih adalah sebesar **41.13%** (320 dari 778 penumpang selamat).

---

## 💬 Jawaban Pertanyaan Diskusi

### 1. Mengapa penting memeriksa dan menangani missing value sebelum data digunakan untuk membuat visualisasi?
**Jawaban:**
1. **Mencegah Galat (Runtime Error):** Beberapa modul visualisasi di Python dan algoritma pemodelan numerik tidak dapat memproses nilai `NaN`/`null`, sehingga dapat memicu error atau peringatan saat pembuatan diagram.
2. **Menghindari Bias Representasi:** Kehilangan data yang tidak ditangani secara tepat dapat mengubah rasio perbandingan kategori atau menggeser kurva distribusi, sehingga pembaca visualisasi menerima informasi yang keliru (*misleading*).
3. **Integritas Analisis:** Memastikan setiap titik data yang digambarkan pada plot mewakili populasi atau sampel yang valid dan dapat dipertanggungjawabkan.

### 2. Dalam kondisi seperti apa sebaiknya kita menggunakan `dropna()`, dan dalam kondisi seperti apa lebih baik menggunakan `fillna()`?
**Jawaban:**
- **Gunakan `dropna()` jika:**
  - Jumlah baris data yang kosong sangat sedikit relatif terhadap ukuran keseluruhan dataset (contoh: < 1-2%), sehingga penghapusan baris tidak merusak karakteristik populasi data.
  - Kolom yang hilang merupakan variabel kunci atau target label (seperti status keselamatan `survived`) yang tidak boleh ditebak atau diasumsikan.
  - Suatu kolom memiliki persentase missing value yang sangat dominan (misalnya > 70-80% seperti kolom `deck`), sehingga kolom tersebut lebih aman dieliminasi secara total.
- **Gunakan `fillna()` jika:**
  - Ukuran dataset relatif kecil, di mana membuang baris data akan mengurangi daya statistik (*statistical power*) sampel.
  - Nilai kosong dapat diestimasi secara logis menggunakan parameter pemusatan data tanpa mendistorsi pola distribusi asli, misalnya menggunakan **mean** atau **median** untuk data numerik, dan **modus** untuk data kategorikal.

### 3. Apa risiko yang bisa terjadi jika data duplikat tidak dihapus sebelum data dianalisis atau divisualisasikan?
**Jawaban:**
1. **Distorsi Statistik Agregasi:** Nilai mean, standar deviasi, frekuensi, dan kuartil akan terboboti secara berlebih (*over-weighted*) pada observasi tertentu (*pseudoreplication*).
2. **Bias pada Visualisasi Data:** Grafik seperti bar chart frekuensi, scatter plot, dan histogram akan memperlihatkan konsentrasi buatan yang menyesatkan, membuat fenomena tertentu tampak lebih umum daripada kenyataannya.
3. **Data Leakage dan Overfitting:** Dalam konteks machine learning lanjutan, baris yang terduplikasi pada data latih dan data uji dapat menyebabkan kebocoran data (*data leakage*), sehingga model tampak memiliki akurasi tinggi semu padahal gagal melakukan generalisasi.

---

## 🚀 Panduan Menjalankan Notebook

### Opsi 1: Google Colab
1. Buka [Google Colab](https://colab.research.google.com/).
2. Pilih tab **Upload** dan unggah file `Praktikum3_GathanHilabi_60324059.ipynb`.
3. Jalankan sel satu per satu menggunakan kombinasi tombol `Shift + Enter` atau klik **Runtime > Run all**.

### Opsi 2: Lingkungan Lokal (Jupyter Notebook / VS Code)
1. Clone repositori ini ke komputer lokal Anda:
   ```bash
   git clone https://github.com/G-than12/DV-03-Data-Processing-with-NumPy-and-Pandas.git
   cd DV-03-Data-Processing-with-NumPy-and-Pandas
   ```
2. Pastikan pustaka yang dibutuhkan sudah terinstal:
   ```bash
   pip install numpy pandas jupyter
   ```
3. Jalankan Jupyter Notebook:
   ```bash
   jupyter notebook Praktikum3_GathanHilabi_60324059.ipynb
   ```

---
*Dibuat untuk memenuhi Tugas Praktikum 2 (Pertemuan 3) - Mata Kuliah Visualisasi Data.*
