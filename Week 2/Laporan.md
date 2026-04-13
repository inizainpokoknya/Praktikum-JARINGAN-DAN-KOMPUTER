# Laporan Praktikum Jaringan Komputer - Modul 2
## Pengenalan Tools (Wireshark Basics)

### Identitas Praktikan
| Item | Keterangan |
|------|------------|
| **Nama** | Zain Ahmad Suraiban |
| **NIM** | 10307243001 |
| **Kelas** | IF-04-01 |

---

## 1. Tujuan Praktikum
Dalam modul praktikum Jaringan Komputer Semester Genap 2025/2026, tujuan utama dari Modul 2 meliputi:
1. Peserta dapat menyelesaikan proses instalasi alat yang diperlukan, yaitu Wireshark.
2. Peserta mampu mengoperasikan alat Wireshark untuk menangkap serta mengidentifikasi paket data yang bersirkulasi.

---

## 2. Dasar Teori
### 2.1 Packet Sniffer
Wireshark adalah perangkat lunak yang berfungsi untuk memantau komunikasi antar entitas protokol, dikenal sebagai **Packet Sniffer**. Alat ini menangkap ("Sniffs") pesan yang dikirim atau diterima oleh komputer pengguna. Sebuah Packet Sniffer beroperasi secara pasif, hanya mengobservasi pesan tanpa terlibat dalam pengiriman atau penerimaan paket tersebut.

Komponen utama dari Packet Sniffer meliputi:
1. **Packet Capture Library:** Yang bertugas menerima duplikat setiap frame pada lapisan link yang dikirim atau diterima oleh komputer.
2. **Packet Analyzer:** Yang menampilkan konten lengkap dari semua field dalam pesan protokol dengan memahami struktur pesan seperti Ethernet, IP, TCP, HTTP, dan lainnya.

### 2.2 Antarmuka Wireshark
Interface Wireshark terdiri dari lima elemen pokok:
1. **Command Menu:** Menu tarik-turun standar seperti File, Capture, dan sebagainya.
2. **Packet Listing Window:** Ringkasan baris tunggal untuk masing-masing paket, mencakup No, Time, Source, Destination, Protocol, Info.
3. **Packet Header Details Window:** Penjelasan mendalam mengenai paket yang dipilih, termasuk Frame, Ethernet, IP, TCP, HTTP.
4. **Packet Contents Window:** Menunjukkan seluruh isi frame dalam bentuk ASCII dan heksadesimal.
5. **Packet Display Filter Field:** Bidang untuk menyaring data yang ditampilkan berdasarkan protokol atau kriteria lainnya.

---

## 3. Langkah Kerja
Berikut merupakan langkah-langkah yang dikerjakan dalam praktikum Modul 2 (Test Run Wireshark):

1. **Persiapan Awal:**
   - Pastikan perangkat terhubung ke jaringan Internet melalui Ethernet atau WiFi.
   - Buka aplikasi browser web.
   - Jalankan program Wireshark.

2. **Memulai Proses Capture:**
   - Pilih menu `Capture` kemudian `Interfaces`.
   - Pilih interface aktif, seperti Wi-Fi atau Ethernet, lalu klik `Start`.

3. **Membuat Traffic:**
   - Dengan Wireshark aktif, buka URL ini di browser:
     `http://gaia.cs.umass.edu/wireshark-labs/INTRO-wireshark-file1.html`
   - Tunggu hingga halaman web sederhana muncul dengan pesan selamat.

4. **Menghentikan Capture:**
   - Tekan tombol `Stop` (ikon kotak merah) di Wireshark.

5. **Menganalisis Paket:**
   - Ketik `http` di kolom filter lalu tekan Enter.
   - Cari pesan **HTTP GET** yang dikirim ke server `gaia.cs.umass.edu`.
   - Klik paket tersebut dan periksa detail protokol di jendela *Packet Header Details*.
   - Sembunyikan detail Frame, Ethernet, IP, dan TCP dengan mengklik tanda `-` atau `>`.
   - Perluas detail protokol HTTP dengan mengklik tanda `+` atau `v`.

6. **Penutupan:**
   - Tutup aplikasi Wireshark.

---

## 4. Hasil dan Pembahasan

### 4.1 Tampilan Awal Wireshark
Di bawah ini adalah tampilan awal Wireshark ketika pertama kali dijalankan sebelum memulai capture paket. Terlihat daftar interface jaringan yang dapat dipilih.

![Tampilan Awal Wireshark](assets/wireshark_home.png)
*Gambar 1: Layar sambutan Wireshark (Welcome Screen).*

### 4.2 Pemilihan Interface Capture
Jendela untuk memilih interface guna memulai penangkapan paket. Interface yang dipilih adalah yang sedang digunakan untuk koneksi internet.

![Pilih Interface](assets/wireshark_interfaces.png)
*Gambar 2: Jendela Capture Interfaces di Wireshark.*

### 4.3 Hasil Penangkapan Paket
Setelah mengunjungi URL `http://gaia.cs.umass.edu/wireshark-labs/INTRO-wireshark-file1.html` dan menghentikan capture, berikut daftar paket yang berhasil ditangkap. Meskipun hanya membuka satu halaman web, banyak protokol berjalan di belakang layar.

![Hasil Capture](assets/wireshark_packet_list.png)
*Gambar 3: Daftar paket (Packet List) setelah capture dihentikan.*

### 4.4 Penyaringan Protokol HTTP
Untuk mempermudah analisis, terapkan filter dengan kata kunci `http` pada display filter. Hanya paket terkait protokol HTTP yang akan muncul.

![Filter HTTP](assets/wireshark_http_filter.png)
*Gambar 4: Hasil penyaringan paket dengan ekspresi "http".*

### 4.5 Analisis Rinci Paket HTTP GET
Di sini, paket **HTTP GET** yang dikirim dari klien ke server `gaia.cs.umass.edu` dipilih. Detail protokol disajikan dalam struktur hierarki.

![Detail Paket HTTP](assets/wireshark_http_detail.png)
*Gambar 5: Rincian paket HTTP GET dengan protokol lain disembunyikan.*

**Penjelasan Rinci Paket:**
- **Frame:** Data fisik mengenai paket yang ditangkap.
- **Ethernet II:** Alamat MAC pengirim dan penerima.
- **Internet Protocol Version 4:** Alamat IP pengirim dan penerima.
- **Transmission Control Protocol:** Port pengirim dan penerima, plus nomor urut (sequence number).
- **Hypertext Transfer Protocol:** Metode permintaan (GET), host, dan user-agent.

### 4.6 Isi Paket (Hex & ASCII)
Jendela bawah menampilkan konten mentah paket dalam format heksadesimal dan ASCII.

![Konten Paket](assets/wireshark_packet_bytes.png)
*Gambar 6: Tampilan Packet Bytes dalam format Hex dan ASCII.*

---

## 5. Kesimpulan
Dari praktikum Modul 2 ini, dapat ditarik kesimpulan sebagai berikut:
1. **Wireshark** telah berhasil dipasang dan diterapkan sebagai alat *packet sniffer* untuk menangkap trafik jaringan.
2. Wireshark dilengkapi dengan komponen kunci seperti *Packet Listing*, *Packet Details*, dan *Packet Bytes* yang memfasilitasi analisis protokol multilayer.
3. Fitur **Display Filter** sangat membantu dalam menyaring paket tertentu, misalnya hanya trafik HTTP, dari sekian banyak paket yang ditangkap.
4. Praktikum ini menggambarkan bahwa aktivitas sederhana seperti membuka halaman web melibatkan berbagai protokol lapisan bawah (Ethernet, IP, TCP) sebelum sampai ke lapisan aplikasi (HTTP).
5. Penguasaan interface Wireshark merupakan fondasi penting untuk modul berikutnya seperti HTTP, DNS, TCP, UDP, dan lainnya.

---

## 6. Daftar Pustaka
1. Kurose, J.F., & Ross, K.W. (2021). *Computer Networking: A Top-Down Approach*, 8th Edition. Pearson.
2. Universitas Telkom. (2026). *Modul Praktikum Jaringan Komputer Semester Genap 2025/2026*. Fakultas Informatika.
3. Wireshark Foundation. (2024). *Wireshark User's Guide*. Retrieved from https://www.wireshark.org/docs/
