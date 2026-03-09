# Percobaan kedua
Caranya: Gunakan cd untuk pindah, pwd untuk verifikasi, dan ls dengan filter agar tidak kewalahan.

## 1. Strategi "Direct Check" (Paling Cepat)
### Langkah-langkahnya:
* Telusuri /bin:
```
cd /bin; pwd; ls -l ls cp mv sh
```
(Ini langsung membuktikan bahwa file-file utama itu ada di sana).
* Telusuri /sbin:
```
cd /sbin; pwd; ls -l reboot fdisk
```
(Membuktikan folder ini berisi perintah administratif).
* Telusuri /tmp:
```
cd /tmp; pwd; ls -a
```
(Cukup lihat isinya sekilas karena biasanya tidak banyak).

Telusuri /boot:
```
cd /boot; pwd; ls -lh vmlinuz*
```
(Mencari file kernel secara spesifik).
<img width="1268" height="465" alt="image" src="https://github.com/user-attachments/assets/8ed22bc0-1e3f-4880-98d5-9c5cd8d54bc3" />

## 2. Menggunakan Fitur Wildcard (*)
Jika kita ingin membuktikan ada banyak file tapi tetap efisien, gunakan tanda bintang. Misalnya di /usr/bin:
```
cd /usr/bin
ls -d g*
```
Menampilkan semua file yang berawalan huruf 'g' saja
<img width="1213" height="210" alt="image" src="https://github.com/user-attachments/assets/7707921c-a2b0-462e-abcb-9624a01e7110" />

## 3. Cara Menjawab dengan cat secara Efisien
Ingat, jangan gunakan cat pada file di /bin atau /sbin karena itu file mesin (biner). Untuk memenuhi tugas "menggunakan cat" dalam penelusuran pohon:
```
cat /etc/hostname    # Melihat nama server
cat /etc/issue       # Melihat versi Ubuntu yang kamu gunakan
```
<img width="346" height="98" alt="image" src="https://github.com/user-attachments/assets/739e4019-2093-4ed3-84e9-c798588119eb" />

