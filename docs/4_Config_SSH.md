# 📦 4. Mengedit Konfigurasi SSH di Linux

Untuk mengedit file konfigurasi SSH pada server Linux, kita menggunakan perintah berikut:

```bash
nano /etc/ssh/sshd_config
```
---

## 💻 Perintah Lengkap

```bash
    root@srv534216:~# nano /etc/ssh/sshd_config
```


## 💻 Penjelasan bagian per bagian:

```bash
    root@srv534216:~#
```
- Ini adalah prompt shell yang menunjukkan bahwa perintah dijalankan oleh pengguna root pada server bernama srv534216, dan direktori kerja saat ini adalah home directory (~).

```bash
    nano /etc/ssh/sshd_config
```
- nano: nano adalah editor teks berbasis terminal yang sederhana dan mudah digunakan di Linux. Ini digunakan untuk mengedit file konfigurasi atau file teks lainnya.
- /etc/ssh/sshd_config : Ini adalah file konfigurasi untuk daemon SSH (Secure Shell) pada sistem Linux. File ini mengatur bagaimana server SSH berperilaku, seperti pengaturan autentikasi, akses pengguna, port yang digunakan, dan lain-lain.


## 💻 Pengaturan Umum dalam sshd_config
Berikut adalah beberapa pengaturan yang umum ditemukan dalam file sshd_config:

### 1. Port
Pengaturan ini menentukan port yang digunakan untuk koneksi SSH.
- Secara default, SSH menggunakan port 22. Anda bisa mengubahnya untuk meningkatkan keamanan dengan memilih port lain seperti port 2221

```bash
Port 22
```


### 2. 👤 Opsi `PermitRootLogin` pada SSH
Pengaturan ini mengatur apakah pengguna root dapat login melalui SSH.

```bash
PermitRootLogin yes
```

| Nilai | Penjelasan                                                              |
|-------|-------------------------------------------------------------------------|
| `yes` | Mengizinkan login sebagai **user root** langsung melalui SSH.           |
| `no`  | Menolak login root langsung — **disarankan untuk alasan keamanan**.     |


### 3. 🔐 Opsi `PasswordAuthentication` pada SSH
Mengatur apakah autentikasi dengan password diperbolehkan.

```bash
PasswordAuthentication yes
```

| Nilai | Penjelasan                                                                 |
|-------|----------------------------------------------------------------------------|
| `yes` | Mengizinkan autentikasi menggunakan **password** saat login SSH.           |
| `no`  | Menonaktifkan autentikasi password, hanya mengizinkan metode lain seperti **key-based authentication** (lebih aman). |


### 4. AllowUsers / DenyUsers
Pengaturan ini mengontrol siapa yang diizinkan atau ditolak untuk login melalui SSH.

```bash
AllowUsers user1 user2
```
- Mengizinkan hanya user1 dan user2 untuk login melalui SSH.

```bash
DenyUsers user3
```
- Menolak user3 untuk login.

### 5. MaxAuthTries
Mengatur jumlah percobaan login yang diizinkan sebelum koneksi diputus.

```bash
MaxAuthTries 3
```
- Ini membatasi percobaan login yang gagal untuk meningkatkan keamanan.


## 💻 Cara Kerja

Ketikkan script ini untuk melakukan konfigurasi
```bash
root@srv534216:~# nano /etc/ssh/sshd_config
```

- Masukan port 2221 untuk mengganti port default 22

- <img src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/image/4.1 Port.png" alt="Deskripsi Gambar" width="640">

- Rubah PermitRootLogin dari yes menjadi no (Menolak login root - disarankan untuk keamanan)
- <img src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/image/4.2 PermitRootLogin.png" alt="Deskripsi Gambar" width="640">


Setelah itu lakukan restart system menggunakan

```bash
root@srv534216:~# systemctl restart sshd
```
Dokumentasi : 

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/4.1 Config SSH.mp4" type="video/mp4">
</video>

## 💻 Kesimpulan

Kesimpulan:

File /etc/ssh/sshd_config adalah tempat utama untuk mengonfigurasi server SSH di Linux. Mengedit file ini dengan benar dapat membantu meningkatkan keamanan dan kontrol akses ke server Anda.

