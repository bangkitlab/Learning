# 📖 Project Wizard

Setelah berhasil menginstal Flutter SDK dan IDE artinya peralatan yang kita butuhkan telah siap. Bagian ini akan menjelaskan langkah-langkah untuk membuat aplikasi Flutter baru, mulai dari template, cara aplikasi, dan menggunakan "Hot Reload" setelah Anda melakukan perubahan kode aplikasi.

Pilih alat pengembangan (IDE) favorit Anda untuk menulis baris perintah, membangun, dan menjalankan aplikasi Flutter.

{% tabs %}
{% tab title="Android Studio/IntelliJ" %}
1. Buka Android Studio/IntelliJ.
2. Pilih **Create New Flutter Project**.\
   [![20210425001202296fe9cafed8e542c3b9289d3bc85e87.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425001202296fe9cafed8e542c3b9289d3bc85e87.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)
3. Pilih **FlutterApplication** sebagai jenis project, dan tekan **Next**.\
   [![20210425001246257b7eeb5e43844d19b72fcac5a8eaf6.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425001246257b7eeb5e43844d19b72fcac5a8eaf6.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)
4. Masukkan nama project yang ingin dibuat pada **Project name**. Pastikan **Flutter SDK Path** sesuai lokasi SDK. Instal SDK jika Anda belum melakukannya. Tentukan di mana project Anda disimpan pada **Project location**. Deskripsikan project Anda pada **Description**.[![202104250013119b97c5b556f7d7e6e2ac4bb267dc50ea.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104250013119b97c5b556f7d7e6e2ac4bb267dc50ea.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)\
   Jika Anda ingin membuat project dapat diakses ketika sedang offline, centang pada **Create project offline**. Klik **Next**.
5. Masukan nama paket aplikasi yang ingin dibuat pada Package name. Centang Include Kotlin support for Android code untuk membuat project Android-nya menggunakan bahasa Kotlin. Jika tidak maka akan menggunakan bahasa Java. Centang Include Swift support for iOS code untuk membuat project iOS-nya menggunakan bahasa Swift. Jika tidak maka akan menggunakan bahasa Objective-C. Klik Finish.[![202104250014087f3886a0b9defb4868b97d73ddf2022a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104250014087f3886a0b9defb4868b97d73ddf2022a.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)\
   **Catatan**: Nama paket aplikasi bersifat unik dan menjadi ID aplikasi, baik ketika dipublikasikan ke Play Store atau App Store maupun ketika dijalankan di perangkat. Kata terakhir pada nama paket akan menjadi nama pada project Flutter tersebut. Jangan gunakan nama project atau nama terakhir pada nama paket tersebut ‘flutter’ karena akan menimbulkan konflik.
6. Tunggu beberapa saat sampai Android Studio selesai menginstal SDK dan membuat project.
{% endtab %}

{% tab title="Visual Studio Code" %}
1. Buka Visual Studio Code.
2. Aktifkan Command Line dengan cara klik **View>Command Pallete…**\
   [![202006151242592eff382a1199a4a8bd473c449cbabe8e.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151242592eff382a1199a4a8bd473c449cbabe8e.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)
3. Ketik “**Flutter”** lalu pilih **Flutter: New Project**.\
   [![202006151242594a47080630a2543d7d8eb54034c7ddfc.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151242594a47080630a2543d7d8eb54034c7ddfc.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)
4. Masukkan **nama project**, dan tekan **Enter**.\
   [![20200615124258c115bbae4a5c5b7988feffc9decf8b85.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615124258c115bbae4a5c5b7988feffc9decf8b85.jpeg)](https://www.dicoding.com/academies/159/tutorials/8586?from=6451#)
5. Buat atau pilih direktori untuk folder project baru.
6. Tunggu beberapa saat sampai VSCode selesai menyiapkan project.
{% endtab %}

{% tab title="Terminal/CMD" %}
1. Buka Terminal/CMD.
2.  Gunakan perintah flutter create untuk membuat project baru:

    ```
    flutter create dicodingcd dicoding
    ```

\

{% endtab %}
{% endtabs %}





Perintah di atas membuat direktori project Flutter yang berisi aplikasi demonstrasi sederhana menggunakan Material Components.

> **Tips**: Kode Dart untuk aplikasi Anda ada di lib/main.dart. Untuk deskripsi lebih lanjut tentang apa yang dilakukan setiap blok kode, lihat komentar yang ada di dalam file tersebut.
