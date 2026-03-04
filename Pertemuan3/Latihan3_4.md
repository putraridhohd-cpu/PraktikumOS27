# Linux Pipeline
## Ketik perintah ini:
```
find / -type f -name "*.conf" 2>/dev/null | tee conf-list.txt | wc -l
```
Maka hasil nya adalah seperti ini:
<img width="748" height="57" alt="image" src="https://github.com/user-attachments/assets/4ad60fdb-9524-40cf-bbc4-013ff587c83b" />

## Penjelasan masing-masing kode:
### 1. Mencari semua file .conf
```
find / -type f -name "*.conf"
```
* / → mulai dari root (seluruh sistem)
* -type f → hanya file

* -name "*.conf" → file berakhiran .conf

## 2. Membuang pesan "Permission denied"
```
2>/dev/null
```
* 2> → redirect error (stderr)
* /dev/null → dibuang (tidak ditampilkan)

## 3. Menghitung Jumlah file
```
wc -l
```
* Menghitung jumlah baris = jumlah file ditemukan
* Di terminal saya menemukan ada total 324 file yang ditemukan seperti pada gambar di atas

## 4. Menyimpan daftar path lengkap ke file
```
tee conf-list.txt
```
* Simpan daftar ke file
* Tetap lanjut ke wc -l
