# Percobaan ketiga
Telusuri direktory /dev. Identifikasi perangkat yang tersedia.Identifikasi tty (termninal) Anda (ketik who am i); siapa pemilih tty Anda (gunakan ls –l).

## 1. Menelusuri Direktori /dev
Jangan kaget, isinya bukan file teks, melainkan file khusus yang mewakili hardware.
* Langkah:
```
cd /dev
pwd
ls -l | more
```

## 2. Identifikasi Terminal saya (who am i)
Karena Ubuntu Server bisa diakses oleh banyak orang sekaligus, kita perlu tahu "pintu" mana yang sedang kita gunakan.
* Langkah:
```
who am i
```
* Analisa Hasil:
<img width="335" height="52" alt="image" src="https://github.com/user-attachments/assets/98f084ab-0c79-45bc-9115-d77b1a4d7207" />
ridhoo tty1 Inilah identitas terminal saya.

## 3. Siapa Pemilik Terminal saya?
Sekarang kita cek "file" yang mewakili terminal tersebut di dalam /dev:
```
ls -l /dev/tty1
```
maka hasil nya adalah:
<img width="449" height="49" alt="image" src="https://github.com/user-attachments/assets/8199a6fb-a05c-446b-8747-7637eb2c1e40" />
* Kolom ke-3 (ridhoo): Adalah nama akun saya
* Kolom ke-4 (tty 4): Adalah Group yang menaungi perangkat terminal tersebut.
* Huruf c di awal: Artinya ini adalah Character Device, bukan file biasa.
