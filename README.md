# DeployWebsite

# TOPOLOGINYA
![image](https://github.com/user-attachments/assets/38e3dc0d-8e99-47d5-bead-1b1a8a48819a)

# PERSIAPAN KONFIGURASI
   
    - MENYIAPKAN ISO DEBIAN 10/11 ATAU DIATASNYA TERSERAH
    - LAPTOP
    - INSTALASI DEBIAN 10 UNTUK 2 VM
    - JARINGAN UNTUK REPO MIRROR

# LANGKAH PERTAMA
    
    - MENKONFIGURASI JARINGAN PADA DEBIAN 
    - VM1 (WEBSERVER)
        ENP0S3 UNTUK INTERNET (dhcp)
        ENP0S8 SEBAGAI IP STATIC YANG NANTINYA TERHUBUNG DENGAN DATABASE
            address 10.10.10.3/24
            gateway 10.10.10.0
    - Untuk Konfigurasi masuk kedalam nano /etc/network/interfaces

# LANGKAH KEDUA

   - Karena disini saya mementingkan kemudahan dalam menginstall package, saya menggunakan repo mirror
   untuk repo mirror bisa dilihat di https://www.linuxsec.org/2019/08/repository-lokal-debian-buster.html
    - konfigurasinya seperti ini :
        nano /etc/apt/source.list
        masuk kan salah satu repo mirror kedalam nya dan taruh pada bagian bawah sendiri
   ![image](https://github.com/user-attachments/assets/498aaf9c-e247-4581-9527-0f16cbfd48cc)
   - setelah itu lakukan apt update dan upgrade


