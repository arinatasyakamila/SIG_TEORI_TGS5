# SIG_TEORI_TGS5
 calculating line lengths and statistics
# Langkah Kerja :

1. Temukan file ne_10m_railroads_north_america.zip yang diunduh di panel Browser dan perluas. Seret file ne_10m_railroads_north_america.shp ke kanvas.

2. Anda akan melihat layer baru ne_10m_railroads_north_america dimuat di panel Layers. Anda akan melihat bahwa lapisan tersebut memiliki garis yang mewakili jalur kereta api untuk seluruh Amerika Utara. Sekarang, mari kita hitung panjang setiap fitur garis. Buka Pemrosesan Kotak Alat.

3. Cari dan temukan geometri Vektor Tambahkan algoritma atribut geometri. Klik dua kali untuk meluncurkannya.

4. Dalam dialog Add Geometry Attributes, pilih ne_10m_railroads_north_america sebagai lapisan Input. Sistem Referensi Koordinat (CRS) lapisan input adalah EPSG:4326 WGS84. Ini adalah CRS Geografis dengan Latitude dan Longitude sebagai koordinat, WGS84 sebagai ellipsoid dan derajat sebagai unit. Karena lintang dan bujur tidak memiliki panjang standar, Anda tidak dapat mengukur jarak atau area secara akurat menggunakan fungsi geometri planar. Untungnya, QGIS menyediakan cara yang lebih baik untuk menghitung jarak menggunakan geometri ellipsoidal, yang merupakan metode paling akurat untuk lapisan yang mencakup area yang luas seperti ini. Pilih Ellipsoidal sebagai opsi Hitung menggunakan. Klik Jalankan. Setelah proses selesai, klik Tutup.

5. Anda akan melihat layer baru Added geom info dimuat di panel Layers. Ini adalah salinan dari lapisan input dengan kolom baru yang ditambahkan untuk jarak. Klik kanan layer Added geom info dan pilih Open Attribute Table.

6. Di Tabel Atribut, Anda akan melihat kolom baru yang disebut jarak. Ini berisi panjang setiap fitur garis dalam meter. Perhatikan juga bahwa atribut sov_a3 yang berisi kode negara untuk setiap fitur. Tutup jendela Tabel Atribut.

7. Sekarang kita memiliki panjang masing-masing segmen jalur kereta api, kita dapat menjumlahkannya untuk menemukan panjang total jalur kereta api. Tetapi karena pernyataan masalah menuntut kita membutuhkan total panjang rel di Amerika Serikat, kita harus menggunakan hanya segmen yang ada di Amerika Serikat. Kita dapat menggunakan nilai kode negara di kolom sov_a3 untuk memfilter layer. Klik kanan layer Added geom info dan pilih Filter.

8. Dalam dialog Query Builder, masukkan ekspresi berikut dan klik OK. "sov_a3" = 'USA'

9. Anda akan melihat ikon Filter muncul di sebelah lapisan Info geom yang ditambahkan di panel Lapisan yang menunjukkan bahwa filter diterapkan ke lapisan. Anda juga dapat mengonfirmasi secara visual bahwa lapisan sekarang berisi segmen garis hanya untuk Amerika Serikat. Sekarang kita siap untuk menghitung jumlahnya. Klik tombol Tampilkan ringkasan statistik di Bilah Alat Atribut.

10. Panel Statistik baru akan terbuka. Pilih Lapisan info geom yang ditambahkan dan kolom panjang.

11. Anda akan melihat berbagai statistik ditampilkan di panel. Satuan statistik sama dengan satuan panjang kolom - meter. Mari kita ubah perhitungan untuk menggunakan kilometer sebagai gantinya. Klik ikon Ekspresi di sebelah menu tarik-turun bidang di panel Statistik.

12. Masukkan ekspresi berikut dalam Dialog Ekspresi yang mengubah panjang menjadi kilometer. length / 1000

13. Nilai Sum yang ditampilkan adalah total panjang rel di Amerika Serikat.
