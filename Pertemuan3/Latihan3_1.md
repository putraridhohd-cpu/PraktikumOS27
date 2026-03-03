# bash scripting + redirection + tee.
## 1.Menampilkan daftar 10 file terbesar di direktori /var/log/
### pertama buat file nya dulu dengan kode:
```
nano latihan3_1.sh
```
lalu setelah itu kita akan di arahkan ke GNU nano,lalu tulis kode ini di GNU nano :
```
#!/bin/bash

du -ah /var/log 2>error.log | \
sort -rh | \
head -n 10 | \
tee large-logs.txt
```
kalau sudah simpan file nya dengan menekan CTRL+O,lalu enter dan keluar dari GNU nano dengan CTRL+X
### lalu tulis kode ini agar izin eksekusi diberikan:
```
chmod +x latihan3_1.sh
```
### lalu jalankan:
```
./latihan3_1.sh
```

### dan ini adalah 10 fie terbesar nya:
<img width="1136" height="236" alt="image" src="https://github.com/user-attachments/assets/19fed998-55d4-4f2d-a4a0-8ed083e4e94b" />

## 2.Menyimpan hasilnya ke file large-logs.txt
sebenarnya hasil nya sudah tersimpan di kode :
```
#!/bin/bash

du -ah /var/log 2>error.log | \
sort -rh | \
head -n 10 | \
tee large-logs.txt
```
di bagian:
```
tee large-logs.txt
```
kode itu juga sekaligus menampilkan output juga di terminal

## 3. Menangani error dengan redirect ke error.log
error ini sudah masuk ke error.log dengan kode :
```
2>error.log
```
yang artinya:
* 2> artinya redirect stderr (error output)
* Jika ada error seperti "Permission denied", akan masuk ke error.log




