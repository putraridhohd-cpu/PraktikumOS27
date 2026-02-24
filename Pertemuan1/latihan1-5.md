# Eksplorasi sistem yang baru diinstall:
## 1. Tampilkan informasi OS: cat /etc/os-release
![os-release](images/Cat.png)
## 2. Tampilkan versi kernel: uname -r
![uname](images/uname.png)
## 3. List partisi: lsblk
![lsblk](images/LSBLK.png)
## 4. Check network connectivity: ping -c 4 google.com
![ping](images/ping.png)
## 5.  Install dan jalankan htop untuk melihat resource usage
![htop](images/htop.png)
## 6. Buat laporan singkat tentang konfigurasi sistem Anda
Sistem operasi yang digunakan adalah Ubuntu Server 22.04 LTS berdasarkan output perintah cat /etc/os-release. Versi kernel yang digunakan adalah 5.15.x berdasarkan perintah uname -r. Sistem memiliki disk virtual sebesar 25GB yang ditampilkan melalui perintah lsblk. Koneksi jaringan berjalan dengan baik karena perintah ping -c 4 google.com berhasil menerima balasan. Monitoring resource menggunakan htop menunjukkan penggunaan CPU dan RAM dalam kondisi normal.