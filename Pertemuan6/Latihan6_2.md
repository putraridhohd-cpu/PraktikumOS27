# Latihan 6.2
<img width="877" height="238" alt="image" src="https://github.com/user-attachments/assets/949584f5-0bb9-42a3-8a61-218e79467bab" />

## 1. Pengamatan Kondisi Proses (STAT)
Langkah Kerja:
Untuk mengamati kolom STAT pada proses sleep 120 sesuai instruksi, saya menjalankan perintah itu dengan menambah simbol ampersand (&) di akhir perintah sebagai berikut:
```
sleep 120 &
ps aux | grep sleep
```
<img width="1291" height="177" alt="image" src="https://github.com/user-attachments/assets/e35a86ba-fd6f-4433-a521-4662e0ab6744" />

### Hasil Pengamatan:
Berdasarkan output terminal, proses sleep 120 dengan PID 1390 menunjukkan kode status S. Sementara itu, muncul pula baris dengan status S+, namun itu merupakan proses dari perintah grep yang sedang mencari kata "sleep" di sistem.
Analisis Kondisi:
* Huruf S (Interruptible Sleep): Menunjukkan proses sleep 120 sedang berada dalam fase menunggu (waiting). Proses ini tidak menggunakan siklus CPU saat ini karena hanya menunggu timer selesai, namun tetap bisa diinterupsi atau dibangunkan oleh sinyal sistem.

* Tanda + (pada grep): Menunjukkan bahwa proses tersebut merupakan bagian dari foreground process group (proses yang sedang aktif di jendela terminal saat ini). Karena proses sleep dijalankan dengan simbol & (background), maka ia hanya memiliki status S tanpa tanda +.


## 2. Analisis Exit Code pada Perintah Linux
Langkah Kerja & Percobaan:
Saya melakukan pengujian untuk melihat bagaimana sistem memberikan sinyal balik (feedback) setelah sebuah perintah selesai dijalankan. Pengujian dilakukan menggunakan perintah echo $? untuk memanggil nilai Exit Code dari perintah terakhir.

### Percobaan Perintah Berhasil:
Saya mencoba melist isi direktori /home dengan perintah:
```
ls /home
echo $?
```
<img width="574" height="142" alt="image" src="https://github.com/user-attachments/assets/df98d783-df8d-42ec-8c6e-8de92f5ec7f7" />

Hasil Output:
Terminal menampilkan user saya ridho27, kemudian muncul notifikasi [1]+ Done sleep 120 (menandakan proses sleep di percobaan sebelumnya telah selesai), dan terakhir muncul angka 0.

### Percobaan Perintah Gagal:
Saya mencoba membaca file yang memang sengaja tidak saya buat dengan perintah:
```
cat file_tidak_ada.txt
echo $?
```
<img width="726" height="115" alt="image" src="https://github.com/user-attachments/assets/af6348b1-fc82-4310-a333-328924a7a9f6" />

Hasil Output:
Sistem memberikan pesan kesalahan No such file or directory dan saat dicek nilainya muncul angka 1.

### Analisis & Temuan:
Dari praktik di atas, saya menemukan sebuah pola konsisten dalam sistem operasi Linux:

* Nilai 0 (Success): Ketika saya menjalankan ls /home, sistem memberikan nilai 0. Ini artinya perintah tersebut dieksekusi dengan sempurna tanpa ada kendala teknis.

* Nilai 1 (Error): Saat saya mencoba cat file yang tidak ada, sistem memberikan nilai 1. Angka non-nol ini adalah cara Linux memberitahu kita (atau skrip otomatis) bahwa terjadi kegagalan atau instruksi tidak bisa diselesaikan.

* Catatan Tambahan: Tadi sempat muncul tulisan Done sleep 120 di tengah-tengah output. Ini adalah fitur job control di Linux yang memberitahu saya bahwa proses background yang saya jalankan di latihan sebelumnya sudah selesai tepat saat saya menekan Enter untuk perintah berikutnya.

### Kesimpulan:
Setiap perintah di Linux selalu meninggalkan "jejak" berupa angka. Jika hasilnya 0 maka aman (berhasil), jika selain 0 maka ada masalah. Pemahaman ini sangat penting jika nanti kita ingin membuat skrip otomasi (Shell Scripting).
