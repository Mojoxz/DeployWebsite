# DeployWebsite

# TOPOLOGINYA
![image](https://github.com/user-attachments/assets/38e3dc0d-8e99-47d5-bead-1b1a8a48819a)

# PERSIAPAN KONFIGURASI
   
    - MENYIAPKAN ISO DEBIAN 10/11 ATAU DIATASNYA TERSERAH
    - LAPTOP
    - INSTALASI DEBIAN 10 UNTUK 2 VM
    - JARINGAN UNTUK REPO MIRROR
    - PADA SAAT INSTALASI PILIH SSH AGAR NANTI TIDAK MENGINSTALL PACAKAGE SSH

# LANGKAH PERTAMA
    
    - MENKONFIGURASI JARINGAN PADA DEBIAN 
    - VM1 (WEBSERVER)
        ENP0S3 UNTUK INTERNET (dhcp)
        ENP0S8 SEBAGAI IP STATIC YANG NANTINYA TERHUBUNG DENGAN DATABASE
            address 10.10.10.3/24
            gateway 10.10.10.0
    - Untuk Konfigurasi masuk kedalam nano /etc/network/interfaces
    - jangan lupa untuk setiap konfigurasi selalu merestart package nya
    - dan jangan lupa untuk konfigurasi ssh ya. (UNTUK KONFIGURASI BANYAK DI BLOGSITE)

# LANGKAH KEDUA

   - Karena disini saya mementingkan kemudahan dalam menginstall package, saya menggunakan repo mirror
   untuk repo mirror bisa dilihat di https://www.linuxsec.org/2019/08/repository-lokal-debian-buster.html
   - konfigurasinya seperti ini :
        nano /etc/apt/source.list
        masuk kan salah satu repo mirror kedalam nya dan taruh pada bagian bawah sendiri
   ![image](https://github.com/user-attachments/assets/498aaf9c-e247-4581-9527-0f16cbfd48cc)
   - setelah itu lakukan apt update dan upgrade

# LANGKAH KETIGA VM 1 (WEBSERVER)

   - karena telah menginstall ssh kita tidak perlu bingung untuk menstransfer file
   - install winscp pada laptop
   - login dengan ip, username dan password anda
   - upload folder web ada ke debian

# LANGKAH KEEMPAT VM 1 (WEBSERVER)

   - dari tempat anda mengupload tadi pindah folder anda kedalam
      - /var/www/folder anda
      - lalu jangan lupa untuk memberikan permission
      - chmod 777 /var/www/folder
      - chown -R www-data:www-data /var/www/folder

# LANGKAH KELIMA VM 1 (WEBSERVER)
   - sebenarnya ada 2 cara untuk mengaktifkan foldernya
   - yang pertama anda bisa membuat conf anda sendiri seperti :
   - nano /etc/apache2/sites-avaible/namafile.conf atau mencopy dari 000-default.conf
   - cp 000-default.conf namafile.conf
   - nantinya rubah folder dalam menjadi seperti foto dibawah ini
   - ![image](https://github.com/user-attachments/assets/cd613691-9d48-4ed2-8972-08d225cd3cd8)
   - jika sudah a2enmod rewrite
   - a2ensite namafile.conf
   - dan restart apache anda.
   - setelah semua selesai jangan lupa merubah file koneksi database anda sesuai dengan yang kalian konfigurasi
   - ![image](https://github.com/user-attachments/assets/31376c03-e0f3-4a9e-b6d5-5621f20f8be6)

# LANGKAH KEENAM VM 1 (WEBSERVER)
   - Pengujian pada laptop client
   - buka di browser sesuai dengan ip yang anda gunakan
   - jika web anda sudah terdapat oprasi if else untuk mengecek database maka akan muncul
   - ![image](https://github.com/user-attachments/assets/8e25e817-dd14-4082-b442-4cf4a714c940)

# LANGKAH KESATU VM 2 (DATABASE)
   
   - untuk langkah pertama ini sama seperti konfigurasi pada vm 1
   - bedanya hanya pada ip
     ENP0S3 UNTUK INTERNET (dhcp)
     ENP0S8 SEBAGAI IP STATIC YANG NANTINYA TERHUBUNG DENGAN DATABASE
            address 10.10.10.4/24
            gateway 10.10.10.0
   - Untuk Konfigurasi masuk kedalam nano /etc/network/interfaces
   - dan jangan lupa untuk restart networknya


# LANGKAH KETIGA VM 2 (DATABASE)

   # install mysql server dan mariadb server
   - apt install mariadb-server mariadb-client -y
   # amankan instalasi
   - mysql_secure_installation
   lalu konfigurasi seperti ini
   - Tekan Enter untuk password root (kosong)
   - Ketik Y untuk mengatur password root
   - Masukkan password baru dan konfirmasi
   - Ketik Y untuk semua pertanyaan berikutnya




