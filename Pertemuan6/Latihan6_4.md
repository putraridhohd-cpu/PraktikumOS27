# Laporan Praktikum Sistem Operasi - Latihan 6.4
<img width="1039" height="340" alt="image" src="https://github.com/user-attachments/assets/2a346b53-0a02-48e2-ad3c-95113988ec8e" />


## 1. Penghentian Sementara Proses dengan SIGSTOP
### Langkah Kerja:
Saya menjalankan proses sleep 1000 di background (PID 1507), lalu mengirimkan sinyal SIGSTOP untuk menghentikan proses tersebut sementara tanpa mematikannya:
```
kill -SIGSTOP 1507
ps aux | grep sleep
```
<img width="1288" height="282" alt="image" src="https://github.com/user-attachments/assets/3f153a45-83f5-46f0-9461-41afb87d7e4f" />

### Hasil Pengamatan:
* Setelah sinyal dikirim, muncul notifikasi Stopped sleep 1000. Pada kolom STAT, status proses berubah menjadi T.
* Analisis: Huruf T kepanjangannya adalah Stopped by job control signal. Ini berarti proses masih ada di memori, namun benar-benar berhenti melakukan aktivitas apa pun sampai ada perintah untuk melanjutkannya.


## 2. Melanjutkan Proses dengan SIGCONT
### Langkah Kerja:
Saya mengirimkan sinyal SIGCONT (Continue) untuk membangunkan kembali proses yang sedang dihentikan sementara tadi:
```
kill -SIGCONT 1507
ps aux | grep sleep
```
<img width="1281" height="115" alt="image" src="https://github.com/user-attachments/assets/d6120215-ea4d-42b4-a293-bcb38c5d9ff7" />

### Hasil Pengamatan:
Pada kolom STAT, status proses kembali berubah dari T menjadi S (Interruptible Sleep). Hal ini membuktikan bahwa proses berhasil melanjutkan tugasnya (menunggu timer) dari titik terakhir ia dihentikan.


## 3. Menghentikan Proses dengan SIGTERM
### Langkah Kerja:
Terakhir, saya mengirimkan sinyal SIGTERM untuk menyudahi proses tersebut secara permanen:
```
kill -SIGTERM 1507
ps aux | grep sleep
```
<img width="1276" height="142" alt="image" src="https://github.com/user-attachments/assets/8f433a8f-7b10-4d8a-84d3-162623613042" />

### Hasil Pengamatan:
Muncul notifikasi Terminated sleep 1000. Saat dicek kembali dengan ps, baris proses dengan PID 1507 sudah benar-benar hilang dari daftar sistem


## Analisis: SIGTERM vs SIGKILL
### Pertanyaan: 
Kapan Anda memilih SIGKILL daripada SIGTERM?
### Jawaban:
Dalam praktikum ini, saya menggunakan SIGTERM (Signal Terminate). Ini adalah cara "sopan" untuk mematikan proses karena memberikan kesempatan pada aplikasi untuk melakukan pembersihan (cleanup), seperti menyimpan data atau menutup koneksi sebelum benar-benar berhenti.
Saya akan memilih SIGKILL (Signal Kill) hanya dalam kondisi darurat, yaitu ketika:

* Sebuah proses macet (stuck/freeze) dan tidak merespons perintah SIGTERM sama sekali.
* Proses tersebut menggunakan sumber daya yang sangat besar dan harus segera dihentikan saat itu juga tanpa menunggu proses pembersihan.

### Perbedaan Utama:

* SIGTERM: Meminta proses berhenti (bisa diabaikan oleh proses yang error).
* SIGKILL: Memaksa sistem operasi untuk langsung mencabut nyawa proses tersebut tanpa toleransi (pasti mati, tapi berisiko menyebabkan data korup jika aplikasi sedang menulis file).
