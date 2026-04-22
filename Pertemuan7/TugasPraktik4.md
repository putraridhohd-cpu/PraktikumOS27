# Laporan Praktikum 4 : Penanganan File dengan Nama Kompleks dan Arsip Aman


## 1. Daftar File Awal (Direktori ~/praktikum4)
Saya telah membuat minimal 4 file dengan berbagai variasi nama untuk pengujian:
* Nama dengan spasi: 'laporan akhir semester.txt'
* Nama dengan karakter khusus: 'data(backup)@2026.csv'
* Pola serupa untuk wildcard: test_v1.log dan test_v2.log
<img width="1279" height="111" alt="image" src="https://github.com/user-attachments/assets/800d6241-9fd5-4c99-8964-4660a4eb1dd7" />


## 2. Analisis Perbedaan Quoting
Berdasarkan percobaan di terminal:
* Tanpa Quoting: Perintah ls -l laporan akhir semester.txt menghasilkan error "No such file or directory" karena shell memecah argumen berdasarkan spasi.
* Dengan Quoting: Perintah ls -l "laporan akhir semester.txt" berhasil mengeksekusi file dengan benar karena seluruh nama dianggap sebagai satu string tunggal.
<img width="1439" height="174" alt="image" src="https://github.com/user-attachments/assets/f66a27a3-bdb5-4c48-b8c2-e5a1b02003df" />


## 3. Proses Backup dan Pengarsipan
Daftar File Hasil Backup: Semua file berhasil disalin ke direktori ~/backup_aman dengan selamat menggunakan bantuan tanda petik dan wildcard test_*.log.
* File Arsip tar.gz: Berhasil dibuat dengan nama arsip_backup_ridho.tar.gz (ukuran 230 byte) yang berisi seluruh isi folder backup.
* Riwayat Perintah: Disimpan dalam file riwayat-arsip.txt sebagai bukti dokumentasi langkah kerja.
<img width="1544" height="879" alt="image" src="https://github.com/user-attachments/assets/3b2bc59d-227a-4414-a3b0-3a0a6435e624" />


## 4. Refleksi Singkat: Pentingnya Quoting di Bash
Quoting bukan sekadar variasi penulisan, melainkan mekanisme keamanan untuk menjaga integritas perintah. Tanpa quoting yang benar, seorang administrator berisiko melakukan kesalahan fatal seperti menghapus file yang salah atau gagal memproses data penting hanya karena ada karakter spasi, tanda kurung, atau simbol khusus lainnya dalam nama file. Penggunaan double quote (" ") memungkinkan penggunaan variabel di dalamnya, sementara single quote (' ') menjaga isi teks tetap literal.
