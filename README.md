# Linux Navigation Basic

Menavigasi dan mengelola file dan folder dalam filesystem merupakan kunci dalam bekerja dengan komputer. Cloud server umumnya menggunakan Linux shell yang sama dan linux command yang umum untuk bekerja dengan file dan folder. Terminal ini akan memperkenalkan beberapa skill fundamental untuk menggunakan command tersebut.

# Struktur Direktori/Folder pada linux

Struktur direktori di linux menggunakan konsep hierarki dengan direktori root ```/``` sebagai direktori dasar bagi seluruh direktori yang ada di linux. Dengan kata lain, seluruh direktori yang ada di sistem operasi linux berada dibawah direktori root ```/```. Berikut gambaran umum struktur direktori di linux.
```
「  /  」
    ├── 「             /bin          」 Essential User Command Binaries
    ├── 「             /boot         」 Static Files of the Boot Loader
    ├── 「 /dev or /devices (or both)」 Devices FIles
    ├── 「             /etc          」 Host Spesific System Configuration
    ├── 「             /home         」 User Home Directory
    ├── 「             /lib          」 Essential Shared libraries and Kernel Modules
    ├── 「             /media        」 Mount Point for Removable Media
    ├── 「             /mnt          」 Mount Point for A Temporarily Mounted Filesystems 
    ├── 「             /opt          」 Add-on Applicatoin Software Packages 
    ├── 「             /sbin         」 System Binaries
    ├── 「             /srv          」 Data for Services Provided by This System
    ├── 「             /tmp          」 Temporary Files
    ├── 「             /usr          」 (Multi-)User Utilities and Applications
                        └── 「 /usr/local 」
                                   ├── 「 /usr/local/bin   」
                                   └── 「 /usr/local/games 」
    ├── 「             /var          」 Variables Files
    ├── 「             /root         」 Home Directory for the Root User
    └── 「             /proc         」 Virtual Filesystem Documenting Kernel and Proces statusat text files

  ```


# Navigasi dan Eksplorasi

Skill paling mendasar untuk dikuasai adalah menjelajahi filesystem dan mendapatkan gambaran tentang apa yang ada di sekelilingmu

<h3>Mencari tahu kamu sedang di mana dengan command "pwd"</h3>

Saat pertama kali login ke server, kamu biasanya akan diarahkan ke direktori home dari akun user, yang dimana direktori home ini merupakan direktori utama. Direktori home adalah direktori yang disediakan untuk menyimpan file dan membuat direktori. direktori ini adalah lokasi di filesystem di mana kamu memiliki kendali penuh

Untuk mencari tahu dimana direktori home-mu di antara filesystem yang lain, kamu bisa menggunakan command ```pwd``` (print working directory). command ini menampilkan direktori yang saat ini sedang kamu akses
```
$ pwd
```
```
Output
/home/nyctoselene
```

Direktori home diberi nama sesuai dengan akun user. Direktori ini berada dalam direktori bernama ```/home```, yang berada dalam direktori tingkat atas, yang biasanya disebut direktori "root", dan diwakili oleh tanda slash tunggal ```/```

<h3>Melihat isi dari direktori menggunakan command "ls"</h3>
setelah mengetahui bagaimana cara mengetahui direktori yang sedang diakses, kamu bisa melihat isi dari direktori.

```
$ cd /usr/share
$ pwd 
```
```
Output
/usr/share
```
Saat ini direktori home-mu tidak memiliki banyak hal yang dapat dilihat, jadi tidak ada isinya. Tetapi, jika direktori nya berisi file, maka akan muncul nama-nama file tersebut

<h3>berpindah-pinidah pada Filesystem dengan command "cd"</h3>
Berikutnya adalah command untuk berpindah direktori. Ada dua cara untuk berpindah direktori menggunakan command "cd"

```
$ cd /user/share #ini merupakan cara utama yaitu dengan memberikan tanda slash awal "/" (Absolute path).
                  Absolute path menunjukkan lokasi direktori relatif terhadap direktori teratas (root).
                  Hal ini memungkinkan kita merujuk ke direktori dengan cara yang tidak ambigu dari mana pun di sistem berkas

$ cd locale      #adapun cara aalternatif yaitu tanpa memberikan tanda slash awal "/" (relative path).
                  Relative path merujuk pada direktori yang terkait dengan direktori saat ini.
                  Cara ini biasanya lebih singkat, dan terkadang lebih menguntungkan untuk berpindah ke direktorilain yang berada dalam direktori yang sama.
                  Setiap direktori di dalam direktori saat ini dapat dirujuk dengan nama tanpa tanda garis miring di depannya.
                  Sebagai contoh, command ini merujuk pada direktori locale yang ada dalam direktori /usr/share , karena command ini dijalankan pada path tersebut

Kesmipulannya, cara pertama digunakan untuk berpindah ke direktori dengan skala lebih luas, tidak terbatas oleh direktori lain
Sedangkan, cara kedua hanya bisa digunakan untuk berpindah ke direktori lain yang masih berada dalam direktori yang sama
```
Untuk kembali ke atas, berpindah ke direktori induk dari direktori saat ini, dengan menggunakan indikator titik ganda khusus. Misalnya, saat ini berada di direktori `/usr/share/locale/`. Untuk berpindah ke level atas, Ketik command:

```
$ cd ..
```
maka kamu akan berpindah ke `/usr/share/`

Kamu dapat selalu kembali ke direktori home dengan menjalankan command `cd` tanpa menentukan direktori atau dengan menjalankan command `cd ~` sebagai pengganti direktori home

```
cd ~
pwd
```
```
/home/nyctoselene
```
<h3>Menampilkan File</h3>

Sebelumnya, kamu telah belajar cara menavigasi sistem berkas. Kamu mungkin melihat beberapa File saat menggunakan command `ls` di berbagai direktori. Berbeda dengan beberapa sistem operasi, Linux dan sistem operasi Unix-sejenis lainnya mengandalkan file teks biasa untuk sebagian besar sistem. 

Cara utama untuk melihat berkas dalam tutorial ini adalah dengan command `less`. Ini disebut “pager” karena memungkinkanmu untuk scroll halaman-halaman file. Jika Command sebelumnya dieksekusi secara langsung dan mengembalikanmu ke command line, `less` adalah aplikasi yang akan terus berjalan dan menempati layar hingga Kamu keluar.

Kamu akan membuka file `/etc/services`, yang merupakan file konfigurasi yang berisi informasi layanan yang diketahui sistem:

```
$ less /etc/services
```

file akan dibuka menggunakan `less`, sehingga Kamu bisa melihat isi dari dokumen:

```
Output
# Network services, Internet style
#
# Note that it is presently the policy of IANA to assign a single well-known
# port number for both TCP and UDP; hence, officially ports have two entries
# even if the protocol doesn't support UDP operations.
#
# Updated from http://www.iana.org/assignments/port-numbers and other
# sources like http://www.freebsd.org/cgi/cvsweb.cgi/src/etc/services .
# New ports will be added on request if they have been officially assigned
# by IANA and used in the real-world or are needed by a debian package.
# If you need a huge list of used numbers please install the nmap package.

tcpmux          1/tcp                           # TCP port service multiplexer
echo            7/tcp
. . .
```
Untuk scroll, gunakan arrow up dan arrow down pada keyboard. 
Untuk mencari teks pada dokumen, kamu bisa ketik forward slash "/"diikuti dengan apa yang ingin dicari. Misalnya, untuk mencari "mail", ketik:

```
/mail
```
ini akan mencari melalui seluruh teks pada dokumen dan berhenti pada hasil pertama. Untuk mendapatkan hasil lain, ketik `n`:

```
n
```

Untuk berpindah ke hasil pencarian sebelumnya ketik `N`:

```
N
```

Untuk keluar dari `less`, ketik `q` untuk quit:

# Mengelola File dan Direktori

pada bagian ini kamu akan membuat dan mengelola file dan direktori

<h3>Membuat file menggunakan "touch"</h3>

Ada banyak command dan program yang dapat membuat file. Cara paling sederhana untuk membuat file adalah dengan command `touch`. Ini akan membuat file kosong dengan nama dan lokasi yang ditentuukan.

Pertama, pastikan kamu berada pada direktori home, karena hanya ada direktori ini alh kamu mempunyai izin untuk menyimpan file (terkecuali jika menggunakan user root). Lalu buat file bernama file1 sebagai contoh dengan mengetik:

```
$ cd
$ touch file1
```

Jika kamu cek isi dari direktori ini, kamu bisa melihat file yang baru saja dibuat:

```
Output
file1
```

Jika kamu menggunakan command `touch` pada file yang sudah ada, command tersebut akan memperbarui waktu “terakhir diubah” yang terkait dengan file tersebut. 

Kamu juga bisa membuat beberapa file sekaligus. Kamu bisa menggunakan absolute path juga. Misalnya, kamu bisa mengetik:

```
$ touch /home/nyctoselene/file2 /home/nyctoselene/file3
$ ls
```
```
Output
file1 file2 file3
```

<h3>Membuat Direktori Menggunakan "mkdir"</h3>

Mirip dengan command `touch`, command mkdir memungkinkanmu untuk membuat direktori kosong.

Misalnya, untuk membuat direktori pada direktori home denagn nama `test`, Kamu bisa mengetik:

```
$ cd 
$ mkdir test
```

Kamu bisa membuat direktori dalam direktori `test` dengan nama `contoh` dengan mengetik:

```
$ mkdir test/example
```

Agar command di atas bekerja, apstikan direktori `test` sudah ada. Agar `mkdir` dapat membuat direktori yang dibutuhkan untuk membangun direktoti yang diberikan, gunakan opsi `-p`. Opsi ini memungkinkanmu untuk membuat direktori bersarang dalam satu langkah. Kamu dapat membuat struktur yang terlihat seperti `direktori/lainnya` dengan mengetik:

```
mkdir -p direktori/lainnya
```

Command ini akan membuat direktori `direktori` terlebih dahulu, kemudian akan membuat direktori `lainnya`

<h3>Memindahkan dan Mengganti Nama File dan Direktori</h3>

Kamu bisa memindahkan file ke tujuan baru dengan command `mv`. Misalnya, kamu ingin memindakhan `file1` ke direktori `test` dengan mengetik:

```
$ mv file1 test
```

Kamu bisa memindahkan kembali ke direktori home dengan menggunakan dot spesial untuk merujuk ke direktori saat nii. Pastikan kamu berada di direktori home, lalu jalankan command `mv`:

```
$ cd
$ mv test/file1 .
```




