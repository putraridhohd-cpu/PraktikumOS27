# 5 fungsi utama sistem operasi (Operating System / OS) beserta contoh konkret dari dua OS berbeda: Windows dan Linux (Ubuntu).
## 1. Manajemen Proses (Process Management)
### fungsi:
berfungsi unntuk Mengatur program yang sedang berjalan (process), termasuk membuat, menjalankan, menjeda, dan menghentikan proses.
### contoh:
1. Windows:
Di Windows 11 kamu bisa membuka Task Manager (Ctrl + Shift + Esc) untuk melihat aplikasi yang berjalan seperti Chrome atau Word, lalu mengakhiri proses jika aplikasi tidak merespons.
2. Linux (Ubuntu):
Di Ubuntu kamu bisa menggunakan perintah:
```
ps aux
```
untuk melihat proses yang berjalan:
```
kill <PID>
```
untuk menghentikan proses.

## 2. Manajemen Memori (Memory Management)
### fungsi:
Mengatur penggunaan RAM agar setiap program mendapat memori yang cukup dan tidak saling bertabrakan.
### contoh:
1. Windows:
Di Task Manager → tab Performance, kamu bisa melihat penggunaan RAM secara real-time.
2. Linux (Ubuntu):
Gunakan perintah:
```
free -h
```
atau
```
htop
```
untuk melihat pemakaian RAM dan swap.

## 3. Manajemen Sistem File (File System Management)
### fungsi:
Mengatur penyimpanan data dalam bentuk file dan folder.
### contoh:
1. Windows:
Menggunakan sistem file NTFS, dan kamu mengakses file lewat File Explorer.
2. Linux (Ubuntu):
Menggunakan sistem file seperti ext4, dan kamu mengakses file lewat File Manager atau terminal:
```
ls
cd
mkdir
```
OS mengatur hak akses file (read/write/execute) agar data aman.
## 4.Manajemen Perangkat Keras (Device Management)
### fungsi:
Mengontrol dan menghubungkan perangkat keras seperti keyboard, mouse, printer, hard disk, dan jaringan.
### contoh:
1. Windows:
Menggunakan Device Manager untuk melihat dan mengatur driver perangkat.
2. Linux (Ubuntu):
Bisa menggunakan perintah:
```
lsblk
```
untuk melihat storage, atau:
```
lspci
```
untuk melihat perangkat yang terhubung

## 5. Manajemen Keamanan dan Hak Akses (Security & User Management)
### fungsi:
Mengatur user, password, dan hak akses agar sistem tetap aman.
### contoh:
1. Windows:
Memiliki fitur User Account Control (UAC) yang meminta izin administrator saat menginstal aplikasi.
2. Linux (Ubuntu):
Menggunakan sistem permission (rwx) dan perintah:
```
sudo
```
untuk menjalankan perintah sebagai administrator.

