# LATIHAN 6.1
<img width="512" height="225" alt="unnamed" src="https://github.com/user-attachments/assets/ba0ff801-52d4-4ca2-b64c-4e76b70f3205" />

## 1. total proses dan PID terkecil
### Total proses:
saat saya ketik perintah "ps aux" muncul banyak sekali proses seperti ini:
<img width="1438" height="1020" alt="image" src="https://github.com/user-attachments/assets/3ecca9b9-b065-4d84-8cd9-1a2c2bde43e3" />
nah daripada hitung manual proses nya satu satu,mending saya ketik perintah ini:
```
ps aux | wc -l
```
untuk memunculkan otomatis jumlah proses nya seperti ini:
<img width="565" height="72" alt="image" src="https://github.com/user-attachments/assets/6ea1de48-e638-4243-b285-a5538c2d7854" />

dan disitu sudah terlihat proses nya ada 109 :)
### Jumlah PID terkecil: 
cukup lihat saja hasil dari "ps aux" tadi lalu lihat di lihat proses dengan PID terkecil,dan cara melihat nama proses nya adalah dengan melihat nama COMMAND nya
<img width="1389" height="640" alt="image" src="https://github.com/user-attachments/assets/db847965-7392-4211-bfb9-c452f12e4dcf" />
disitu sudah terlihat jelas proses dengan PID adalah proses "/sbin/init"


## 2. Menemukan induk dari proses BASH
ketik perintah ini: 
```
pstree -p
```
lalu cari proses BASH nya,setelah ketemu,lihat induk nya yang berada tepat di atas bash dalam diagram tersebut
<img width="1102" height="1060" alt="image" src="https://github.com/user-attachments/assets/19c28776-13ad-4fc7-adc5-ac46706968ac" />
nah disitu sudah terlihat induk dari proses BASH itu adalah "sshd",Karena saya login via SSH, induk dari bash saya adalah proses sshd


## 3. Membandingkan ps aux dan ps aux -L
Jalankan kedua perintah tersebut secara bergantian:
```
ps aux
```
```
ps aux -L
```
Perbedaan yang saya lihat:
* ps aux: Hanya menampilkan Proses. Setiap baris mewakili satu program yang sedang berjalan.
* ps aux -L: Menampilkan proses beserta Threads (unit instruksi yang lebih kecil di dalam proses).
Indikator Utama: Di ps aux -L, akan muncul kolom tambahan bernama LWP (Light Weight Process) atau TID (Thread ID). saya melihat satu aplikasi (misal: Java atau server) bisa memiliki banyak baris karena ia menjalankan banyak thread sekaligus.

