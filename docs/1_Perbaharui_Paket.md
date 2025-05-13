# 📦 1. Perbaharui Paket

Perintah 

```bash
apt update -y && apt upgrade -y
```

Perintah ini biasa dijalankan di sistem operasi berbasis Debian/Ubuntu (seperti Ubuntu Server) untuk memperbarui paket perangkat lunak di sistem. Berikut penjelasan bagian per bagiannya:

---

## 💻 Perintah Lengkap

root@srv534216:~# apt update -y && apt upgrade -y


## 💻 Penjelasan bagian per bagian:

root@srv534216:~#

Ini adalah prompt shell yang menunjukkan bahwa perintah dijalankan oleh pengguna root pada server bernama srv534216, dan direktori kerja saat ini adalah home directory (~).

apt update -y && apt upgrade -y

1. apt: apt adalah alat baris perintah untuk mengelola paket di sistem berbasis Debian/Ubuntu. Ini digunakan untuk menginstal, menghapus, memperbarui, dan mengelola paket perangkat lunak.
2. update : update akan mengambil informasi terbaru dari repositori paket. Artinya, sistem akan mengecek apakah ada versi baru dari paket yang tersedia.
3. -y : Opsi -y berarti jawab "yes" secara otomatis untuk semua konfirmasi, jadi pembaruan akan berjalan tanpa menunggu input pengguna.
4. && : Ini adalah operator logika di shell Linux. Artinya: jalankan perintah berikutnya hanya jika perintah sebelumnya berhasil. Jadi jika apt update berhasil, maka apt upgrade akan dijalankan.
5. upgrade : upgrade digunakan untuk memasang pembaruan paket yang tersedia di sistem

## 💻 Kesimpulan

Kesimpulan:
Perintah ini akan:

Mengecek daftar paket terbaru dari repositori (apt update).

Jika berhasil, langsung melanjutkan untuk memperbarui semua paket yang sudah diinstal ke versi terbaru yang tersedia (apt upgrade), tanpa meminta konfirmasi (-y).

Kalau kamu butuh versi yang lebih aman, biasanya orang juga menambahkan:
```bash
apt update && apt full-upgrade -y
```
Atau sebelum update:

```bash
apt update && apt list --upgradable
```

## 💻 Processing
Dokumentasi :

<video width="640" height="360" controls>
  <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/1.1 Perbaharui Paket.mp4" type="video/mp4">
</video>

```bash
root@srv534216:~# apt update -y && apt upgrade -y

Hit:1 http://in.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease [128 kB]
Hit:3 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu jammy InRelease   
Get:5 http://archive.ubuntu.com/ubuntu jammy-security InRelease [129 kB]
Hit:6 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
Get:7 http://in.archive.ubuntu.com/ubuntu jammy-security InRelease [129 kB]
Get:8 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [128 kB]
Fetched 514 kB in 2s (245 kB/s)  
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  cloud-init
The following packages will be upgraded:
  linux-base pci.ids qemu-guest-agent
3 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 521 kB of archives.
After this operation, 96.3 kB of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 qemu-guest-agent amd64 1:6.2+dfsg-2ubuntu6.26 [251 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 pci.ids all 0.0~2022.01.22-1ubuntu0.1 [251 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-base all 4.5ubuntu9+22.04.1 [19.1 kB]
Fetched 521 kB in 2s (327 kB/s)      
Preconfiguring packages ...
(Reading database ... 94144 files and directories currently installed.)
Preparing to unpack .../qemu-guest-agent_1%3a6.2+dfsg-2ubuntu6.26_amd64.deb ...
Unpacking qemu-guest-agent (1:6.2+dfsg-2ubuntu6.26) over (1:6.2+dfsg-2ubuntu6.25) ...
Preparing to unpack .../pci.ids_0.0~2022.01.22-1ubuntu0.1_all.deb ...
Unpacking pci.ids (0.0~2022.01.22-1ubuntu0.1) over (0.0~2022.01.22-1) ...
Preparing to unpack .../linux-base_4.5ubuntu9+22.04.1_all.deb ...
Unpacking linux-base (4.5ubuntu9+22.04.1) over (4.5ubuntu9) ...
Setting up pci.ids (0.0~2022.01.22-1ubuntu0.1) ...
Setting up linux-base (4.5ubuntu9+22.04.1) ...
Setting up qemu-guest-agent (1:6.2+dfsg-2ubuntu6.26) ...
Processing triggers for man-db (2.10.2-1) ...
Scanning processes...                                                                                                                                                            
Scanning candidates...                                                                                                                                                           
Scanning linux images...                                                                                                                                                         

Restarting services...
 systemctl restart polkit.service
Service restarts being deferred:
 /etc/needrestart/restart.d/dbus.service
 systemctl restart networkd-dispatcher.service
 systemctl restart unattended-upgrades.service

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.

root@srv534216:~# 
```