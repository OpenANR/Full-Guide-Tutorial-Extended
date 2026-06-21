# Penggunaan Chown dan Chmod di Linux

_by: Ahmad Nuzulur Rozaq + Gemini AI_

Di sistem operasi Linux (dan keluarga Unix lainnya), keamanan file dan direktori diatur dengan sangat ketat. Dua perintah penting untuk mengelola hak akses ini adalah `chown` dan `chmod`.

Secara sederhana:
- `chown` menentukan **SIAPA** yang memiliki file tersebut.
- `chmod` menentukan **APA** yang bisa dilakukan oleh pemilik, grup dan orang lain terhadap file tersebut.

Berikut adalah penjelasan lengkap untuk keduanya.

## 1. `chown` (Change Owner)

Perintah `chown` digunakan untuk mengubah pemilik (owner) dan grup (group) dari sebuah file atau direktori. Di Linux, setiap file pasti dikaitkan dengan satu _user_ spesifik dan satu _group_ spesifik.

**Sintaks Dasar**
```bash
chown [user_baru]:[grup_baru] nama_file
```

**Contoh Penggunaan**

- **Mengubah pemilik file:** `chown nuzul keterangan.txt` (Membuat user 'nuzul' menjadi pemilik file keterangan.txt)
- **Mengubah pemilik dan grup sekaligus**: `chown nuzul:teknisi instalasi.txt` (Membuat user 'nuzul' dan grup 'teknisi' menjadi pemilik file instalasi.txt)
- **Mengubah seluruh isi folder (Rekursif)**: `chown -R nuzul:teknisi /home/nuzulurrozaq/project` (Parameter `-R` atau rekursif akan mengubah kepemilikan folder `/home/nuzulurrozaq/project/` beserta seluruh file dan sub-folder di dalamnya).

**Catatan**: Mengubah file biasanya memerlukan hak akses superuser (`root` dengan menambahkan perintah `sudo` di awal sendiri).

## 2. `chmod` (Change Mode)

Perintah `chmod` digunakan untuk mengubah hak akses (permission) dari file atau direktori. Hak akses ini dibagi untuk tiga kategori pengguna:

1. **User (u)**: Pemilik file.
2. **Group (g)**: Anggota grup yang memiliki file tersebut.
3. **Other (o)**: Semua orang lain (publik).

Terdapat 3 jenisn hak akses:

- **Read (r)**: Hak untuk membaca isi file atau melihat daftar isi direktori.
- **Write (w)**: Hak untuk memodifikasi/menghapus file atau membuat file baru di dalam direktori.
- **Execute (x)**: Hak untuk menjalankan file sebagai program/script, atau hak untuk masuk (cd) ke dalam direktori.

Ada dua cara untuk menggunakan `chamod` yaitu **Mode Angka (Oktal)** dan **Mode Huruf (Simbolik).**

### A. Mode Angka (Oktal)

Ini adalah cara paling umum dan cepat. Setiap hak akses diwakili oleh angka:

- **Read (r)** = 4
- **Write (w)*** = 2
- **Execute (x)** = 1
- Tidak ada akses = 0

Anda tinggal menjumlahkan angka-angka ini untuk setiap kategori (User, Group, Others).

**Contoh Kombinasi Angka**:
_Read
- 7 (4+2+1) = _Read, Write, Execute_
- 6 (4+2) = _Read, Write_
- 5 (4+1) = _Read, Execute_
- 4 = _Read Saja_

**Contoh Penggunaan `chmod` Angka**:

- `chmod 755 script.sh`
    - Angka 1(`7`): Pemilik bisa `rwx` (baca, tulis, eksekusi).
    - Angka 2(`5`): Grup bisa `rx` (Baca, eksekusi).
    - Angka 3(`5`): Orang lain bisa `rx` (baca, eksekusi).

- `chmod 644 catatan.txt`
    - Pemilik bisa membaca dan menulis (6).. Grup dan orang lain hanya bisa membaca (4). Ini adalah hak akses standar untuk file teks.

- `chmod 777 /path/ke/folder/file`
    - Semua orang bisa melakukan apa saja (baca, tulis, dan eksekusi). Sangat berbahaya dan jarang disarankan untuk file penting.

### B. Mode Huruf (Simbolik)

Mode ini menggunakan huruf untuk menambah (`+`), mengurangi (`-`), atau menetapkan secara pasti (`=`) hak akses.

- Kategori: `u` (user), `g`(group), `o`(others), `a` (all/semua).
- Aksi: `+`(tambah), `-`(kurangi), `=`(set).
- Akses: `r`, `w`, `x`

**Contoh Penggunaan `chmod` Huruf**:

- `chmod u+x script.sh` (Menambahkan hak eksekusi hanya untuk pemilik file).
- `chmod g-w file.txt` (Menghapus hak tulis grup).
- `chmod a=r dokumen.pdf` (Mengatur semua orang-user, group, others-hanya memiliki hak baca).