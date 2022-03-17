# 📖 Pengenalan Dasar-Dasar Flutter

### Pengenalan Dasar-Dasar Flutter

Sebelumnya kita telah belajar bagaimana cara menginstal Flutter pada komputer dan menjalankan aplikasi Flutter untuk pertama kalinya. Nah, kali ini kita akan mempelajari struktur _project_ Flutter dan membuat aplikasi pertama kita. Mari kita simak uraian berikut ini.

### Struktur Project Flutter

Setelah membuat _project_ Flutter pertama kali, flutter akan membuatkan struktur _project_. Ketika membuka folder _project_ Flutter pada berkas explorer, kita akan mendapati folder-folder seperti berikut:\
[![2020061209403347ce68632ed2f31ed6b8be9f67cc0e57.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061209403347ce68632ed2f31ed6b8be9f67cc0e57.jpeg)](https://www.dicoding.com/academies/159/tutorials/6454#)

Untuk tingkat pemula kita tidak perlu mengetahui seluk-beluk struktur _project_ secara mendetail. Di sini Anda hanya cukup mengenal beberapa dari folder-folder tersebut.

Berikut beberapa folder yang harus Anda ketahui:

* **android/**\
  Folder ini merupakan tempat Anda untuk mengatur konfigurasi untuk aplikasi android. Di dalamnya terdapat file gradle, AndroidManifest, dan lain-lain. File-file tersebut sangat umum ketika Anda membuat aplikasi android native (menggunakan bahasa pemrograman Java atau Kotlin), nanti Anda akan melakukan beberapa setting pada folder android seiring waktu.
* **ios/**\
  Sama halnya dengan folder android, hanya saja ini untuk iOS. Folder ini merupakan tempat konfigurasi untuk aplikasi iOS. Ketika kita hendak membuat project flutter yang dapat berjalan pada iPhone, Anda akan berkutat dengan folder ini.
* **build/**\
  Ketika Anda melakukan build project flutter, hasil build akan ada pada folder ini. Sebagai contoh, ketika Anda ingin membuat file APK untuk project flutter, maka hasil file tersebut ada dalam folder ini. Folder ini hanya akan ada ketika sudah pernah mem-build project, dan akan terhapus jika menjalankan flutter clean.
* **lib/**\
  Ini merupakan folder utama ketika Anda mengerjakan project flutter. Seluruh source code flutter Anda akan berada pada folder ini.
* **test/**\
  Folder ini tempat Anda menyimpan source code testing. Untuk pemula tidak akan berkutat pada folder ini.
