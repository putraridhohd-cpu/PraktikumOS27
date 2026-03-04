# Implementasikan script backup
## 1. kita buat file backup nya dulu:
```
nano backup.sh
```
lalu isi di GNU nano dengan ini:
```
#!/bin/bash

SOURCE_DIR="/etc"
BACKUP_FILE="backup-$(date +%Y%m%d-%H%M%S).tar.gz"
SUCCESS_LOG="backup-success.log"
ERROR_LOG="backup-error.log"

echo "===== $(date) =====" | tee -a $SUCCESS_LOG $ERROR_LOG

tar -czvf "$BACKUP_FILE" "$SOURCE_DIR" \
    > >(tee -a $SUCCESS_LOG) \
    2> >(tee -a $ERROR_LOG)

echo "Backup selesai: $(date)" | tee -a $SUCCESS_LOG
```
<img width="483" height="284" alt="script" src="https://github.com/user-attachments/assets/dd2ac3a5-8569-48da-84ef-96303088a679" />

lalu kita simpan pakai CTRL+O lalu enter,lalu keluar dengan menggunakan CTRL+X

lalu beri izin terlebih dahulu:
```
chmod +x backup.sh
```

lalu jalankan:
```
./backup.sh
```

### HASIL NYA:
<img width="492" height="604" alt="image" src="https://github.com/user-attachments/assets/9d3e931f-fb7a-4a04-bc59-184289ec3689" />

## Penjelasan kode panjang di GNU Nano
### 1. Menggunakan tar
```
tar -czvf
```
* c = create
* z = gzip
* v = tampilkan file (progress)
* f = nama file

### 2. Menampilkan progress dengan tee
Output tar ditampilkan di terminal karena pakai tee.

### 3. Mencatat stdout ke backup-success.log
```
> >(tee -a $SUCCESS_LOG)
```
Semua output normal masuk ke log + tampil di layar.

### 4. Mencatat stderr ke backup-error.log
```
2> >(tee -a $ERROR_LOG)
```
Semua error masuk file error log.

### 5. Timestamp di setiap log entry
Kita tambahkan:
```
echo "===== $(date) ====="
```
Dan nama file backup juga pakai timestamp:
```
backup-20260303-201530.tar.gz
```
