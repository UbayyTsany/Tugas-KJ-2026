Tugas 1: Bab 1 Pengantar Jaringan & Standar Protokol Wi-Fi
A. Pengantar Jaringan Internet
Jaringan komputer adalah kumpulan perangkat (node) yang saling terhubung untuk berbagi sumber daya, data, dan informasi. Berdasarkan cakupan geografisnya, jaringan dibagi menjadi:

LAN (Local Area Network): Jaringan dalam area terbatas (gedung, kantor, kampus).

MAN (Metropolitan Area Network): Jaringan yang mencakup suatu kota.

WAN (Wide Area Network): Jaringan skala besar yang melintasi wilayah geografis negara/benua (Internet).

B. Standar Protokol Teknologi Wi-Fi (IEEE 802.11)
Wi-Fi beroperasi berdasarkan standar dari IEEE (Institute of Electrical and Electronics Engineers). Berikut adalah evolusi protokol Wi-Fi:

802.11b (Wi-Fi 1 - 1999): Frekuensi 2.4 GHz, kecepatan maksimal 11 Mbps.

802.11a (Wi-Fi 2 - 1999): Frekuensi 5 GHz, kecepatan maksimal 54 Mbps.

802.11g (Wi-Fi 3 - 2003): Frekuensi 2.4 GHz, kecepatan maksimal 54 Mbps (kompatibel dengan 802.11b).

802.11n (Wi-Fi 4 - 2009): Frekuensi 2.4 GHz dan 5 GHz, menggunakan teknologi MIMO (Multiple-Input Multiple-Output), kecepatan hingga 600 Mbps.

802.11ac (Wi-Fi 5 - 2014): Frekuensi 5 GHz, beamforming, kecepatan gigabit (hingga 3.5 Gbps).

802.11ax (Wi-Fi 6 & 6E - 2019/2021): Frekuensi 2.4 GHz, 5 GHz, dan 6 GHz (untuk 6E). Menggunakan OFDMA untuk efisiensi koneksi banyak perangkat, kecepatan hingga 9.6 Gbps.

802.11be (Wi-Fi 7 - 2024): Frekuensi 2.4, 5, dan 6 GHz dengan Multi-Link Operation (MLO) dan channel width 320MHz, kecepatan teoritis melampaui 30 Gbps.

Tugas 2: Bab 2 Model OSI & TCP/IP (Bagian A, B, C)
A. Model OSI (Open Systems Interconnection)
Model referensi konseptual 7 lapis yang menstandarkan fungsi komunikasi jaringan:

Physical Layer: Mengatur transmisi bit mentah lewat media fisik (kabel, sinyal radio).

Data Link Layer: MAC Address, deteksi error, dan framing (Switch beroperasi di sini).

Network Layer: IP Address, routing paket antar jaringan berbeda (Router).

Transport Layer: Pengiriman data ujung-ke-ujung (TCP yang handal, UDP yang cepat), segmentasi, port komunikasi.

Session Layer: Membuka, menjaga, dan menutup sesi komunikasi antar aplikasi.

Presentation Layer: Enkripsi, kompresi, dan format data (JPEG, ASCII, TLS).

Application Layer: Antarmuka pengguna dan aplikasi jaringan (HTTP, FTP, SMTP, DNS).

B. Model TCP/IP (Transmission Control Protocol/Internet Protocol)
Standar aktual yang digunakan pada Internet saat ini, lebih ringkas menjadi 4 lapisan:

Network Access (Link) Layer: Setara dengan gabungan Data Link & Physical di OSI.

Internet Layer: Setara dengan Network layer (Protokol IP, ICMP).

Transport Layer: Sama dengan Transport OSI (Protokol TCP, UDP).

Application Layer: Setara dengan gabungan Application, Presentation, dan Session di OSI.

C. Proses Enkapsulasi dan Dekapsulasi
Enkapsulasi (Pengiriman): Proses di mana data bergerak dari Application ke Physical layer.Di setiap layer transport ke bawah, data dibungkus dengan header tambahan (Data $\rightarrow$ Segment $\rightarrow$ Packet $\rightarrow$ Frame $\rightarrow$ Bit).
Dekapsulasi (Penerimaan): Kebalikan dari enkapsulasi. Perangkat penerima membuka bungkusan header lapis demi lapis dari Physical naik ke Application layer untuk merakit kembali pesan asli.

Tugas 3: Visualisasi Penjumlahan Sinyal Harmonisa

Berdasarkan analisis Deret Fourier, penjumlahan sinyal sinus dengan frekuensi harmonisa ganjil ($n = 1, 3, 5, \dots$) yang amplitudonya bernilai $1/n$ akan membentuk gelombang kotak (Square Wave).
Di bawah ini adalah kode Python (menggunakan matplotlib dan numpy) untuk memvisualisasikan bagaimana gelombang sinus murni bertransformasi menjadi gelombang kotak seiring bertambahnya harmonisa ganjil.
import numpy as np
import matplotlib.pyplot as plt

# Parameter waktu (t) dari 0 hingga 2*pi
t = np.linspace(0, 2 * np.pi, 1000)

# Array harmonisa ganjil
harmonisa = [1, 3, 5, 7, 9, 15, 50]
sinyal_gabungan = np.zeros_like(t)

plt.figure(figsize=(12, 7))

# Loop penambahan sinyal harmonisa
for n in harmonisa:
    # Rumus harmonisa: (1/n) * sin(n * t)
    sinyal_gabungan += (1 / n) * np.sin(n * t)
    
#Visualisasikan setiap tahap yang signifikan
    if n in [1, 3, 5, 50]:
        label_text = f'Hingga Harmonisa {n}'
        if n == 50:
            label_text += ' (Mendekati Square Wave)'
        plt.plot(t, sinyal_gabungan.copy(), label=label_text, linewidth=1.5)

plt.title('Visualisasi Penjumlahan Sinyal Harmonisa Ganjil (Deret Fourier)', fontsize=14)
plt.xlabel('Waktu (t)', fontsize=12)
plt.ylabel('Amplitudo', fontsize=12)
plt.axhline(0, color='black', linewidth=0.8, linestyle='--')
plt.legend(loc='upper right')
plt.grid(alpha=0.4)
plt.tight_layout()
plt.show()

Tugas 4: Perhitungan Subnetting
1. 192.168.1.0/24 Dibagi 4 SubnetTarget: 4 subnet $\rightarrow 2^2 = 4$ (Pinjam 2 bit)Prefix Baru: /26 (Netmask: 255.255.255.192)Blok IP per subnet: 64

Subnet Ke-,Network IP,Range IP Valid (Usable),Broadcast IP
1,192.168.1.0,192.168.1.1 - 192.168.1.62,192.168.1.63
2,192.168.1.64,192.168.1.65 - 192.168.1.126,192.168.1.127
3,192.168.1.128,192.168.1.129 - 192.168.1.190,192.168.1.191
4,192.168.1.192,192.168.1.193 - 192.168.1.254,192.168.1.255

2. 132.10.0.0/16 Dibagi 10 Segment
Target: 10 segment $\rightarrow 2^4 = 16 \ge 10$ (Pinjam 4 bit)Prefix Baru: /20 (Netmask: 255.255.240.0)Blok IP: Berjalan kelipatan 16 di oktet ke-3.

Subnet Ke-,Network IP,Range IP Valid,Broadcast IP
1,132.10.0.0,132.10.0.1 - 132.10.15.254,132.10.15.255
2,132.10.16.0,132.10.16.1 - 132.10.31.254,132.10.31.255
...,...,...,...
10,132.10.144.0,132.10.144.1 - 132.10.159.254,132.10.159.255

3. 17.8.0.0/16 Dibagi 4 Subnet
arget: 4 subnet $\rightarrow 2^2 = 4$ (Pinjam 2 bit)
Prefix Baru: /18 (Netmask: 255.255.192.0)
Blok IP: Berjalan kelipatan 64 di oktet ke-3.

Subnet Ke-,Network IP,Range IP Valid,Broadcast IP
1,17.8.0.0,17.8.0.1 - 17.8.63.254,17.8.63.255
2,17.8.64.0,17.8.64.1 - 17.8.127.254,17.8.127.255
3,17.8.128.0,17.8.128.1 - 17.8.191.254,17.8.191.255
4,17.8.192.0,17.8.192.1 - 17.8.255.254,17.8.255.255

4. 8.32.0.0/12 Dibagi 6 Subnet
Target: 6 subnet $\rightarrow 2^3 = 8 \ge 6$ (Pinjam 3 bit)
Prefix Baru: /15 (Netmask: 255.254.0.0)
Blok IP: Berjalan kelipatan 2 di oktet ke-2.

Subnet Ke-,Network IP,Range IP Valid,Broadcast IP
1,8.32.0.0,8.32.0.1 - 8.33.255.254,8.33.255.255
2,8.34.0.0,8.34.0.1 - 8.35.255.254,8.35.255.255
3,8.36.0.0,8.36.0.1 - 8.37.255.254,8.37.255.255
4,8.38.0.0,8.38.0.1 - 8.39.255.254,8.39.255.255
5,8.40.0.0,8.40.0.1 - 8.41.255.254,8.41.255.255
6,8.42.0.0,8.42.0.1 - 8.43.255.254,8.43.255.255

Tugas 5: Analisis Cara Kerja Traceroute & Mekanisme TTL

1. Mekanisme TTL (Time-To-Live)

TTL adalah sebuah field berukuran 8-bit dalam header paket IPv4. 
Fungsinya adalah untuk mencegah paket data berputar-putar tanpa batas (looping) di dalam jaringan akibat kesalahan tabel routing.

Aturan Kerja: Setiap kali sebuah paket melewati sebuah Router (hop), nilai TTL akan dikurangi 1.
Penghapusan Paket: Jika paket mencapai Router dan nilai TTL-nya menjadi 0, Router tersebut akan membuang (drop) paket itu dan mengirimkan pesan kesalahan kembali ke pengirim berupa ICMP Time Exceeded.

2. Cara Kerja Traceroute
Traceroute memanfaatkan mekanisme TTL dan pesan ICMP untuk memetakan jalur routing dari pengirim ke tujuan.
Hop Pertama: Traceroute mengirimkan 3 paket (UDP atau ICMP Echo) ke IP tujuan dengan nilai TTL = 1. Saat sampai di Router pertama (hop 1), Router tersebut mengurangi TTL menjadi 0, lalu membuang paket dan membalas dengan ICMP Time Exceeded. Traceroute mencatat IP Router 1 beserta waktu tempuhnya.
Hop Kedua: Traceroute kemudian mengirimkan paket baru dengan TTL = 2. Paket ini melewati Router 1 (TTL sisa 1) dan mencapai Router 2. Router 2 mengurangi TTL menjadi 0, membuangnya, dan membalas pengirim. Traceroute mencatat IP Router 2.

Selesai: Proses ini terus berulang (mengirimkan TTL=3, TTL=4, dst.) hingga paket tersebut berhasil mencapai server/komputer tujuan akhir. Tujuan akhir kemudian akan merespons dengan ICMP Port Unreachable atau Echo Reply, yang menandakan bahwa pelacakan jalur (Trace) sudah komplit.

Tugas 6: Perhitungan VLSM (Variable Length Subnet Mask)Network Asal: 10.252.108.0 /24Menggunakan metode VLSM, pembagian wajib diurutkan dari kebutuhan Host yang paling besar ke yang paling kecil agar tidak terjadi tumpang tindih (overlap) IP.
LabA (Kebutuhan: 90 Host)Rumus Block Size: $2^7 = 128$ host (dikurangi 2 untuk Network & Broadcast = 126 Host Valid). Cukup untuk 90.Prefix & Netmask: /25 (255.255.255.128)
LabB (Kebutuhan: 60 Host)Rumus Block Size: $2^6 = 64$ host (dikurangi 2 = 62 Host Valid). Cukup untuk 60.Prefix & Netmask: /26 (255.255.255.192)
Administrasi (Kebutuhan: 14 Host)Rumus Block Size: $2^4 = 16$ host (dikurangi 2 = 14 Host Valid). Pas untuk 14.Prefix & Netmask: /28 (255.255.255.240)
End-point (Kebutuhan: 2 Host)Rumus Block Size: $2^2 = 4$ host (dikurangi 2 = 2 Host Valid). Pas untuk 2. (Biasanya digunakan untuk point-to-point router).Prefix & Netmask: /30 (255.255.255.252)

Nama Jaringan,Kebutuhan,Ukuran Blok,Prefix,Network IP,Range IP Valid (Usable),Broadcast IP
LabA,90 Host,128,/25,10.252.108.0,10.252.108.1 - 10.252.108.126,10.252.108.127
LabB,60 Host,64,/26,10.252.108.128,10.252.108.129 - 10.252.108.190,10.252.108.191
Administrasi,14 Host,16,/28,10.252.108.192,10.252.108.193 - 10.252.108.206,10.252.108.207
End-point,2 Host,4,/30,10.252.108.208,10.252.108.209 - 10.252.108.210,10.252.108.211
