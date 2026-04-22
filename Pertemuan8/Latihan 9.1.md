# Praktikum 7.1 Script Pertama: Laporan Sistem

## Persiapan Direktori
Saya membuat folder kerja baru secara terorganisir menggunakan perintah ``` mkdir -p ``` untuk memisahkan antara file script, log, dan data di dalam folder week09.

## Pembuatan Script
buat script nya pake editor nano,lalu buat file bernama laporan-sistem.sh

<img width="1877" height="1120" alt="image" src="https://github.com/user-attachments/assets/11f51476-e32d-4c22-8ccb-77accbfff4ba" />

## Logika Script
* Menggunakan variabel nama file untuk menyimpan nama file laporan dengan format dinamis mengikuti tanggal saat ini (rabu 4 april 2026)
* Menggunakan perintah echo yang dikelompokkan untuk menampilkan informasi sistem.
* Informasi RAM dan Disk diambil menggunakan bantuan perintah awk agar tampilannya lebih rapi dan hanya mengambil data yang diperlukan.

## eksekusi
Sebelum dijalanin,saya beri izin eksekusi pada file itu pake perintah chmod +x.

## modifikasi latihan 9.1
Berdasarkan instruksi pada Latihan 9.1,saya modifikasi script awal biar gak cuman menampilkan teks di layar,tapi juga menyimpannya secara otomatis ke file.txt. Saya memaakai operator pipe (|) dan perintah tee di akhir blok perintah biaar output sistem terdokumentasi dengan baik tanpa harus mengetik nama file secara manual.

## Hasil Percobaan
Setelah dijalankan dengan perintah ./laporan-sistem.sh, script berhasil menampilkan:

* Informasi waktu (Hari, Tanggal, Jam).
* Identitas sistem (Hostname dan User).
* Status hardware (Jumlah CPU core dan RAM tersedia).
* Kapasitas penyimpanan pada direktori root (/).
* File baru bernama laporan-2026-04-22.txt tercipta secara otomatis di dalam folder yang sama.

<img width="1594" height="1037" alt="image" src="https://github.com/user-attachments/assets/5c922c23-f3b0-439d-b9b9-248743d6410f" />

