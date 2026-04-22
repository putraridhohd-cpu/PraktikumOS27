# Laporan Praktikum 3 : Mini Health Check Harian Server
<img width="575" height="894" alt="Screenshot 2026-04-08 095127" src="https://github.com/user-attachments/assets/f8388375-9c5c-4728-a477-61a62768461f" />


## 1. Kode Script ``` daily-healthcheck ``` 
Berikut adalah kode yang telah diimplementasikan di direktori ``` ~/bin/ ``` agar dapat dijalankan dari mana saja:
```
#!/bin/bash
LOG_FILE="healthcheck-$(date +%F).log"
{
    echo "=========================================="
    echo "      LAPORAN HEALTH CHECK HARIAN         "
    echo "=========================================="
    echo "Waktu Cek    : $(date)"
    echo "Hostname     : $(hostname)"
    echo "User Aktif   : $(whoami)"
    echo "Shell Aktif  : $SHELL"
    echo "Uptime       : $(uptime -p)"
    echo "------------------------------------------"
    echo "Penggunaan Memori:"
    free -h
    echo ""
    echo "Penggunaan Disk (Root):"
    df -h /
    echo ""
    echo "10 Command Terakhir:"
    tail -n 10 ~/.bash_history
    echo "=========================================="
} | tee "$LOG_FILE"

if [ ${PIPESTATUS[0]} -eq 0 ]; then
    echo "Health check berhasil disimpan ke $LOG_FILE"
else
    echo "Terjadi kesalahan!"
fi
```


## 2. Contoh Isi File Log Hasil Eksekusi
<img width="1229" height="964" alt="Screenshot 2026-04-08 095343" src="https://github.com/user-attachments/assets/30f7309d-6144-4393-9c5a-806928a6bd6f" />

Berdasarkan pengujian pada tanggal 2026-04-08, isi file healthcheck-2026-04-08.log adalah sebagai berikut:
* Waktu Cek: Wed Apr 8 02:53:21 AM UTC 2026.
* Uptime: up 1 hour, 42 minutes.
* Penggunaan Disk: 49% (5.2G Used dari 12G).
* Status Memori: 1.3Gi Free dari total 1.9Gi.


## 3. Penjelasan Fungsi Tiap Bagian Script
Untuk memenuhi syarat konsep yang harus muncul dalam praktikum ini:
* Environment Variable & PATH: Script diletakkan di folder bin yang sudah didaftarkan pada $PATH agar bisa dieksekusi secara global.
* Command Substitution: Menggunakan $(date +%F) untuk penamaan file log otomatis dan $(whoami) untuk mendeteksi user aktif secara dinamis.
* Pipeline & tee: Mengalirkan seluruh blok informasi ke perintah tee sehingga admin bisa melihat hasil di layar sekaligus menyimpannya ke file permanen.
* History: Mengambil data dari ~/.bash_history menggunakan perintah tail untuk melihat aktivitas terakhir yang relevan dengan audit sistem.
* Penanganan Error Dasar: Menggunakan variabel ${PIPESTATUS[0]} untuk memastikan bahwa blok perintah utama berhasil dijalankan sebelum memberikan pesan konfirmasi sukses.

  
