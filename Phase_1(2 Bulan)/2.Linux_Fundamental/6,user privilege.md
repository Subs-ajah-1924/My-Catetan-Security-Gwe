di dalam linux,sistem hanya melihat process ini di jalankan oleh siapa dan punya izin apa.di linux terdapat 2 aktor,yaitu **user** dan **root**.kedua aktor ini mempunyai beberapa privilege dan izin masing masing.
- **User Privilege** misal menjalankan program seperti firefox atau bash.linux akan men cap proses ini milik user(biasanya di tambah UID dan GID = 1000) lalu privilege akan nempel ke proses tersebut.misal mau bikin child proses,privilege tersebut akan di wariskan jadi sama sama user proses.misal proses nya di hack,yang di ambil hacker itu adalah proses privilege nya,bukan akun usernya.user privilege biasanya terbatas apalagi kalau berurusan dengan sistem.
- **Root Privilege** adalah tingkat privilege tertinggi di sistem.ini bisa mengubah ,menghapus ,membuat seluruh sistem.dengan privilege ini,user dapat melakukan semua yang dibatasi di user privilege

sistem biasanya melihat dulu proses tersebut milik siapa dan akan menentukan batasan batasannya.biasanya di tandai dengan UID dan GID.setiap proses memilik UID dan GID nya sendiri.UID = 0 itu milik root,sedangkan yang lain itu milik user.jika punya root privilege,sistem akan melewati permission check nya jadinya bebas.**privilege itu mengalir**.misal proses a(root) menjalankan proses b,jika tidak diturunkan secara manual privilegenya maka proses b permissionnya akan kedetek sama sebagai root dan itu akan berbehaya.

**daemon** sering kali menjadi target dari attacker karena proses ini memilik privilege sebagai root.untuk mengetasi hal tersebut,daemon di distro distro modern sudah bisa memotong siklus aliran privilege tersebut.daemon akan start sebagai root lalu setelah proses yang cukup,privilegenya akan di turunkan,jika tidak di turunkan misal ada attacker yang bisa ngambil child prosesnya aja udah wasallam 

**Capability**(root uang di pecah pecah)
linux sadar bahwa root terlalu berbahaya untuk sistemnya,lalu muncullah Capability.capability memungkinkan user dapat menggunakan beberapa privilege dari root tetapi tetap di hitung sebagai user process.contoh CAP_NET_ADMIN -> bisa mengubah network.

Proses dari capability ini biasanya memiliki dua ID,yaitu Real UID dan Effective UID.
- Real UID adalah user asli dari proses tersebut
- Effective UID adalah identitas yang akan digunakan kernel saat cek permission,biasanya menggunakan root atau user lain
jadi saat sistem membaca UID proses tersebut,itu akan kedetek sebagai root walaupun di proses dengan itu UID user privilege,contoh sudo, ping,dll.program terebut disimpat di file **setuid bit**.disinilah peluang heker dengan memanfaatkan bug di program tersebut yang dinamakan privilege escalation 

hal apik 
**command sudo** itu tidak merubah privilege user menjadi root,tetapi membuat proses dengan UID = 0,begitu prosesnya mati/selesai maka privilegenya akan menjadi user lagi  


