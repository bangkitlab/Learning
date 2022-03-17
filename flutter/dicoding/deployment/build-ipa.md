# 📖 Build IPA

> Catatan: Build .IPA hanya bisa dijalankan dengan mendaftar akun Apple Developer Program. Silakan baca informasi tentang Apple Developer Program di sini [https://developer.apple.com/programs/](https://developer.apple.com/programs/).
>
> Untuk lulus dari kelas ini, tidak diwajibkan untuk bisa build .IPA.

Pada materi ini kita akan mempelajari bagaimana melakukan _build_ aplikasi Flutter menjadi berkas **.ipa** yang dapat dijalankan pada perangkat iOS. Sebelum melakukan _build_, ada beberapa hal yang perlu kita atur seperti nama dan ikon aplikasi

### Setting Nama Aplikasi

Untuk mengatur nama aplikasi buka berkas **Info.plist** pada direktori **/ios/Runner/**. Konfigurasi untuk nama aplikasi dapat Anda temukan dan ubah pada **key Bundle Name**.

```
<key>CFBundleName</key>
<string>builder</string>
```

Atau Anda bisa gunakan library [berikut](https://pub.dev/packages/flutter\_launcher\_name) untuk men-_generate_ nama aplikasi melalui **pubspec.yaml**.

### Setting Ikon Aplikasi

Sama seperti perangkat Android, layar untuk perangkat iPhone juga terbagi ke dalam berbagai ukuran. Sehingga diperlukan juga ukuran ikon yang berbeda. Untuk membuat berbagai ukuran ikon untuk iOS, Anda dapat memanfaatkan website seperti [https://appicon.co/](https://appicon.co) atau yang lainnya. Website ini juga bisa digunakan untuk membuat ikon aplikasi Android. Perlu Anda perhatikan bahwa untuk icon pada iOS Anda tidak dapat membuatnya transparant. Alih-alih, Anda harus membuat icon tersebut penuh dengan warna&#x20;

[![20200615175755d214ec5285ddf91c7ed4c8c2d794c17e.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615175755d214ec5285ddf91c7ed4c8c2d794c17e.jpeg)](https://www.dicoding.com/academies/159/tutorials/8575#)

Ketika Anda klik **Generate**, browser akan mengunduh berkas yang Anda butuhkan. Ikon untuk aplikasi iOS bisa Anda dapatkan pada folder **Assets.xcassets**.\
[![LU9\_iLjbu4Fa3rUc7WQdj9VlgisQorwF5DslXuJbKU2fHDJWE3O6HcUh0VDmberZQqbRItq4kS3N6FF5Ejqj3LkFS5EujfYHMYIuNY\_F0OIjXU0SYfxv7ShYlBf3BPBK7QPIztJJ](https://lh4.googleusercontent.com/LU9\_iLjbu4Fa3rUc7WQdj9VlgisQorwF5DslXuJbKU2fHDJWE3O6HcUh0VDmberZQqbRItq4kS3N6FF5Ejqj3LkFS5EujfYHMYIuNY\_F0OIjXU0SYfxv7ShYlBf3BPBK7QPIztJJ)](https://www.dicoding.com/academies/159/tutorials/8575#)\


Selanjutnya Anda dapat mengganti folder **Assets.xcassets** yang ada pada direktori **/ios/Runner/** dengan hasil ikon yang sudah Anda _generate_. Atau Anda bisa menggunakan _library_ [berikut](https://pub.dev/packages/flutter\_launcher\_icons) untuk men-_generate_ ikon aplikasi melalui **pubspec.yaml**

### Melakukan build IPA

File IPA juga terbagi menjadi **debug**, **profile**, dan **release**. Namun untuk melakukan build aplikasi Flutter menjadi IPA hanya bisa dilakukan pada device macOS. Untuk melakukan build aplikasi menjadi **.ipa** Anda cukup membuka terminal pada editor atau IDE Anda lalu menjalankan perintah berikut:

```
flutter build ios
```

Secara default perintah di atas akan menghasilkan ipa release, sedangkan jika Anda ingin membuat versi debug atau profile, gunakan perintah:

```
flutter build ios --debug
```

Namun, bagi Anda yang tidak mempunyai perangkat Apple jangan khawatir, Anda tetap dapat men-_deploy project_ Anda ke iOS menggunakan CI/CD seperti [Codemagic](https://blog.codemagic.io/getting-started-with-codemagic/) dan [Bitrise](https://devcenter.bitrise.io/getting-started/getting-started-with-flutter-apps/).

Selamat Anda telah berhasil membuat dan _build_ _project_ Flutter di Android atau iOS. Selanjutnya Anda diharuskan untuk mengirim submission _project_ Flutter. Silakan lanjut ke materi berikutnya untuk menuju halaman submission.
