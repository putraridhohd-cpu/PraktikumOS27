# Membuat Pipelines
## File /etc/passwd berisi data user Linux.
### contoh isinya:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
```
* Formatnya dipisahkan dengan tanda titik dua :
* Kolom pertama = username.

## Ketik langsung di terminal:
```
cat /etc/passwd | cut -d: -f1 | sort > sorted-users.txt
```
arti dari "cat /etc/passwd" adalah membaca isi file,nah kalo tidak muncul apa-apa itu normal,karena Tanda > itu artinya:
* Output tidak ditampilkan ke layar
* Tapi disimpan ke file sorted-users.txt

Jadi terminal memang akan terlihat kosong.
kalau mau lihat hasil nya cukup ketik:
```
cat sorted-users.txt
```
dan hasilnya akan muncul daftar username yang sudah terurut alfabetis seperti ini:
<img width="376" height="561" alt="image" src="https://github.com/user-attachments/assets/c5e48f79-e2a8-4a28-ab38-f79a3fc7dabe" />
