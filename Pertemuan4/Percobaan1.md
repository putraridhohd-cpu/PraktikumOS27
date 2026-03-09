# Percobaan Pertama
<img width="251" height="311" alt="55629d25-1426-45ea-9314-683d0a20dead" src="https://github.com/user-attachments/assets/2fb0a42d-3af9-4aeb-ae8f-15fb61332079" />

## 1. Navigasi Home & Direktori Aktif
* $ cd: Tanpa argumen, perintah ini akan membawa kamu kembali ke Home Directory pengguna (misalnya: /home/namauser).
* $ pwd: Menampilkan alamat direktori saat ini. Jika baru menjalankan cd, hasilnya biasanya /home/[nama_user].
* $ ls -al: Menampilkan semua file (termasuk yang tersembunyi/hidden) beserta detailnya (izin, pemilik, ukuran).
<img width="648" height="452" alt="image" src="https://github.com/user-attachments/assets/d0461fa5-1c15-4126-87dc-d49592cd10ee" />

## 2.Menggunakan Titik (.) dan Titik Dua (..)
* $ cd .: Titik satu melambangkan direktori saat ini. Perintah ini tidak akan mengubah posisi kamu, kamu tetap berada di folder yang sama.
* $ pwd: Hasilnya tetap sama dengan sebelumnya.
* $ cd ..: Titik dua melambangkan parent directory (satu level di atas). Kita akan pindah keluar dari folder saat ini menuju folder di atasnya (misalnya dari /home/user ke /home).
* $ pwd: Akan menunjukkan lokasi baru yang lebih tinggi satu level.
* $ ls -al: Menampilkan isi dari direktori induk tersebut.
<img width="449" height="143" alt="image" src="https://github.com/user-attachments/assets/2e59efd2-cfd0-4f77-81bd-d62b5a4bd10e" />

## 3. Bergerak ke Root
* $ cd ..: Jika dilakukan lagi, kita akan sampai ke direktori Root (/), yang merupakan dasar dari seluruh sistem file Linux.
* $ pwd: Hasilnya akan menampilkan /.
* $ ls -al: Menampilkan folder sistem penting seperti bin, etc, var, dan home.
<img width="578" height="552" alt="image" src="https://github.com/user-attachments/assets/625c8669-684d-40f4-b236-5bf3116d97dc" />

## 4. Eksplorasi Konfigurasi (/etc)
* $ cd /etc: Berpindah langsung ke folder /etc, tempat penyimpanan file konfigurasi sistem.
* $ ls -al | more: Menampilkan daftar file di /etc. Karena isinya sangat banyak, perintah | more digunakan agar tampilan berhenti per layar (tidak langsung meluncur ke bawah), sehingga kita bisa membacanya perlahan.
* $ cat passwd: Membaca isi file bernama passwd. File ini berisi daftar pengguna (users) yang terdaftar di sistem Ubuntu tersebut.
<img width="758" height="589" alt="image" src="https://github.com/user-attachments/assets/739d19e7-90c6-4819-b55e-ffa29513aaa0" />

## 5. Fitur "Back" di Terminal
* $ cd -: Ini adalah jalan pintas untuk kembali ke direktori sebelumnya (seperti tombol Back). Jika sebelumnya kamu berada di / sebelum masuk ke /etc, perintah ini akan membawamu kembali ke /.
* $ pwd: Menunjukkan lokasi terakhir setelah melakukan "Back".
<img width="283" height="83" alt="image" src="https://github.com/user-attachments/assets/f1efac6c-a931-42d7-abe1-ca71781fa5f1" />

## Analisa Singkat
Latihan ini mengajarkan kita perbedaan antara Relative Path (menggunakan ..) dan Absolute Path (menggunakan /etc), serta cara mengintip isi file sistem tanpa membukanya di editor.
