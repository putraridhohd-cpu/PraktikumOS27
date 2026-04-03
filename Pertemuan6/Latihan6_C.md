# Laporan Praktikum Sistem Operasi - Latihan 6.C
<img width="871" height="376" alt="53665fc8-ba84-48d3-bfb0-504c795832c2" src="https://github.com/user-attachments/assets/06045276-5477-4496-8b44-98f0e049d4ef" />

## 1. Pengaturan Prioritas Awal (Nice Value)
### Langkah Kerja:
Saya menjalankan dua proses latar belakang dengan nilai prioritas (nice) yang berbeda menggunakan perintah:
```
nice -n 5 sleep 1000 &
nice -n 15 sleep 1001 &
```
Lalu saya memverifikasi hasilnya dengan perintah:
```
ps -o pid,ni,stat,cmd -C sleep
```
<img width="802" height="317" alt="image" src="https://github.com/user-attachments/assets/9a34adeb-d67e-4695-9370-c237411d3a92" />

### Alasan Modifikasi Perintah:
Saya menggunakan opsi -o pid,ni,stat,cmd karena perintah ps standar sering kali tidak menampilkan kolom NI (Nice) secara otomatis. Dengan perintah ini, saya bisa memastikan secara visual bahwa PID 1136 memiliki NI 5 dan PID 1137 memiliki NI 15.


## 2. Mengubah Prioritas dengan renice
### Langkah Kerja:
Saya mengubah prioritas proses pertama (PID 1136) dari 5 menjadi 10 menggunakan perintah:
```
renice -n 10 -p 1136
```
### Hasil Pengamatan:
<img width="702" height="68" alt="image" src="https://github.com/user-attachments/assets/acada344-89ff-4286-ba37-2452c2d7880f" />

Sistem berhasil memperbarui nilai prioritas menjadi 10.
### Analisis Prioritas:
Antara proses dengan NI 10 (PID 1136) dan NI 15 (PID 1137), yang lebih diprioritaskan oleh scheduler adalah proses pertama (PID 1136). Dalam Linux, semakin kecil angka nice-nya, semakin tinggi prioritas CPU yang didapatkan oleh proses tersebut.


## 3. Manipulasi Sinyal (SIGSTOP dan SIGCONT)
### Langkah Kerja:
Saya mengirimkan sinyal penghenti ke PID 1136:
* Menghentikan: ``` kill -SIGSTOP 1136 ```
* Verifikasi: ``` ps -o pid,stat,cmd -p 1136 ``` 
* Melanjutkan: ``` kill -SIGCONT 1136 ```

### Hasil Pengamatan:
<img width="757" height="206" alt="image" src="https://github.com/user-attachments/assets/14fab50d-46ff-4df9-9601-6a16deff6a78" />

Saat diverifikasi setelah SIGSTOP, kolom STAT menunjukkan kode TN. Huruf T berarti Stopped (berhenti) dan N berarti Nice (memiliki prioritas rendah). Setelah SIGCONT dikirim, proses kembali aktif untuk melanjutkan tugasnya di sistem.


## 4. Pembersihan Akhir
### Langkah Kerja:
Terakhir, saya menghentikan semua proses simulasi sekaligus menggunakan perintah:
```
pkill sleep
```
### Hasil:
<img width="729" height="88" alt="image" src="https://github.com/user-attachments/assets/da5256f9-7534-4b35-9ba6-ed0cf95783fd" />

Semua proses sleep yang masih berjalan (termasuk sisa dari latihan sebelumnya) berhasil dihentikan secara massal (Terminated).
