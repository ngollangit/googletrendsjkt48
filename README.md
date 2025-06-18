# googletrendsjkt48
Analisis Tren Popularitas Member JKT48 Generasi 12
Selamat datang di repositori ini! Proyek ini bertujuan untuk menganalisis dan memvisualisasikan popularitas member JKT48 Generasi 12 berdasarkan data minat pencarian dari Google Trends. Dengan menggunakan benchmark yang spesifik, kita bisa mendapatkan gambaran yang lebih detail tentang siapa saja member yang sedang menarik perhatian publik di platform Google Search dan YouTube.

Tujuan Proyek
Mengidentifikasi tren popularitas member JKT48 Generasi 12 dalam periode tertentu.
Membandingkan minat pencarian masing-masing member relatif terhadap satu kata kunci patokan.
Menyediakan visualisasi data yang intuitif (Bubble Chart) untuk memudahkan pemahaman.
Mendokumentasikan proses pengambilan data menggunakan API Google Trends melalui pytrends.
Metodologi
Proyek ini menggunakan pendekatan berbasis data untuk mengukur popularitas:

Sumber Data Member: Data nama panggilan dan ID member JKT48 diambil dari file CSV (jkt48_members_data.csv).
Rentang Member Terpilih: Analisis difokuskan pada member dengan ID Member antara 277 hingga 293, yang secara spesifik merupakan anggota JKT48 Generasi 12.
Periode Analisis: Data tren dikumpulkan untuk periode dari 18 November 2023 hingga 31 Mei 2025.
Kata Kunci Patokan (Benchmark): Minat pencarian setiap member dibandingkan dengan kata kunci "Freya JKT48". Pemilihan Freya sebagai benchmark dilakukan untuk mendapatkan skala perbandingan yang lebih granular dan relevan di antara member-member JKT48.
Platform Pencarian: Analisis dilakukan untuk dua properti Google: Google Search (Web) dan YouTube.
Pengambilan Data Otomatis: Pustaka pytrends digunakan untuk berinteraksi dengan Google Trends API secara otomatis, termasuk implementasi mekanisme retry dan jeda waktu untuk menghindari batasan rate limit.
Hasil Analisis
Setelah proses pengambilan data selesai, proyek ini akan menghasilkan:

File CSV Rekapitulasi: Sebuah file CSV (.csv) yang berisi ringkasan skor rata-rata minat pencarian untuk setiap member (dibandingkan dengan benchmark) di kedua platform (Web dan YouTube). File ini akan disimpan dengan nama yang mencerminkan rentang ID member dan periode analisis.
Visualisasi Bubble Chart: Dua buah gambar Bubble Chart (.png), satu untuk Google Search (Web) dan satu untuk YouTube.
Setiap gelembung merepresentasikan satu member JKT48 Generasi 12.
Ukuran gelembung proporsional dengan skor rata-rata minat pencarian member tersebut (semakin besar, semakin tinggi minatnya).
Warna gelembung juga menunjukkan skor minat (misalnya, gradasi dari ungu untuk skor rendah ke kuning untuk skor tinggi).
Nama member dan skornya ditampilkan di dalam gelembung (tergantung ukuran gelembung).
Cara Menjalankan Proyek
Untuk menjalankan analisis ini, Anda dapat menggunakan Google Colaboratory (Colab) karena sudah terintegrasi dengan Google Drive dan mudah dalam instalasi dependensi.

Siapkan Google Colab:
Buka notebook Colab baru.
Pastikan Anda login dengan akun Google Anda.
Hubungkan ke Google Drive Anda (drive.mount('/content/drive')).
Pastikan folder Colab Data JKT48 ada di "My Drive" atau sesuaikan DRIVE_BASE_PATH dalam skrip.
Siapkan Data Member:
Pastikan Anda memiliki file jkt48_members_data.csv di folder Colab Data JKT48 (atau di path yang ditentukan).
File ini wajib memiliki kolom bernama Nama Panggilan JKT48 dan ID Member.
Salin Kode:
Salin seluruh kode dari file notebook (.ipynb) atau langsung dari repositori ini ke dalam sel-sel di Colab Anda.
Jalankan Secara Berurutan:
Sel 1 (Setup Awal): Jalankan sel pertama untuk menginstal dan memperbarui semua pustaka yang diperlukan. PENTING: Setelah ini, RESTART RUNTIME Colab Anda (Menu Runtime -> Restart session).
Sel-sel Berikutnya: Setelah runtime di-restart, jalankan sel-sel berikutnya secara berurutan. Skrip akan secara otomatis memuat data, melakukan analisis, dan menghasilkan output CSV serta grafik.
Dependensi
Proyek ini menggunakan pustaka Python berikut:

pandas
pytrends
matplotlib
circlify
numpy
openpyxl (untuk membaca/menulis Excel, meskipun dalam skrip ini lebih fokus ke CSV)
Catatan Penting
Rate Limit Google Trends: Google Trends memiliki batasan jumlah permintaan. Skrip ini sudah dilengkapi dengan mekanisme retry dan jeda waktu untuk meminimalkan error TooManyRequestsError (429). Namun, jika Anda menjalankan berulang kali dalam waktu singkat, Anda mungkin tetap akan menghadapi batasan ini.
Akurasi Data: Data dari Google Trends bersifat terindeks dan relatif. Ini adalah indikator minat pencarian, bukan jumlah pencarian absolut.
