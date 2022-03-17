# 📖 Menggunakan Packages Package Dependencies

### Menggunakan Packages Package Dependencies

Dalam pengembangan suatu aplikasi, kita tidak akan lepas dari _package/library_ (selanjutnya akan disebut _package_). _Package_ di sini merupakan sebuah kode yang dibuat untuk menyelesaikan suatu masalah. Contohnya ketika aplikasi yang kita buat membutuhkan fitur kalender sementara fitur tersebut tidak di-support oleh Flutter. Alih-alih membuat fitur kalender dari nol, kita dapat menggunakan _package_ yang telah dibuat oleh developer lain. Waktu pembuatan fitur menjadi lebih singkat!&#x20;

_Package dependencies_ merupakan sekumpulan _package_ yang dibutuhkan dalam pengembangan aplikasi. _Package_ tersebut akan diatur oleh _package manager_. Setiap bahasa pemrograman memiliki _package manager_-nya masing-masing, contohnya NodeJS memiliki npm atau yarn, Java dengan maven atau gradle, PHP dengan composer. Begitu pula dengan Flutter yang ditulis dengan bahasa dart memiliki _package manager_ bernama **pub**.

Kali ini kita akan membahas mengenai _package manager pub_, bagaimana menggunakan pub, dan di mana mencari package yang dapat digunakan untuk aplikasi kita.

### Dart Pub

Seperti yang telah kita singgung sebelumnya Pub merupakan sebuah _package manager_. Pub memiliki tugas untuk mengatur _package_ apa saja yang dibutuhkan dalam pengembangan aplikasi. Pada _package manager_ kita dapat mengatur versi _package_ yang ingin kita gunakan. Pengaturan versi sangat penting karena ketika versi flutter/dart yang digunakan tidak cocok dengan package yang kita butuhkan akan berpengaruh pada jalannya aplikasi yang kita buat. Oleh karena itu, kita harus memastikan versi yang kompatibel dengan versi Flutter yang terinstal.

Lalu bagaimana kita menggunakan pub pada project Flutter kita? Untuk mengatur _package-package_ yang akan kita gunakan, cukup buka berkas **pubspec.yaml** yang ada pada folder project.\
[![2020061211413324442ae54db346fbfad1dd1d5634112e.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061211413324442ae54db346fbfad1dd1d5634112e.jpeg)](https://www.dicoding.com/academies/159/tutorials/8566?from=6474#)

Ketika membuka berkas **pubspec.yaml** kita akan melihat begitu banyak pengaturan tapi tidak perlu khawatir karena yang kita bahas hanya mengenai _package dependencies_-nya saja.

Coba kita fokus pada kode yang ada pada **pubspec.yaml** berikut:

```
dependencies:
  flutter:
    sdk: flutter
 
  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^0.1.2
 
dev_dependencies:
  flutter_test:
    sdk: flutter
```

Kode di atas merupakan _package-package_ yang digunakan pada _project_ Flutter kita. Jika kita perhatikan, terdapat 2 jenis _dependency_ yaitu <mark style="color:yellow;">`dependencies`</mark> dan <mark style="color:yellow;">`dev_dependencies`</mark>. Fungsi dev\_dependencies digunakan untuk package-package yang berkaitan ketika proses pengembangan aplikasi Flutter, contohnya seperti flutter\_test yang digunakan untuk _testing_. Package di dalam dev\_dependencies tidak akan disertakan ketika aplikasi dirilis pada _play store_ atau _app store_. Fungsi _dependencies_ digunakan untuk _package-package_ yang langsung berkaitan dengan fitur aplikasi Flutter, contohnya seperti cupertino\_icons yang digunakan untuk mendapatkan ikon-ikon cupertino (icon untuk iOS) dan contoh lainnya seperti cloud\_firestore yang merupakan _package_ untuk firebase firestore.

Sekarang kita akan fokus pada _dependencies_. Untuk mendaftarkan _package_ yang dibutuhkan kita cukup menulis seperti di bawah ini pada bagian _dependencies_:

```
nama_package: versi
```

nama\_package merupakan nama package yang kita butuhkan, lalu disambung dengan versinya. Penulisan versi bisa langsung seperti contoh 0.1.2, atau kita menambahkan simbol caret (^) seperti ^0.1.2 . Simbol caret (^) artinya: gunakan versi _patch_ terbaru dari versi yang telah ditentukan. Jika versi nya ^0.1.2 artinya kita akan gunakan versi minimal 0.1.2 dan maksimal versi terbaru. Karena itu, jika versi _package_ tersebut sekarang sudah _update_, maka _package_ yang digunakan merupakan versi terbaru.

> **Catatan**: Hanya pada versi patch atau pada angka terakhir yaitu angka 2 jika pada contoh cupertino\_icons: ^0.1.2. Atau kita juga bisa gunakan versi minimal dan maksimal seperti contoh ‘>=0.1.2 <2.0.0’ yang artinya kita akan menggunakan versi terbaru yang ada pada saat ini yang masih berada di dalam range tersebut yaitu lebih besar sama dengan 0.1.2 dan lebih kecil dari 2.0.0.

Okay sebagai contoh kita akan menambahkan sebuah package provider yang nantinya akan kita gunakan.

```
dependencies:
  flutter:
    sdk: flutter
 
  cupertino_icons: ^0.1.2
  provider: ^4.0.1
```

Yang perlu diperhatikan dalam menulis berkas **.yaml** adalah pada indentasinya. Indentasi atau penggunaan spasi ini sangat penting karena menunjukkan urutan dan blok kode yaml yang dibaca oleh komputer. Sebagai contoh, ketika kita menambahkan _package provider_, maka kita harus menuliskannya sejajar dengan _package_ lainnya dan juga lebih menjorok ke dalam jika dibandingkan dengan _dependencies_. Ini menunjukkan bahwa _package_ seperti cupertino\_icons dan provider merupakan bagian dari dependencies yang akan ditambahkan. Setiap jaraknya adalah 2 spasi, jika _dependencies_ menempel pada ujung kiri, maka <mark style="color:yellow;">`cupertino_icons`</mark> dan <mark style="color:yellow;">`provider`</mark> berjarak 2 spasi dari ujung kiri.

Setelah menambahkan _package_ yang dibutuhkan, kita dapat melakukan **get package** tersebut. Jika Anda menggunakan visual studio code cukup simpan berkas **pubspec.yaml**, maka nanti akan secara otomatis mensinkronisasi pubspec tersebut. Atau, bisa dengan menekan tombol seperti gambar unduh pada pojok kanan atas paling kiri.\
[![20200612120353e864bb8c2c07c15cacff30cbacdf7d4f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200612120353e864bb8c2c07c15cacff30cbacdf7d4f.jpeg)](https://www.dicoding.com/academies/159/tutorials/8566?from=6474#)

Bila menggunakan Android Studio Anda cukup menekan tombol "**Pub get**" pada Android Studio seperti berikut:

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006121206080348b7f845f0f420be1d7ace23f0bd24.jpeg)

Kita juga bisa secara manual menggunakan terminal dengan menjalankan perintah flutter pub get di dalam _project_ tersebut. Setelah melakukan pub get, maka package tersebut sudah dapat digunakan.

### Tempat-tempat mencari package flutter

Flutter memiliki segudang package yang telah dibuat oleh komunitas, lantas di mana kita dapat mencari package-package untuk kita gunakan? Berikut website-website yang dapat Anda gunakan untuk mencari package.

* [https://pub.dev](https://pub.dev)\
  Website ini merupakan _web official_ untuk Anda mencari _package_.\
  \

* [https://flutterawesome.com](https://flutterawesome.com)\
  Berisi _package-package_ yang dibuat oleh komunitas, di sini banyak sekali _package_ UI keren yang dapat Anda coba.

### Private Packages

Selain menggunakan package yang ada pada pub.dev Anda juga bisa menggunakan package yang tidak dipublikasikan pada pub.dev tersebut dengan cara menggunakan url git package tersebut:

```
dependencies:
  plugin1:
    git:
      url: git://github.com/flutter/plugin1.git
```

Atau path direktori package tersebut yang tersimpan secara _offline_ di komputer Anda.

```
dependencies:
  plugin1:
    path: ../plugin1/
```
