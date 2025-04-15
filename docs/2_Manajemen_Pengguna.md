# 📦 2. Manajemen Pengguna Baru

Untuk menambahkan pengguna baru di sistem Linux, Anda bisa menggunakan perintah:

```bash
adduser fauzhan
```

## 💻 Perintah Lengkap

```bash
    root@srv534216:~# adduser fauzhan
```

## 💻 Penjelasan Perintah : 

- adduser : Perintah yang digunakan untuk membuat akun pengguna baru. Ini adalah versi yang lebih ramah dari useradd karena secara otomatis membuat home directory, mengatur password, dan menjalankan proses konfigurasi interaktif.

- fauzhan : Nama pengguna (username) baru yang ingin ditambahkan ke sistem.

## 💻 Proses yang terjadi : 
Saat Anda menjalankan perintah ini, sistem akan:

#### 1. Membuat Direktori
```bash
home: /home/fauzhan
```

#### 2. Menanyakan password untuk pengguna baru

Meminta informasi tambahan (yang bisa dikosongkan):

- Full Name
- Room Number
- Work Phone
- Home Phone
- Other

#### 3. Menambahkan pengguna ke grup default

#### 4. Mengatur shell default (/bin/bash)

Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/2.1 Manajemen Pengguna.mp4" type="video/mp4">
  Browser kamu nggak support tag video.
</video>

## 💻 Masuk ke pengguna baru:
Untuk Masuk ke pengguna baru dari root. Kita dapat megetikkan perintah

```bash
su - <username>
```
contoh
```bash
su - fauzhan
```
Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/2.2 Masuk ke Pengguna.mp4" type="video/mp4">
</video>

## 💻 Tips Tambahan
Untuk menambahkan pengguna ke grup tertentu (misalnya sudo), gunakan:
```bash
usermod -aG sudo fauzhan
```
Untuk menghapus pengguna:

```bash
deluser fauzhan
```


