# Laporan Praktikum Sistem Operasi - Latihan 6.A
<img width="888" height="409" alt="9091557c-8de1-40f8-9008-84bbfd21c9c0" src="https://github.com/user-attachments/assets/1e83b359-179c-42d8-84a6-227c4e402989" />

## 1. Eksplorasi Proses dengan PID 1
### Langkah Kerja:
Saya menggunakan perintah ini untuk langsung mengidentifikasi proses pertama yang dijalankan oleh sistem. Perintah ini sengaja saya modifikasi dari instruksi awal (ps aux -forest) agar hasilnya lebih fokus dan tidak tertumpuk oleh ribuan baris proses lainnya.
```
ps -p 1 -o pid,comm,args
```
### Hasil Pengamatan:
<img width="736" height="92" alt="Screenshot 2026-04-03 132419" src="https://github.com/user-attachments/assets/6601ffa9-dd12-413a-82a7-02b374b74ab4" />

* PID: 1
* COMMAND: systemd (dengan argumen /sbin/init)
### Analisis & Fungsi:
Dalam sistem Linux modern, systemd adalah "bapak" dari semua proses. Ia adalah proses pertama yang dijalankan oleh kernel saat booting dan bertanggung jawab untuk mengelola semua layanan (services) serta proses lainnya hingga sistem siap digunakan. Itulah sebabnya ia selalu memiliki PID 1.


## 2. Perbandingan Jumlah Proses: Root vs User
### Langkah Kerja:
Saya menggunakan perintah ini untuk menghitung jumlah proses secara otomatis agar lebih akurat dibandingkan menghitung manual dari daftar yang panjang:
```
ps -u ridho27 | wc -l
```
dan untuk menghitung proses root: 
```
ps -u root | wc -l
```
### Hasil Pengamatan:
<img width="661" height="68" alt="Screenshot 2026-04-03 132427" src="https://github.com/user-attachments/assets/5842f7c0-61b0-4f09-91ac-afb39ac6a4a3" />
<img width="626" height="100" alt="Screenshot 2026-04-03 133338" src="https://github.com/user-attachments/assets/e736cc5e-e66e-41d3-8d94-548bb2e4c37b" />

* Jumlah Proses User (ridho27): 8 proses.
* Jumlah Proses Root: 100 proses.
### Analisis:
Mengapa Root memiliki lebih banyak proses?
Hal ini dikarenakan Root bertanggung jawab penuh atas seluruh infrastruktur sistem operasi. Sebagian besar proses milik Root adalah background services (daemon) yang bertugas mengelola perangkat keras, jaringan, keamanan, dan memori. Sedangkan proses milik user ridho27 hanya terbatas pada aktivitas yang sedang saya jalankan secara aktif, seperti sesi SSH dan perintah terminal saat ini.


## 3. Analisis Proses dalam Kondisi S (Sleeping)
### Langkah Kerja:
Saya menjalankan perintah ini untuk memfilter semua proses yang berstatus S:
```
ps -eo state,comm | grep "^S"
```
### Hasil Pengamatan:
<img width="1111" height="635" alt="Screenshot 2026-04-03 132606" src="https://github.com/user-attachments/assets/65ee26c7-0be6-47a7-a654-f4107c8129ea" />

Muncul daftar panjang proses seperti systemd, kthreadd, ksoftirqd, dan lain-lain dengan status S.
### Analisis:
Mengapa sebagian besar proses berada dalam kondisi Sleeping?
Ini adalah mekanisme efisiensi dari kernel Linux. Kondisi S (Interruptible Sleep) berarti proses tersebut sedang "beristirahat" menunggu adanya event atau input tertentu (seperti ketukan keyboard, paket jaringan yang masuk, atau timer). Jika semua proses terus-menerus dalam kondisi R (Running), maka CPU akan terbebani 100% secara terus-menerus, yang akan menyebabkan sistem menjadi sangat panas dan boros energi. Dengan mode sleeping, Linux bisa menghemat sumber daya CPU untuk proses yang benar-benar sedang membutuhkan komputasi aktif.
