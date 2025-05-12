# 📦 4. UFW (Uncomplicated Firewall)

## 💻 Definisi

🔐 Apa itu ufw?
ufw = Uncomplicated Firewall

adalah tool firewall yang digunakan untuk mengelola aturan iptables di Linux (terutama di Ubuntu dan turunannya).

 ## 📋 Fungsi Perintah ufw status
Perintah ini digunakan untuk:

Melihat status firewall dan aturan-aturan yang aktif.

Contoh:

```bash
sudo ufw status 
```
Output-nya bisa seperti ini:

```bash
Status: active
```

| Port/Protokol | Action | From      |
|---------------|--------|-----------|
| 22/tcp        | ALLOW  | Anywhere  |
| 80/tcp        | ALLOW  | Anywhere  |
| 443/tcp       | ALLOW  | Anywhere  |


### 📘 Penjelasan Kolom UFW Status

| Kolom   | Artinya                                                           |
|---------|-------------------------------------------------------------------|
| To      | Port/protokol yang diatur                                         |
| Action  | Apakah koneksi diizinkan (`ALLOW`) atau diblok (`DENY`)          |
| From    | Sumber koneksi (bisa `Anywhere` atau IP tertentu)  


### 📘 Cek status lengkap (dengan nomor port):

```bash
sudo ufw status numbered
```

Contoh output:

```bash
Status: active
```

| No | Port/Protokol | Service | Action | Direction | From      |
|----|---------------|---------|--------|-----------|-----------|
| 1  | 22/tcp        | SSH     | ALLOW  | IN        | Anywhere  |
| 2  | 80/tcp        | HTTP    | ALLOW  | IN        | Anywhere  |


🔄 Kalau ufw belum aktif:
Output-nya mungkin seperti ini:

```bash
Status: inactive
```


## 💻 Cara Megaktifkan Firewall

Aktifkan firewall dengan:

```bash
sudo ufw enable
```

🧯 Nonaktifkan firewall:

```bash
sudo ufw disable

```
## 🔧 Perintah Dasar UFW (Uncomplicated Firewall)

| Perintah               | Fungsi                                             |
|------------------------|----------------------------------------------------|
| `sudo ufw status`      | Lihat status dan aturan firewall yang aktif        |
| `sudo ufw enable`      | Aktifkan firewall                                  |
| `sudo ufw disable`     | Nonaktifkan (matikan) firewall                     |
| `sudo ufw allow 22`    | Izinkan koneksi ke port tertentu (contoh: SSH)     |
| `sudo ufw deny 80`     | Blokir koneksi ke port tertentu (contoh: HTTP)     |

## 💻 Langkah Penggunaan

1. Cek dengan ufw status apakah ufw terpasang
     ```bash
     fauzhan@srv534216:~# sudo ufw status

     atau

     root@srv534216:/home/fauzhan# ufw status 
     ```

     Contoh :

     ```bash
     root@srv534216:/home/fauzhan# ufw status
     Status: inactive
     root@srv534216:/home/fauzhan#
     ```

2. Mengaktifkan ufw 

     ```bash
     fauzhan@srv534216:~# sudo ufw enable

     atau

     root@srv534216:/home/fauzhan# ufw enable 
     ```

     Contoh : 
     
     ```bash
     root@srv534216:/home/fauzhan# ufw enable
     Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
     Firewall is active and enabled on system startup
     root@srv534216:/home/fauzhan# ufw status
     Status: active
     root@srv534216:/home/fauzhan#
     ```

3. Membuka port 2221
     ```bash
     fauzhan@srv534216:~# sudo ufw allow 2221/tcp

     atau

     root@srv534216:/home/fauzhan# ufw allow 2221/tcp 
     ```
    Contoh : 

     ```bash
     root@srv534216:/home/fauzhan# ufw allow 2221/tcp
     Rule added
     Rule added (v6)
     root@srv534216:
     ```
4. Membuka port http
     ```bash
     fauzhan@srv534216:~# sudo ufw allow http

     atau

     root@srv534216:/home/fauzhan# ufw allow http 
     ```

    Contoh : 

     ```bash
     root@srv534216:/home/fauzhan# ufw allow http
     Rule added
     Rule added (v6)
     root@srv534216:
     ```

5. Membuka port https
     ```bash
     fauzhan@srv534216:~# sudo ufw allow https

     atau

     root@srv534216:/home/fauzhan# ufw allow https 
     ```

    Contoh : 

     ```bash
     root@srv534216:/home/fauzhan# ufw allow https
     Rule added
     Rule added (v6)
     root@srv534216:
     ```

5. Cek Status Kembali
    ```bash
     root@srv534216:/home/fauzhan# ufw status
     Status: active

     To                         Action      From
     --                         ------      ----
     2221/tcp                   ALLOW       Anywhere                  
     80/tcp                     ALLOW       Anywhere                  
     443                        ALLOW       Anywhere                  
     2221/tcp (v6)              ALLOW       Anywhere (v6)             
     80/tcp (v6)                ALLOW       Anywhere (v6)             
     443 (v6)                   ALLOW       Anywhere (v6)             

     root@srv534216:/home/fauzhan# 
     ```

- Dokumentasi :

     <!-- <video width="640" height="360" controls>
     <source src="/Users/fauzannurrachman/Sites/Course/VPS/Config/Main Setup VPS/video/5.1 Ufw.mp4" type="video/mp4">
     </video> -->
