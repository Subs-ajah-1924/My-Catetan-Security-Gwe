**Networking** adalah proses menghubungkan dua atau lebih perangkat supaya bisa salaing berkomunikasi dan bertukar data dan untuk menghubungkannya kita membutuhkan internet.internet adalah jaringan besar berupa kabel yang tersebar di seluruh dunia yang digunakan untuk jalan untuk setiap perangkat berkomunikasi.

alur komunikasi,misal buka web google.com di browser

**ENCAPSULATION**
- application layer
user akan mengetikan nama dns url google.com, lalu browser akanmembuat data req sesuai dengan kemauan client
- presentation layer 
data akan di format,misal di encrypt oleh protocol yang sesuai,misal TSL /SSL
- session layer 
lalu browser akan memastikan koneksi tersedia,berhasil dan menutup koneksi jika komunikasi sudah selesai.
- Transport layer
lalu data akan dikirimkan ke server tujuan oleh transport protocol biasanya TCP/UDP.layer ini menentukan protocol(Kurir) mana yang akan dipakai,menentukan port dan mengatur aliran pengiriman data.port disini digunakan untuk identitas dari apliaksi/web tersebut.misal HTTP = 80 ,HTTPS = 443.jika data akan di pecah menjadi bagian kecil kecil(segment) lalu akan dirakit ulang saat data sudah sampai
- Netwrok Layer 
lalu sistem akan menentukan IP(alamat) tujuan dan IP sumber dan dimadukkan ke header pada setiap segmen data.setelah itu sistem akan menentukan jalur mana yang terbaik untuk menuju Ip tujuan,setelah itu data akan diubah menjadi packet 
- Data Link Layer
lalu sistem akan menentukan MAC address dari router untuk menjadi alamat fisik untuk layer bawah berkomunikasi.proses tersebut di sebut framing.setlah itu data dikirim ke hop selanjutnya
- Physical Layer
setelah menerima data frame,data tersebut di ubah menjadi binary , lalu hardware akan mengubahnya menjadi sebuah sinyal dan sinyAl tersebut dikirim ke MAC yang ada di data

**DE - ENCAPSULATION**

kebalikannya