# membuat file server.log
## 1. Jalankan perintah
```
nano server.log
```

## 2. Isi dengan minimal 10 baris seperti ini:
```
INFO Server started
INFO User login success
WARN Memory usage high
ERROR Database connection failed
INFO Backup completed
WARN Disk space low
ERROR Failed to open configuration file
INFO Service restarted
ERROR Timeout while connecting to API
WARN CPU temperature high
```
lalu Simpan:
* Ctrl + O → Enter
* Ctrl + X

## 3. Gunakan grep untuk Menampilkan Hanya ERROR
```
grep "ERROR" server.log
```
outputnya seperti ini:
```
ERROR Database connection failed
ERROR Failed to open configuration file
ERROR Timeout while connecting to API
```
## kesimpulan
File server.log telah dibuat dengan 10 baris yang mengandung variasi INFO, WARN, dan ERROR. Untuk menampilkan hanya baris yang mengandung ERROR digunakan perintah:
```
grep "ERROR" server.log
```
Perintah tersebut berhasil menampilkan seluruh baris yang mengandung kata ERROR.