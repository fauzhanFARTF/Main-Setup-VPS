# 📦 3. Manajemen Superuser Do (Sudo)

Di sistem operasi Linux/Unix, sudo digunakan untuk menjalankan perintah dengan hak akses administrator (root). Jadi, kalau kamu bukan root user, tapi ingin melakukan tugas yang membutuhkan izin tinggi (seperti install aplikasi, edit file sistem, restart service, dll), kamu bisa pakai sudo : 

Karena:

Linux menjaga sistem tetap aman dengan memisahkan pengguna biasa dan root.
Hanya perintah penting atau sensitif yang membutuhkan izin root.
Dengan sudo, kamu tidak perlu login sebagai root — cukup tambahkan sudo di depan perintah.

```bash
  sudo apt update -y && apt upgrade -y
```

## 💻 Perintah Lengkap

```bash
  fauzhan@srv534216:~# sudo apt update -y && apt upgrade -y
```

## 💻 Penjelasan Perintah : 

- sudo : Jalan pintas untuk menjalankan perintah sebagai root (administrator).

- apt update -y && apt upgrade -y : Perintah ini biasa dijalankan di sistem operasi berbasis Debian/Ubuntu (seperti Ubuntu Server) untuk memperbarui paket perangkat lunak di sistem.

 ## 🔐 Apa yang Terjadi Saat Menggunakan sudo?
Saat kamu menjalankan sudo, biasanya sistem akan:
- Meminta password pengguna kamu (bukan password root).
- Jika kamu termasuk dalam grup sudoers, maka perintah akan dijalankan dengan izin root.
- Setelah berhasil, kamu bisa menjalankan beberapa perintah lain tanpa perlu input password lagi (untuk waktu tertentu, default-nya 15 menit).


## 💻 Proses yang terjadi : 
Saat Anda belum terdaftar hak akses sudo, sistem akan memberitahu bahwa
"fauzhan is not in the sudoers file"

```bash
fauzhan@srv534216:~$ apt update -y && apt upgrade -y

Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)


fauzhan@srv534216:~$ sudo apt update -y && apt upgrade -y

[sudo] password for fauzhan: 
fauzhan is not in the sudoers file.  This incident will be reported.
```
Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/3.1 Not Sudoers.mp4" type="video/mp4">
</video>


 ## 🔐 Cara Menambahkan User ke Grup sudo
Agar user mendapatkan hak akses sudo maka 
Misalnya kamu mau kasih akses sudo ke user bernama fauzhan.

1. ✅ Login sebagai root atau user yang sudah punya akses sudo
      - Keluar dari user yang akan digunakan dari sudo ke root, dengan perintah 
      ```bash
         fauzhan@srv534216:~# exit
      ```
    
      Atau pindah ke user sudo dengan nama 'superuser' menggunakan perintah

      ```bash
         su - <username>
      ```
      
      Contoh :

      ```bash
         fauzhan@srv534216:~# su - superuser
      ```
      
2. ✅ Jalankan perintah berikut:

```bash
root@srv534216:~# usermod -aG sudo fauzhan
```

- usermod = mengubah informasi user.
- -aG = menambahkan user ke grup (append to Group).
- sudo = nama grup yang akan ditambahkan.
- fauzhan = nama user yang ingin kamu beri akses sudo.

Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/3.2 Add User to Sudo.mp4" type="video/mp4">
</video>

## 💻 Verifikasi Groups
Untuk Verifikasi bahwa user sudah masuk ke grup sudo, Kamu bisa cek dengan:
```bash
root@srv534216:~# groups fauzhan
```
Maka Outputnya:

```bash
fauzhan : fauzhan sudo
```
Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/3.3 Verifikasi Grup Sudo.mp4" type="video/mp4">
</video>


## 💻 Test Instalasi
Untuk mengecek apakah hak akses telah berfungsi dengan baik alangkah baiknya kita coba script update paket yang tersedia
```bash
  fauzhan@srv534216:~# sudo apt update
```
Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/3.4 Sudo apt update.mp4" type="video/mp4">
</video>

## 💻 Tips 
Agar kita mendapatkan hak akes penuh ke user root (superuser) maka sudo su adalah pilihan yang tepat

- sudo su adalah gabungan dua perintah yang digunakan untuk berpindah ke user root (superuser) dengan hak akses penuh, walaupun kamu awalnya login sebagai user biasa
.
- Ketika sudah berpindah ke user root, kita tidak perlu menggunakan sudo di awal kata

```bash
fauzhan@srv534216:~$ sudo su


root@srv534216:/home/fauzhan# apt update

Hit:1 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:2 http://in.archive.ubuntu.com/ubuntu jammy InRelease
Hit:3 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:4 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:6 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:7 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:8 http://in.archive.ubuntu.com/ubuntu jammy-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
```
Jika ingin keluar dari user root dengan mengetikan perintah  "exit"

```bash
root@srv534216:/home/fauzhan# exit

exit

fauzhan@srv534216:~$
```

Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/3.5 Apt Update Root.mp4" type="video/mp4">
</video>

