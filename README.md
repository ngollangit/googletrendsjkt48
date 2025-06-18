# googletrendsjkt48
# Analisis Tren Popularitas Member JKT48 Generasi 12

Proyek ini merupakan alat untuk menganalisis dan memvisualisasikan minat pencarian member JKT48 Generasi 12 menggunakan data dari Google Trends. Tujuannya adalah memberikan gambaran visual mengenai popularitas digital member dalam periode waktu tertentu, dengan perbandingan terhadap satu kata kunci patokan.

## Gambaran Umum

Proyek ini melakukan langkah-langkah berikut:
1.  **Pengambilan Data Member**: Memuat daftar member JKT48 dari file CSV, khusus untuk Generasi 12 (ID 277-293).
2.  **Analisis Google Trends**: Menggunakan pustaka `pytrends` untuk mengambil data minat pencarian dari Google Trends.
    * **Benchmark**: Popularitas setiap member dibandingkan dengan kata kunci **"Freya JKT48"**.
    * **Periode**: Analisis dilakukan dari **18 November 2023** hingga **31 Mei 2025**.
    * **Platform**: Meliputi **Google Search (Web)** dan **YouTube**.
3.  **Penyimpanan Hasil**: Data skor rata-rata popularitas disimpan ke dalam file CSV.
4.  **Visualisasi**: Membuat "Bubble Chart" yang intuitif untuk memvisualisasikan popularitas member, di mana ukuran dan warna gelembung merepresentasikan skor minat pencarian.

## Cara Menjalankan Proyek

Proyek ini dirancang untuk dijalankan dengan mudah di lingkungan **Google Colaboratory (Colab)**, yang sudah terintegrasi dengan Google Drive dan mempermudah instalasi pustaka.

1.  **Akses Google Colab:**
    * Buka [Google Colaboratory](https://colab.research.google.com/).
    * Buat Notebook baru (`File` > `New notebook`).

2.  **Mount Google Drive:**
    * Jalankan kode Python ini di sel pertama Colab Anda untuk menghubungkan ke Google Drive:
        ```python
        from google.colab import drive
        drive.mount('/content/drive', force_remount=True)
        DRIVE_BASE_PATH = '/content/drive/My Drive/Colab Data JKT48/'
        # Opsional: Buat folder jika belum ada
        import os
        if not os.path.exists(DRIVE_BASE_PATH):
            os.makedirs(DRIVE_BASE_PATH)
            print(f"Folder '{DRIVE_BASE_PATH}' telah dibuat.")
        print(f"Path dasar untuk data: {DRIVE_BASE_PATH}")
        ```
    * Ikuti instruksi untuk mengizinkan akses Google Drive Anda.

3.  **Siapkan Struktur Folder & Data Member:**
    * Pastikan ada folder bernama `Colab Data JKT48` di "My Drive" Google Drive Anda.
    * Upload file CSV berisi data member Anda (`jkt48_members_data.csv`) ke dalam folder `Colab Data JKT48` tersebut.
    * File CSV ini **wajib** memiliki kolom `Nama Panggilan JKT48` dan `ID Member`.

4.  **Salin dan Jalankan Kode:**
    * Salin seluruh kode Python dari file notebook proyek ini ke dalam sel-sel di Colab Anda.
    * **Langkah 1: Instalasi Library.** Jalankan sel kode pertama yang berisi perintah `!pip uninstall` dan `!pip install`. Ini akan menyiapkan semua pustaka yang dibutuhkan.
    * **!!! PENTING: SETELAH SEL PERTAMA SELESAI, HARAP RESTART RUNTIME COLAB ANDA !!!**
        * Anda bisa melakukannya lewat menu `Runtime` > `Restart session` (atau `Restart runtime`). Ini krusial agar pustaka yang baru diinstal terload dengan benar.
    * **Langkah 2 - Seterusnya:** Setelah *runtime* di-restart, jalankan sel-sel kode berikutnya secara berurutan dari atas ke bawah. Skrip akan otomatis:
        * Mengimpor pustaka.
        * Memuat data member (akan difilter otomatis untuk ID 277-293).
        * Menginisialisasi `pytrends`.
        * Melakukan analisis tren untuk periode dan platform yang ditentukan.
        * Menyimpan hasil rekap ke file CSV output (`jkt48_trends_REKAP_ID_277-293_Freya_RAW_2023-11-18_to_2025-05-31.csv`).
        * Membuat dan menyimpan visualisasi Bubble Chart (`.png`) di folder yang sama.

## Parameter Kunci (Dapat Disesuaikan dalam Kode)

* `member_id_start`, `member_id_end`: Rentang ID Member JKT48 yang akan dianalisis (default: 277 dan 293).
* `analysis_start_date`, `analysis_end_date`: Periode analisis tren (default: "2023-11-18" dan "2025-05-31").
* `BENCHMARK_KEYWORD`: Kata kunci pembanding untuk analisis tren (default: "Freya JKT48").

## Dependensi

Proyek ini membutuhkan pustaka Python berikut:

* `pandas`
* `pytrends`
* `matplotlib`
* `circlify`
* `numpy`
* `openpyxl`

## Catatan Penting

* **Rate Limit Google Trends**: Google memiliki batasan jumlah permintaan API. Skrip ini sudah dilengkapi dengan mekanisme *retry* dan jeda waktu untuk meminimalkan error (kode 429), namun penggunaan berlebihan dalam waktu singkat tetap bisa memicu pembatasan.
* **Data Relatif**: Skor dari Google Trends bersifat relatif (0-100) terhadap titik tertinggi dalam periode yang dianalisis untuk kata kunci tertentu. Ini mengukur minat pencarian relatif, bukan jumlah pencarian absolut.

---
