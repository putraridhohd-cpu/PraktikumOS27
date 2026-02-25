# SIGTERM vs SIGKILL.

## 1. Menjalankan Proses
Perintah berikut digunakan untuk menjalankan proses di background:
```
sleep 600 &
```

Tanda & membuat proses berjalan di background. Sistem menampilkan PID (Process ID) setelah perintah dijalankan.

## 2. Menemukan PID
Untuk melihat PID proses:
```
ps aux | grep sleep
```

PID adalah nomor unik yang digunakan sistem untuk mengidentifikasi proses.

## 3. Menghentikan Proses dengan SIGTERM
Proses dihentikan dengan:
```
kill <PID>
```

Perintah kill secara default mengirim SIGTERM (15) yang menghentikan proses secara normal (graceful).

## 4. Perbedaan SIGTERM dan SIGKILL
* SIGTERM (15) → Menghentikan proses secara normal, memberi kesempatan cleanup.
* SIGKILL (9) → Menghentikan proses secara paksa dan tidak bisa ditangkap oleh program.

Disarankan menggunakan SIGTERM terlebih dahulu sebelum SIGKILL.