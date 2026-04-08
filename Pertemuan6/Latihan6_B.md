# Laporan Praktikum Sistem Operasi - Latihan 6.B
<img width="860" height="387" alt="image" src="https://github.com/user-attachments/assets/62df00c0-bebf-49fe-a6fa-49beb7ad3946" />

## 1. Menjalankan Beberapa Job di Background
### Langkah Kerja:
Saya menjalankan tiga perintah sleep dengan durasi yang berbeda di background.
```
sleep 500 &
sleep 600 &
sleep 700 &
jobs
```

### Hasil Pengamatan:
<img width="731" height="324" alt="Screenshot 2026-04-03 165503" src="https://github.com/user-attachments/assets/5810f563-03c7-49dc-8cfe-78403eafb93b" />

Sistem memberikan nomor job [1], [2], dan [3] beserta PID-nya masing-masing. Ketiganya berstatus Running.
* Alasan Perubahan Durasi: Saya memperlama durasi menjadi 500, 600, dan 700 detik (dari instruksi asli 100, 200, 300) agar memiliki waktu yang cukup untuk melakukan manajemen job tanpa terburu-buru oleh proses yang selesai otomatis (Done).


## 2. Manajemen Job (Foreground ke Background)
### Langkah Kerja:
Saya memindahkan job kedua ke depan (foreground), menghentikannya sementara, lalu melemparnya kembali ke belakang (background).
```
fg %2
```
### Hasil Pengamatan:
<img width="589" height="117" alt="image" src="https://github.com/user-attachments/assets/b8913e8d-da86-4aed-b81f-5799846c994b" />

Setelah mengetik kode diatas dan menekan Ctrl+Z, job [2] berubah statusnya menjadi Stopped. Hal ini menunjukkan bahwa proses tersebut masih ada di memori namun tidak sedang menghitung waktu (diam).


## 3. Penghentian Job Spesifik
### Langkah Kerja:
Saya mencoba menghentikan job pertama menggunakan identitas nomor job.
```
kill %1
jobs
```
### Hasil Pengamatan:
<img width="638" height="180" alt="image" src="https://github.com/user-attachments/assets/71e71752-164a-4e80-bd38-03aca336a565" />

Setelah perintah kill %1, job [1] masih muncul di daftar dengan status Running.

* Analisis: Hal ini terjadi karena sinyal kill standar (SIGTERM) memerlukan waktu sepersekian detik untuk memproses penghentian, atau proses tersebut sedang menunggu giliran CPU untuk dieksekusi sinyalnya. Jika ingin memaksa langsung hilang, bisa menggunakan kill -9 %1.
* Job yang Tersisa: Pada pengecekan terakhir, terdapat 3 job yang masih terdaftar di sistem (1 Running, 1 Stopped, 1 Running).

### Analisis Teknis: Mengapa menggunakan % dan Nomor Job?
Dalam laporan ini, saya menggunakan simbol % (seperti %1, %2) untuk merujuk pada nomor job, bukan menggunakan PID (Process ID).
* Alasannya: Menggunakan nomor job jauh lebih praktis dan manusiawi untuk administrasi terminal secara cepat. PID biasanya terdiri dari 4-5 digit angka acak yang sulit dihapal, sedangkan nomor job (1, 2, 3) diberikan secara berurutan oleh shell sehingga meminimalisir kesalahan pengetikan saat ingin mengelola proses tertentu.
