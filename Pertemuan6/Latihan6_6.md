# Laporan Praktikum Sistem Operasi - Latihan 6.6
<img width="907" height="338" alt="image" src="https://github.com/user-attachments/assets/bbd25468-4949-4e7e-b54d-fdafc09a4222" />


## 1. Identifikasi Proses dengan Konsumsi Memori Tertinggi
### Langkah Kerja:
Saya menggunakan perintah ps aux yang diurutkan berdasarkan persentase penggunaan memori (--sort=-%mem) untuk memantau beban sistem.
```
ps aux --sort=-%mem | head -n 5
```
### Hasil Pengamatan:
Berdasarkan output terminal, proses yang menggunakan memori paling banyak adalah:
* Nama Proses: /snap/snapd/current/usr/lib/snapd/snapd (PID 692).
* Penggunaan Memori: Sekitar 1.9%.
* Analisis: snapd adalah layanan latar belakang yang mengelola paket aplikasi Snap di Ubuntu. Proses ini wajar memakan memori lebih banyak karena bertugas menjaga integrasi dan pembaruan aplikasi-aplikasi tersebut.
<img width="1886" height="213" alt="Screenshot 2026-04-03 125650" src="https://github.com/user-attachments/assets/1f6aa742-b608-47b5-ad12-b7cbc502da01" />


## 2. Eksplorasi Visualisasi CPU pada top
### Langkah Kerja:
Saya menjalankan top dan menekan angka 1 sebanyak dua kali.
### Hasil Pengamatan:
<img width="1521" height="920" alt="f8f71faa-782e-4f39-a672-d7c76b5412a1" src="https://github.com/user-attachments/assets/d3cbab7c-da94-427e-8214-81e464c04c7f" />

* Perubahan Tampilan: Baris %Cpu(s) yang awalnya hanya satu baris (gabungan) berubah menjadi beberapa baris terpisah, yaitu %Cpu0 dan %Cpu1.
* Mengapa Informasi Ini Berguna?
Informasi ini sangat krusial untuk mendeteksi adanya ketidakseimbangan beban pada prosesor. Dengan tampilan ini, kita bisa tahu apakah hanya satu core yang bekerja keras sementara yang lain menganggur. Ini membantu admin dalam menganalisis apakah sebuah aplikasi mendukung multi-threading atau jika ada proses yang menyebabkan bottleneck di core tertentu.


## 3. Navigasi Sinyal pada htop
### Langkah Kerja:
Saya menjalankan htop, memilih proses sshd (PID 1058), dan menekan tombol F9.
### Hasil Pengamatan:
<img width="399" height="855" alt="d5f8dc74-8a98-42c9-9964-9e2d6fcb91f8" src="https://github.com/user-attachments/assets/fdeb6f38-bae3-4bd2-9b5a-02084eea4d1e" />

Di sebelah kiri layar muncul panel "Send signal" yang berisi daftar sinyal standar Linux, di antaranya:
* 9 SIGKILL
* 15 SIGTERM
* 19 SIGSTOP
* 18 SIGCONT
* ...dan banyak lagi (total ada sekitar 26+ opsi sinyal).

### Analisis:
Menggunakan htop jauh lebih efisien dan aman bagi admin karena kita bisa melihat daftar sinyal secara visual tanpa perlu menghafal nomor sinyalnya. Memilih PID 1058 (sshd) untuk simulasi menunjukkan bahwa kita bisa mengontrol layanan akses jarak jauh (SSH) langsung dari task manager ini jika terjadi masalah koneksi.

## Kesimpulan Akhir:
Melalui latihan ini, saya belajar bahwa memantau sistem tidak hanya soal melihat angka, tapi juga memahami distribusi beban kerja pada CPU dan memiliki kontrol penuh terhadap sinyal proses melalui tool interaktif seperti htop.
