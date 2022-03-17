# 📖 Build APK

Project Flutter yang telah dibuat dapat kita build menjadi berkas .apk yang dapat berjalan di Android. Build APK adalah suatu proses membungkus aplikasi flutter menjadi format .apk yang nantinya untuk diinstal pada perangkat Android. Berikut tahapan ketika build aplikasi Flutter ke APK.

### AndroidManifest.xml

Sebelum mem-build APK, kita akan mengatur berkas <mark style="color:yellow;">`android/app/src/main/AndroidManifest.xml`</mark>. **AndroidManifest.xml** merupakan sebuah berkas yang berisikan informasi mengenai aplikasi Android yang akan di-_build_. Informasi-informasi tersebut berupa nama aplikasi, ikon, _permission_, _screen orientation_, dan lain-lain. Isi dari **AndroidManifest.xml** seperti berikut:

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="id.eudeka.samples">
    <application
        android:name="io.flutter.app.FlutterApplication"
        android:label="samples"
        android:icon="@mipmap/ic_launcher">
        <activity
            android:name=".MainActivity"
            android:launchMode="singleTop"
            android:theme="@style/LaunchTheme"
            android:configChanges="orientation|keyboardHidden|keyboard|screenSize|smallestScreenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
            android:hardwareAccelerated="true"
            android:windowSoftInputMode="adjustResize">
            <meta-data
              android:name="io.flutter.embedding.android.NormalTheme"
              android:resource="@style/NormalTheme"
              />
            <meta-data
              android:name="io.flutter.embedding.android.SplashScreenDrawable"
              android:resource="@drawable/launch_background"
              />
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
        <meta-data
            android:name="flutterEmbedding"
            android:value="2" />
    </application>
</manifest>
```

### Setting Nama Aplikasi

Untuk mengatur nama aplikasi, kita cukup mengubah properti <mark style="color:yellow;">`android:label`</mark> yang ada pada file **AndroidManifest.xml** seperti berikut:

```xml
<application
        android:name="io.flutter.app.FlutterApplication"
        android:label="common_widget"
        android:icon="@mipmap/ic_launcher">
```

menjadi

```xml
<application
        android:name="io.flutter.app.FlutterApplication"
        android:label="Nama Aplikasi"
        android:icon="@mipmap/ic_launcher"">
```

Isikan android:label dengan nama aplikasi yang diinginkan. Atau Anda bisa gunakan _library_ [berikut](https://pub.dev/packages/flutter\_launcher\_name) untuk menghasilkan nama aplikasi dari **pubspec.yaml**.

### Setting Ikon Aplikasi

Secara _default_ ikon aplikasi Flutter kita adalah ikon Flutter. Untuk mengubah icon aplikasi dengan mudah, kita akan mengganti gambar <mark style="color:yellow;">`ic_launcher.png`</mark> yang berada pada folder <mark style="color:yellow;">`android/app/src/main/res/`</mark> yang terbagi menjadi berbagai _mipmap_ (ukuran resolusi ikon).

Hal yang pertama kita lakukan adalah membuat ikon aplikasi dengan [Android Asset Studio](https://romannurik.github.io/AndroidAssetStudio/icons-launcher.html).

![](https://dicoding-web-img.sgp1.cdn.digitaloceanspaces.com/original/academy/dos:2cc1c2271b0aba82b3a851ea24a2f72420211021140854.jpeg)

Dengan <mark style="color:yellow;">`Android Asset Studio`</mark>, kita dapat membuat ikon aplikasi dengan mudah dan nantinya akan terbuat dalam berbagai resolusi (_mipmap_). Setelah membuat ikon sesuai dengan keinginan, tekan tombol _download_ yang ada di kanan atas.

![](https://dicoding-web-img.sgp1.cdn.digitaloceanspaces.com/original/academy/dos:74f604db01c154e4e48c9f5db588d95820211021140821.jpeg)

Setelah mengunduh, _unzip_-lah berkas tersebut dan temukan folder <mark style="color:yellow;">`res/`</mark> di dalamnya. Lalu copy folder <mark style="color:yellow;">res/</mark> ke <mark style="color:yellow;">`android/app/src/main/res/`</mark> untuk mengganti <mark style="color:yellow;">`ic_launcher.png`</mark> pada setiap _mipmap_ dengan ikon aplikasi yang baru. Atau Anda bisa gunakan _library_ [berikut](https://pub.dev/packages/flutter\_launcher\_icons) untuk menghasilkan _icon launcher_ dari **pubspec.yaml**.

### Setting Perizinan Aplikasi

Ketika aplikasi dalam mode _debug_ atau profil, perizinan internet akan secara otomatis ditambahkan. Namun ketika Anda ingin menjalankan atau membuatnya dalam mode rilis, Anda perlu menambahkan semua perizinan yang dibutuhkan pada **AndroidManifest**.

Untuk menambahkan perizinan pada aplikasi Android, Anda bisa menambahkan _tag_ **uses-permission** pada **AndroidManifest**, di dalam _tag_ _manifest_ dan sejajar _tag application._ Contohnya seperti di bawah ini:

```
<uses-permission android:name="android.permission.INTERNET"/>
```

### Melakukan Build APK

Setelah kita mengatur nama dan ikon aplikasi, langkah selanjutnya adalah melakukan _build_ aplikasi menjadi APK. Sebelumnya terdapat tiga (3) jenis mode aplikasi yang perlu diketahui, yaitu _debug_, _profile,_ dan _release_. APK _debug_ umumnya digunakan untuk pengujian dan penggunaan aplikasi secara internal. Mode _debug_ digunakan secara _default_ ketika menjalankan aplikasi menggunakan perintah **flutter run**. Sementara untuk bisa dirilis melalui Google Play Store, Anda perlu membuat APK _release_. Sedangkan mode _profile_ sama hal nya dengan _release_ hanya saja tetap dapat di-_debug_ menggunakan _tools_ seperti DevTools dan tidak dapat dijalankan di emulator atau simulator.

Pada kelas ini kita akan mempelajari bagaimana membuat APK _debug_. Caranya ialah menggunakan terminal pada Android Studio. Tekan tombol **Terminal** yang ada pada pojok kiri bawah.

![](https://dicoding-web-img.sgp1.cdn.digitaloceanspaces.com/original/academy/dos:a2426b471743e6307fdce313df22a7de20211021141027.jpeg)

Bila menggunakan Visual Studio Code pilih menu terminal yang ada pada menu kiri atas. Lalu pilih **new terminal**.

![](https://dicoding-web-img.sgp1.cdn.digitaloceanspaces.com/original/academy/dos:0b59500b5ac1f489c449459e0f2633e020211021141011.jpeg)

Jika terminal telah muncul, tuliskan perintah berikut:

```bash
flutter build apk --debug
```

Tunggu hingga proses _build_ berhasil. Setelah berhasil, hasil build yang berupa berkas **apk-debug.apk** akan terletak di folder <mark style="color:yellow;">`build/app/outputs/apk/debug/`</mark> atau akan muncul direktori tempat tersimpannya berkas ketika proses _build_ selesai pada Terminal.

Untuk bisa mem-_build_ apk release dan mengunggahnya melalui Google Play Store, Anda memerlukan _signing key_. _Signing key_ ini digunakan sebagai tanda tangan supaya aplikasi Anda lebih aman. Secara _default_ Flutter menggunakan _debug key_ sebagai _signing key_ sehingga Anda sebenarnya bisa membuat apk release dengan menjalankan perintah berikut:

```
flutter build apk
```

Namun, tentunya akan lebih baik jika Anda menggunakan signing key milik Anda sendiri. Cara untuk membuat signing key dan membuat apk release dapat Anda baca pada tautan dokumentasi berikut: [https://flutter.dev/docs/deployment/android](https://flutter.dev/docs/deployment/android).
