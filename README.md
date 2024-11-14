# Fitur Login pada Ionic

Tugas pertemuan 8 praktikum pemrograman mobile membuat CRUD Mahasiswa menggunakan ionic.

## Penjelasan Proses CRUD

### 1. Create

 <img src="readme-img/R.png" style="width: 200px">
- Di backend, database menyimpan data pengguna seperti `username` dan `password`.
- Saat pengguna mencoba login, aplikasi Ionic mengirimkan data ini ke server untuk diverifikasi. Jika cocok dengan data di database, server akan mengembalikan `token` sebagai tanda bahwa login berhasil.

### 2. Read

- PHP menangani permintaan login dari aplikasi Ionic melalui endpoint (`login.php`).
- Setelah menerima `username` dan `password`, PHP memvalidasi data terhadap database. Jika valid, PHP mengembalikan respons berisi `status_login` dengan nilai "berhasil" dan `token` untuk autentikasi selanjutnya.
- Jika tidak valid, PHP mengirimkan respons `status_login` "gagal" untuk memberi tahu aplikasi Ionic.

### 3. Update

- Pengguna memasukkan `username` dan `password` pada halaman login.
- Ketika tombol login ditekan, aplikasi memanggil metode `postMethod` pada `AuthenticationService` yang mengirim data login ke server (PHP).
- Jika login berhasil (dengan `status_login` "berhasil"), `token` disimpan dalam aplikasi menggunakan `Capacitor - Preferences`, dan pengguna diarahkan ke halaman `home`.
- Jika login gagal, aplikasi menampilkan pesan kesalahan menggunakan `AlertController`.

### 4. Delete

- `AuthGuard` memastikan hanya pengguna yang sudah login yang bisa mengakses halaman `home`.
- `AutoLoginGuard` mengarahkan pengguna yang sudah login langsung ke `home` tanpa harus login ulang setiap kali membuka aplikasi.
