# Laporan Praktikum: Audit File Konfigurasi dan Logging Aman
<img width="740" height="901" alt="Screenshot 2026-04-08 092555" src="https://github.com/user-attachments/assets/01cd8878-1ab2-482d-b202-42f7ab6d9bfb" />


## 1. Detail Perintah yang Digunakan
Untuk memenuhi syarat konsep praktikum, saya menjalankan rangkaian perintah berikut:
```
NAMA_LAPORAN="audit-konfigurasi-$(date +%F).txt"
find /etc -name "*.conf" > "$NAMA_LAPORAN" 2> audit-error.log
echo "Total file konfigurasi ditemukan: $(wc -l < "$NAMA_LAPORAN")" | tee -a "$NAMA_LAPORAN"
```
### Alasan Modifikasi & Penggunaan Simbol:
* Variable & Command Substitution: Menggunakan $(date +%F) agar nama file laporan dinamis mengikuti tanggal audit (2026-04-08).
* Redirection (> & 2>): Memisahkan output standar (daftar file) ke file .txt dan mengalihkan pesan kesalahan (stderr) ke audit-error.log agar laporan utama tetap bersih.
* Pipeline (|) & tee: Mengalirkan hasil perhitungan wc -l ke layar terminal sekaligus menambahkannya (append) ke akhir file laporan.


## 2. Hasil Audit Sistem
* File Laporan Utama: audit-konfigurasi-2026-04-08.txt.
* Statistik Temuan: Ditemukan sebanyak 156 file berekstensi .conf di dalam direktori /etc.
<img width="1643" height="567" alt="image" src="https://github.com/user-attachments/assets/8e587e72-7e39-497e-a137-6c0c340bcf41" />

* File Log Error: audit-error.log.
<img width="1175" height="134" alt="image" src="https://github.com/user-attachments/assets/adf71242-7baa-4125-a621-678d5716d936" />


## 3. Analisis Pentingnya Pemisahan stdout dan stderr
Pemisahan antara Standard Output (stdout) dan Standard Error (stderr) sangat kritikal dalam audit sistem karena:

* Integritas Data: Laporan hasil (seperti daftar file konfigurasi) tidak tercampur dengan pesan teknis error, sehingga data siap diolah oleh program lain atau dibaca manusia dengan mudah.
* Efisiensi Troubleshooting: Admin dapat langsung fokus memeriksa audit-error.log untuk melihat folder mana yang tidak bisa diakses tanpa harus mencarinya di antara ratusan baris hasil sukses.
* Otomasi: Memungkinkan sistem monitoring untuk memicu peringatan (alert) hanya jika file stderr berisi informasi yang tidak terduga.


