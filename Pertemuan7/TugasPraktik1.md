# Laporan Praktikum 1: Toolkit Bash Administrator Pribadi
<img width="730" height="875" alt="Screenshot 2026-04-08 085436" src="https://github.com/user-attachments/assets/a4e12c85-23de-4837-92a2-fd832f27d93f" />

## 1. Konfigurasi .bashrc
### Siapkan "Gudang" Script:
Kita buat dulu direktori bin di dalam folder home
```
mkdir -p ~/bin
```
### Rakit Toolkit di .bashrc:
```
nano ~/.bashrc
```
Gulir sampai paling bawah,lalu tambah kode blok konfigurasi ini:
```
# --- Ridho's Admin Toolkit ---
export PATH="$HOME/bin:$PATH"

# Aliases (Minimal 2)
alias cls='clear'
alias kcl='ps aux --sort=-%mem | head -n 10'

# Function (Minimal 1)
cek_koneksi() {
    echo "--- Mengecek koneksi ke Google ---"
    ping -c 3 8.8.8.8
}
```


## 2. Verifikasi Environment & Toolkit
Berdasarkan pengujian di terminal, berikut adalah bukti bahwa konfigurasi telah aktif:

* Output echo $PATH:
<img width="1646" height="59" alt="image" src="https://github.com/user-attachments/assets/f7bb660b-d291-452f-beed-1563ed8f2fb6" />
(Direktori /home/ridho27/bin berhasil ditambahkan di urutan paling depan).

* Lalu Verifikasi Alias (cls):
<img width="464" height="61" alt="image" src="https://github.com/user-attachments/assets/13f92094-82ff-428b-96f1-fcf5973aa344" />

* Verifikasi Fungsi (cek_koneksi):
<img width="673" height="207" alt="image" src="https://github.com/user-attachments/assets/59ff9233-1db4-4b18-a680-5a12eb92ee82" />

* Verifikasi Script (spek):
<img width="571" height="60" alt="image" src="https://github.com/user-attachments/assets/abf1ba30-703b-4474-acb1-a1e0b6a99774" />


## 3. Eksekusi Script Ringkasan Sistem (spek)
Isi Script ~/bin/spek:
```
#!/bin/bash
echo "=== RINGKASAN SISTEM RIDHO ==="
echo "User Aktif : $(whoami)"
echo "Waktu Nyala: $(uptime -p)"
echo "Sisa Disk  :"
df -h / | tail -1 | awk '{print $4}'
```

Output Saat Dijalankan:
<img width="517" height="207" alt="image" src="https://github.com/user-attachments/assets/fcf08c4b-496b-41dc-9ad4-fbfe4d8bd76a" />


## Analisis & Catatan Perubahan (Notes for Instructor)
Dalam laporan ini, saya menerapkan beberapa penyesuaian dari instruksi dasar:

* Modifikasi PATH: Saya menempatkan $HOME/bin di paling depan variabel PATH ($HOME/bin:$PATH).
Alasannya: Agar jika saya membuat script dengan nama yang sama dengan perintah sistem, script buatan saya yang akan diprioritaskan terlebih dahulu.
* Efisiensi Alias & Fungsi: Saya menambahkan alias kcl untuk memantau 10 proses pemakan memori terbesar secara instan, yang sangat berguna untuk tugas administrasi harian dibandingkan hanya alias sederhana.
* Aksesibilitas Script: Script spek dapat dipanggil dari direktori mana pun tanpa harus mengetikkan path lengkapnya (misal: /home/ridho27/bin/spek), membuktikan bahwa konfigurasi environment variabel telah berhasil.




