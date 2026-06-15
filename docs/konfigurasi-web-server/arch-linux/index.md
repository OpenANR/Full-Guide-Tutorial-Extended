# Panduan Web Server di Arch Linux
_Langkah-langkah setup lingkungan pengembangan web di sistem Arch Linux._

Bagian ini menyediakan tutorial terperinci tentang cara menginstal dan mengkonfigurasi komponen web server stack di distribusi Arch Linux secara mandiri.

## Langkah Setup Web Server

Silakan ikuti urutan instalasi di bawah ini untuk membangun stack web server Anda:

1.  **[Instalasi MariaDB (Database)](install-mariadb.md)**
    Panduan menginstal paket MariaDB, inisialisasi direktori data database, melakukan setup keamanan melalui `mysql_secure_installation`, serta membuat pengguna database baru.
2.  **[Instalasi PHP](install-php.md)**
    Panduan cara mengunduh PHP dan mengaktifkan extension yang diperlukan (seperti PDO, cURL, GD, ZIP) agar kompatibel dengan framework modern seperti Laravel.
3.  **[Instalasi phpMyAdmin](install-phpmyadmin.md)**
    Panduan instalasi phpMyAdmin untuk mengelola database secara visual melalui antarmuka web, mengkonfigurasi *blowfish secret*, setup folder sementara, serta memecahkan pesan peringatan (warning) umum.
