# PERINTAH ZIP DAN UNZIP

_by : Ahmad Nuzulur Rozaq + Gemini AI_

![Pengelola ZIP dan UNZIP](images/perintah_zip_dan_unzip.jpg)

Utilitas `zip` dan `unzip` di Linux merupakan program yang berjalan di terminal yang memiliki fungsi memanajemen file arsip. `zip` merupakan utilitas yang memiliki fungsi seperti menggabungkan beberapa file atau lebih hingga menjadi satu. Kemudian `unzip` merupakan utilitas yang digunakan untuk mengekstrak file `.zip`.

Dibawah ini perintah lengkap cara menggunakan `zip` dan `unzip` beserta penjelasan flag nya secara umum.

## UTILITAS ZIP (Pengarsip File)

Contoh penggunaan dasar di terminal :
```bash
zip [opsi_flag] nama_file.zip
```
### 1. Penjelasan Flag

| **Flag**         | **Fungsi**                                                                                                                                                                               | **Contoh Penggunaan**                           |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| `-r`             | **Recursive**: Digunakan untuk mengompresi sebuah direktori (folder) beserta seluruh isi di dalamnya secara  rekursif.                                                                   | `zip -r nama_file.zip /folder/data/`            |
| `-e`             | **Encrypt**: Menambahkan enkripsi password ke dalam file zip. Saat dijalankan, terminal akan meminta Anda untuk memasukkan kata sandi.                                                   | `zip -e nama_file.zip /folder/data/`            |
| `-q`             | **Quiet**: Berjalan di latar belakang tanpa menampilkan output proses (log) di layar terminal.                                                                                           | `zip -q nama_file.zip /folder/data/`            |
| `-v`             | **Verbose**: Menampilkan proses kompresi secara sangat detail berupa log.                                                                                                                | `zip -v nama_file.zip /folder/data/`            |
| `-m`             | **Move**: Memindahkan file. Setelah file berhasil dimasukkan ke dalam arsip zip, maka folder dan file yang berasal dari sumber aslinya akan langsung di hapus.                           | `zip -m nama_file.zip /folder/data/`            |
| `-u`             | **Update**: Memperbarui file zip yang sudah ada hanya dengan file yang baru dimodifikasi atau file baru, tanpa mengompresi ulang file yang tidak berubah.                                | `zip -u nama_file.zip file_baru.txt`            |
| `-d`             | **Delete**: Menghapus file tertentu dari dalam arsip zip tanpa perlu mengekstraknya terlebih dahulu.                                                                                     | `zip -d nama_file.zip file_salah.txt`           |
| `-0` hingga `-9` | **Compression Level**: Mengatur tingkat kompresi. `-0` berarti  hanya menyimpan (tanpa kompresi). Sedangkan `-9` adalah kompresi maksimal (ukuran file kecil, tetapi proses lebih lama). | `zip -9 nama_file.zip video.mp4`                |

### 2. Penjelasan Compression Level

- Penggunaan utilitas `zip` dengan kombinasi **Compression Level**, berikut perintah terminal nya.
```bash
# 1. Menggunakan level 0 (Menggabungkan file tanpa kompresi)
zip -0 nama_file.zip contoh_file.pdf

# 2. Menggunakan level 1 (Kompresi file paling cepat)
zip -1 nama_file.zip contoh_file.pdf

# 3. Menggunakan level 9 sekaligus menggabungkan banyak file secara rekursif
zip -9 -r nama_file.zip /folder/file/
```

- Dibawah ini merupakan penjelasan tiap angka flag yang dimiliki oleh utilitas `zip`.

| **Level**        | **Kategori**                | **Penjelasan**                                                                                                                                                                                                                                                 |
|------------------|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-0`             | **Store Only** (Tanpa Kompresi) | File hanya dibungkus ke dalam format `.zip` tanpa kompresi sama sekali. Proses nya sangat cepat, akan tetapi ukuran file sama persis dengan total ukuran file aslinya.                                                                                         |
| `-1`             | **Fastest** (Paling Cepat)      | Memberikan kompresi paling cepat namun rasio kompresi paling rendah. Ukuran file hasil kompresi masih relatif besar.                                                                                                                                           |
| `-2` hingga `-5` | **Intermediate** (Menengah)     | Tingkat kompresi bertahap yang perlahan meningkatkan rasio kompresi dan mengurangi kecepatan.                                                                                                                                                                  |
| `6`              | **Default** (Standar)           | Ini adalah level yang digunkan `zip` secara otomatis jika Anda tidak memasukkan flag angka sama sekali. Level `-6` diracang untuk memberikan keseimbangan yang paling optimal antara kecepatan kompresi yang wajar dan pengurangan ukuran file yang memuaskan. |
| `-7` dan `-8`    | **High** (Tinggi)               | Memberikan kompresi yang lebih padat daripada pengaturan default. Proses pembuatan arsip akan terasa lebih lambat, tetapi ukuran file akhir akan lebih kecil.                                                                                                  |
| `-9`             | **Maximum / Best** (Maksimsal)  | Tingkat kompresi tertinggi yang bisa dilakukan oleh format zip. Menghasilkan ukuran file paling kecil, namun proses nya sangat lama dan memakan sedikit lebih banyak sumber daya CPU.                                                                          |


## UTILITAS UNZIP (Pengekstrak File)

Contoh penggunaan dasar di terminal :
```bash
unzip [opsi_flag] nama_file.zip
```

### Penjelasan Flag

| **Flag** | **Fungsi / Penjelasan**                                                                                                                                 | **Contoh Penggunaan**                    |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| `-d`     | **Directory**: Mengekstrak isi file zip ke direktori (folder) tujuan yang spesifik, bukan di direktori saat ini.                                        | `unzip nama_file.zip -d /tujuan/folder/` |
| `-l`     | **List**: Hanya menampilkan daftar file yang ada di dalam arsip zip tanpa mengekstraknya.                                                               | `unzip -l nama_file.zip`                 |
| `t`      | **Test**: Menguji integritas file zip untuk memastikan tidak ada file yang _corrupt_ (rusak) atau error sebelum di ekstrak.                             | `unzip -t nama_file.zip`                 |
| `-o`     | **Overwrite**: Jika ada file dengan nama yang sama di direktori tujuan, file tersebuut akan langsung ditimpa (di-overwrite) tanpa konfirmasi.           | `unzip -o nama_file.zip`                 |
| `-n`     | **Never Overwrite**: Mengekstrak file, tetapi akan melewati (tidak menimpa) file yang sudah ada di direktori tujuan.                                    | `unzip -n nama_file.zip`                 |
| `-q`     | **Quiet**: Melakukan ekstrasi secara diam-diam tanpa menampilkan daftar file yang sedang di ekstrak di layar terminal.                                  | `unzip -q nama_file.zip`                 |
| `-P`     | **Password**: Digunakan untuk memasukkan kata sandi secara langsung melalui command line. (Tidak Disarankan karena akan tersimpan di history terminal). | `unzip -P katasandi nama_file.zip`       |