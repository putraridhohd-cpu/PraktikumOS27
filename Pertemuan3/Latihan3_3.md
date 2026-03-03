# Monitoring Script
## 1. Buat file baru:
```
nano monitoring.sh
```

## 2. isi kde ini di GNU nano nya:
```
#!/bin/bash

LOG_FILE="monitoring.log"

for i in {1..12}
do
    echo "===== $(date) =====" | tee -a $LOG_FILE
    
    echo "CPU Usage:" | tee -a $LOG_FILE
    top -bn1 | grep "Cpu(s)" | tee -a $LOG_FILE
    
    echo "Memory Usage:" | tee -a $LOG_FILE
    free -h | grep "Mem" | tee -a $LOG_FILE
    
    echo "" | tee -a $LOG_FILE
    
    sleep 5
done
```
lalu Simpan → Ctrl + O → Enter
da Keluar → Ctrl + X

## 3. Beri izin eksekusi:
```
chmod +x monitoring.sh
```

## 4. Lalu jalankan:
```
./monitoring.sh
```
Maaf pak tidak ada ss hasil nya,tetap hasil nya kurang lebih seperti ini:
```
===== Tue Mar 3 20:15:01 WIB 2026 =====
CPU Usage: ...
Memory Usage: ...
```

## 5. Penjelasan:
```
for i in {1..12}
```
Loop 12 kali → total 1 menit

```
date
```
Menampilkan timestamp

```
top -bn1
```
* -b = batch mode (tanpa tampilan interaktif)
* -n1 = ambil 1 kali snapshot 

```
free -h
```
Menampilkan penggunaan memory dalam format human readable

```
tee -a
```
* -a = append (tidak menimpa file lama)
* Tampil di layar DAN simpan ke file

```
sleep 5
```
Tunggu 5 detik sebelum iterasi berikutnya
