# Latihan 6.3
<img width="1071" height="367" alt="image" src="https://github.com/user-attachments/assets/17a3e57f-e999-47f0-a2b3-091281b04330" />


## 1. Menjalankan Proses dengan Nilai Nice Spesifik
### Langkah Kerja:
Saya menguji cara menjalankan sebuah proses dengan prioritas tertentu menggunakan perintah nice. Di sini, saya menetapkan nilai Nice (NI) sebesar 5 untuk perintah sleep 200 dan menambahkan simbol & agar proses berjalan di background:
### Hasil Verifikasi:
Sistem memberikan PID 1481. Saat saya cek menggunakan perintah ps -o pid,ni,cmd -p 1481, kolom NI menunjukkan angka 5, yang berarti proses berhasil berjalan dengan prioritas sedikit di bawah standar (0).
<img width="685" height="144" alt="image" src="https://github.com/user-attachments/assets/f86050f8-3351-4865-982d-658bb1033205" />


## 2. Mengatur Ulang Prioritas dengan renice
### Langkah Kerja:
Tanpa menghentikan proses yang sedang berjalan, saya mencoba menurunkan prioritasnya lebih jauh lagi menjadi 10 menggunakan perintah renice:
### Hasil Pengamatan:
Sistem memberikan konfirmasi: 1481 (process ID) old priority 5, new priority 10. Ketika diverifikasi kembali dengan ps, nilai NI memang benar sudah berubah menjadi 10. Hal ini membuktikan bahwa prioritas proses di Linux bersifat dinamis dan bisa diatur ulang kapan saja tanpa perlu mematikan proses tersebut.
<img width="717" height="145" alt="image" src="https://github.com/user-attachments/assets/323de7ca-038f-4ba0-bc52-e2dac5af2b3e" />


## 3. Pembatasan Hak Akses pada Nilai Nice Negatif
### Langkah Kerja:
Saya mencoba memberikan prioritas tinggi (nilai Nice negatif -5) kepada proses yang sama tanpa menggunakan hak akses sudo:
### Hasil Pengamatan:
Sistem menolak perintah tersebut dengan pesan kesalahan:
<img width="1008" height="85" alt="image" src="https://github.com/user-attachments/assets/ecb4c07a-c4d5-43cc-9245-d32e53bdb976" />

### Analisis & Jawaban:
* Mengapa hal ini terjadi? Linux melarang user biasa untuk meningkatkan prioritas prosesnya sendiri ke angka negatif atau di bawah nilai saat ini.
* Alasannya: Ini adalah mekanisme keamanan untuk menjaga stabilitas sistem. Jika setiap pengguna bisa meningkatkan prioritas prosesnya secara bebas, satu pengguna dapat memonopoli sumber daya CPU. Hal ini berisiko membuat proses penting milik sistem atau pengguna lain terganggu atau bahkan menyebabkan sistem menjadi hang. Hanya Superuser (root) yang memiliki wewenang untuk memberikan prioritas tinggi demi menjaga keadilan pembagian sumber daya.
