# Laporan Praktikum Sistem Operasi - Latihan 6.5
<img width="914" height="382" alt="image" src="https://github.com/user-attachments/assets/e73bf87d-a9f6-4bbe-9616-1e66bbdc8e9a" />


## 1. Menjalankan top di Foreground
### Langkah Kerja:
Saya menjalankan perintah top secara normal di terminal:
```
top
```
### Hasil Pengamatan:
Terminal langsung menampilkan tabel daftar proses sistem secara real-time. Selama top berjalan di foreground, terminal terkunci dan saya tidak bisa mengetikkan perintah Linux lainnya karena top menguasai input/output terminal tersebut.
<img width="1864" height="1058" alt="image" src="https://github.com/user-attachments/assets/f643a491-27fb-4191-ac26-beed246b3399" />


## 2. Menghentikan Sementara dengan Ctrl + Z
### Langkah Kerja:
Saya menekan kombinasi tombol Ctrl + Z untuk menghentikan proses sementara.
### Hasil Pengamatan:
Muncul pesan [1]+ Stopped top. Saat saya cek dengan perintah jobs, statusnya adalah Stopped. Ini berarti proses top masih ada di memori, tetapi "dibekukan" dan tidak lagi memperbarui data di layar.
<img width="1286" height="198" alt="image" src="https://github.com/user-attachments/assets/cb2fd268-e14d-47a0-9462-89ff4cc5d32e" />


## 3. Memindahkan ke Background dengan bg
### Langkah Kerja:
Saya mencoba memindahkan proses top agar berjalan di belakang layar dengan perintah:
```
bg
```
### Hasil Pengamatan:
Muncul pesan [1]+ top &, namun sesaat kemudian langsung muncul kembali pesan Stopped top.
<img width="552" height="165" alt="image" src="https://github.com/user-attachments/assets/3189f2f7-cf86-409f-89df-97428e0fc8e8" />
### Analisis (Mengapa top tidak bisa jalan di background?):
Program top adalah aplikasi interaktif yang memerlukan akses ke Standard Output (layar) untuk menampilkan data secara terus-menerus. Di Linux, program interaktif seperti ini tidak bisa berjalan di background. Begitu dipindah ke belakang, sistem akan mengirimkan sinyal SIGTTOU (untuk menghentikannya) karena program tersebut mencoba menulis data ke terminal yang sedang digunakan oleh shell. Itulah kenapa statusnya kembali menjadi Stopped.


## 4. Mengembalikan ke Foreground dengan fg
Langkah Kerja:
Saya mengetikkan perintah ini untuk membawa kembali proses ke depan:
```
fg
```
### Hasil Pengamatan:
Terminal kembali menampilkan antarmuka top seperti semula. Saya kemudian keluar dari program dengan menekan tombol q.
<img width="1334" height="630" alt="image" src="https://github.com/user-attachments/assets/0a0d5969-27db-422c-ae61-482fef6d85cf" />

### Kesimpulan:
Perintah fg (foreground) berfungsi untuk mengambil alih kembali kendali terminal oleh proses yang sebelumnya dihentikan atau ditaruh di background. Karena top memang didesain untuk berjalan di depan, ia langsung aktif kembali secara normal.
