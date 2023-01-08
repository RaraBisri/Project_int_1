# Langkah Kerja Peta 1: Performing Table Joins (QGIS3)

Temukan file tl_2019_06_tract.zip di Browser QGIS dan kembangkan. Pilih file tl_2019_06_tract.shp dan seret ke kanvas.

Dialog Select Transformation akan meminta untuk mengkonversi dari EPSG:4269 ke EPSG:4326. Dialog ini menyajikan beberapa transformasi untuk mengkonversi antara koordinat antara proyeksi tersebut. Tinggalkan pilihan ke pilihan default dan klik OK.

Anda akan melihat layer tl_2019_06_tract dimuat di panel Layers. Lapisan ini berisi batas-batas bidang sensus di California. Klik kanan pada layer tl_2019_06_tract dan pilih Open Attribute Table.

Periksa atribut layer. Untuk menggabungkan tabel dengan lapisan ini, kita memerlukan atribut unik dan umum dari setiap fitur. Dalam hal ini, ada 8057 rekaman traktat individual dengan bidang GEOID. Kolom ini dapat menautkan lapisan ini dengan lapisan atau tabel lain yang berisi ID yang sama.

Untuk memuat data tabular, klik Open Data Source Manager.

Dalam dialog Pengelola Sumber Data, pilih Teks yang Dibatasi. Kemudian di sebelah kanan, klik ... di sebelah Nama file dan ramban ke folder yang tidak di-zip dengan CSV populasi California.

Sekarang di bawah Data Sampel, kita dapat memeriksa data bahkan sebelum memuatnya sebagai lapisan. Representasi menunjukkan bahwa tabel data berisi 2 baris header.

Untuk menghilangkan baris tajuk tambahan, di bawah Opsi Rekam dan Bidang atur Jumlah baris tajuk untuk dibuang ke 1. Sekarang tabel akan berisi tajuk kolom yang tepat. Karena lapisan ini hanya berisi data tabular, pilih Tanpa geometri (tabel hanya atribut) di bawah Definisi Geometri. Klik Add untuk menambahkannya sebagai layer dan kemudian klik Close untuk menutup kotak dialog ini.

CSV sekarang akan diimpor sebagai tabel ke QGIS dan muncul sebagai ACST5Y2019.S0101 di panel Lapisan. Sekarang klik kanan pada layer dan pilih Open Attribute Table.

Kolom ID berisi id unik untuk setiap record, yang dapat digunakan untuk menggabungkan tabel ini dengan layer tl_2019_06_tract. Jika Anda membandingkan nilai ID dengan kolom GEOID dari tl_2019_06_tract. Anda akan melihat bahwa itu diawali dengan 1400000US. Untuk menggabungkan kedua tabel ini dengan sukses, nilainya harus sama persis. Mari hapus awalan ini dan tambahkan kolom baru dengan 11 karakter terakhir yang berisi nilai yang sama persis.

Untuk membuat kolom baru dengan 11 digit terakhir, buka Processing Toolbox dengan masuk ke Processing ‣ Toolbox, dan cari dan temukan tabel Vector ‣ Algoritma kalkulator lapangan.

Dalam dialog Kalkulator bidang, pilih ACST5Y2019.S0101 sebagai lapisan Input, masukkan geoid di Nama bidang, dan pilih string di Jenis Bidang Hasil. Sekarang cari substr dalam ekspresi. Kita dapat menggunakan fungsi ini untuk mengekstrak bagian yang diperlukan dari kolom id.

Masukkan ekspresi di bawah ini. Kami menggunakan fungsi substr dan mengekstrak nilai dari posisi -11 (nilai negatif dihitung dari akhir). Hasil akhir dapat dilihat di bagian Pratinjau. Klik Jalankan.
 
