# Percobaan ke-4
Telusuri derectory /proc. Tampilkan isi file interrupts, devices, cpuinfo, meminfo dan uptime menggunakan perintah cat. Dapatkah Anda melihat mengapa directory /proc disebut pseudo -filesystem yang memungkinkan akses ke struktur data kernel ?

## 1.Eksplorasi Data Hardware & Sistem
Gunakan perintah cat untuk mengintip informasi langsung dari "otak" server kamu:
* Informasi Processor:
```
cat /proc/cpuinfo
```
<img width="806" height="517" alt="image" src="https://github.com/user-attachments/assets/5c7932a8-0c10-4389-9dfa-ce5de20216af" />
* Informasi RAM:
```
cat /proc/meminfo
```
<img width="424" height="581" alt="image" src="https://github.com/user-attachments/assets/0fa5016e-188a-4549-920d-b2ac6fc83706" />
* Waktu Nyala (Uptime):
```
cat /proc/uptime
```
<img width="360" height="51" alt="image" src="https://github.com/user-attachments/assets/d5b794df-4d5c-4e75-b225-71f7d3cdbd2d" />
* Interupsi Hardware:
```
cat /proc/interrupts | more
```
<img width="630" height="535" alt="image" src="https://github.com/user-attachments/assets/b1c555c2-1b21-44bb-834c-0c2684b0a628" />
* Daftar Perangkat:
```
cat /proc/devices
```
<img width="279" height="589" alt="image" src="https://github.com/user-attachments/assets/b493c01c-1445-4eba-b7e5-a8cf9a5387ee" />


## 2. Mengapa Disebut Pseudo-Filesystem?
Setelah saya menjalankan perintah cat di atas, saya menyadari sesuatu yang aneh jika mengecek ukuran filenya:
```
ls -lh /proc/cpuinfo
```
<img width="459" height="50" alt="image" src="https://github.com/user-attachments/assets/bd9b0ec5-3a04-4462-ae7a-fce384ebe41b" />
### Analisa kenapa disebut "Pseudo" (Semu):
* Tidak Ada di Disk: File-file ini tidak memakan ruang di harddisk. Mereka hanya ada di dalam RAM (Memory).
* Jendela ke Kernel: Saat kamu melakukan cat /proc/cpuinfo, Kernel Linux secara real-time mengumpulkan data dari hardware dan menyajikannya dalam bentuk "teks" seolah-olah itu adalah file biasa.
* Dinamis: Isinya berubah setiap detik. Misalnya, isi meminfo akan selalu berubah tergantung aplikasi apa yang sedang berjalan.
* Komunikasi Dua Arah: Selain membaca (cat), admin terkadang bisa menulis (echo) ke file tertentu di /proc (biasanya di /proc/sys) untuk mengubah pengaturan sistem tanpa harus restart.
