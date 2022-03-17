# 📖 Menjalankan di Web

### Menjalankan di Web

Selain platform mobile, Flutter juga bisa berjalan pada web browser. Dalam proses pengembangan, untuk keperluan debugging kita perlu menggunakan [Google Chrome](https://www.google.com/chrome/) sebagai browser. Flutter 2 telah mengumumkan bahwa Flutter Web sudah memasuki versi stable sehingga bisa digunakan secara langsung. Jika menggunakan versi di bawahnya, Anda perlu mengaktifkan channel beta terlebih dahulu. Silakan ikuti langkahnya pada blog [berikut](https://www.dicoding.com/blog/ingin-bikin-web-menggunakan-flutter-yuk-kenalan-dengan-hummingbird/).

Untuk menambahkan dukungan web pada project Anda, jalankan perintah berikut melalui terminal dari lokasi project:

```
flutter create .
```

Setelah berhasil, folder web akan ditambahkan ke dalam folder project Anda. Di dalam folder ini akan berisi berkas html dan konfigurasi web lainnya. Anda bisa mencoba menjalankan aplikasi web Flutter ini dengan memilih target device chrome pada IDE yang Anda gunakan.

Android Studio:

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252011429a4508096c53449e20e76a7a33b41440.jpeg)

Visual Studio Code:

[![202104252012069a02a5b90f7d7dded25bad126016cee0.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252012069a02a5b90f7d7dded25bad126016cee0.jpeg)](https://www.dicoding.com/academies/159/tutorials/16758?from=8596#)

Ketika target device Chrome sudah terpilih seperti di atas, Anda dapat menjalankan aplikasi dengan cara yang sama seperti ketika menjalankannya pada platform mobile. Jika Anda ingin menjalankan melalui terminal, maka perintahnya adalah seperti ini:

```
flutter run -d chrome
```

Setelah proses build selesai, jendela browser akan muncul dan menampilkan aplikasi Anda:

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042520141975ec369d16f4e0b7d9bc6fec02d783ea.png)

Pada Flutter Web, perlu diperhatikan bahwa Flutter memiliki dua jenis renderer yang berbeda, keduanya antara lain:

* **HTML renderer**\
  Renderer ini menggunakan kombinasi elemen HTML, CSS, Canvas, dan SVG. Jenis renderer ini memiliki ukuran unduhan yang lebih kecil.\

* **CanvasKit renderer**\
  Renderer ini bekerja dengan cara yang sama dengan platform mobile atau desktop. CanvasKit renderer memiliki performa yang lebih tinggi, tetapi menambahkan ukuran hingga sekitar 2 MB.

Anda dapat menentukan renderer yang digunakan dengan menambahkan parameter pada _command line_, contohnya seperti berikut:

```
flutter run -d chrome --web-renderer htmlflutter run -d chrome --web-renderer canvaskit
```

Jika Anda tidak mendefinisikan parameter --web-renderer, maka renderer akan menggunakan mode auto (_default_). Opsi ini akan menggunakan HTML renderer ketika aplikasi berjalan di browser mobile dan menggunakan CanvasKit saat aplikasi berjalan di browser desktop.
