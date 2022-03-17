# 📖 Menjalankan Project Flutter

Setelah mengetahui persiapan sebelum menjalankan _project_ di Android dan di iOS, baik itu di _emulator_ maupun _device_. Berikut cara untuk menjalankannya di beberapa IDE yang sudah dijelaskan sebelumnya.

{% tabs %}
{% tab title="Android Studio/Intelij" %}
* Temukan toolbar Android Studio seperti di bawah ini:\
  [![2020061513132096a11d10a36eac133bf67f4ca697bb8a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061513132096a11d10a36eac133bf67f4ca697bb8a.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
* Pada target selector, pilih perangkat Android untuk menjalankan aplikasi. Jika tidak ada yang terdaftar, pilih **Tools > AVD Manager** dan buat satu emulator di **AVD Manager.**\
  [![20200615131321fd1298fdababe1882bac03152118db2c.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615131321fd1298fdababe1882bac03152118db2c.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)&#x20;
* Klik ikon run pada toolbar, atau buka item menu **Run > Run ‘main.dart’**.\
  [![20200615131321f01a25178e0ebd7ea5782eccd19a4d8f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615131321f01a25178e0ebd7ea5782eccd19a4d8f.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
* Setelah build aplikasi selesai, Anda akan melihat aplikasi starter di perangkat Anda.[![202006151313216b8906b7009988b99d47340485564d9d.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151313216b8906b7009988b99d47340485564d9d.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
{% endtab %}

{% tab title="Visual Studio Code" %}
1. Temukan **Status Bar** pada bagian paling bawah jendela VSCode :\
   [![202006151313204f1973ee3d7e348c08aaaf8112b0fee6.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151313204f1973ee3d7e348c08aaaf8112b0fee6.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
2. Pilih perangkat di area **Device Selector.**\
   [![20200615131320e75ccc4a0825a6a089c3ff6d46b38226.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615131320e75ccc4a0825a6a089c3ff6d46b38226.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
   1. Jika tidak ada perangkat yang tersedia dan Anda ingin menggunakan simulator perangkat, klik **No Device** dan luncurkan simulator.
   2. Untuk menyiapkan perangkat fisik (smartphone pribadi), ikuti petunjuk khusus perangkat pada saat melakukan **Install Flutter SDK** untuk OS Anda.
3. Aktifkan **Command Line** dengan cara pilih **Run > Start Debugging** atau **tekan F5**, atau pada kode void main akan muncul **run dan debug**, atau pada tab Run di bagian kiri.\
   [![20200615131321c96e026a855bb2abac035093eddce859.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615131321c96e026a855bb2abac035093eddce859.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)\
   \
   [![202006151313223588bfdc750ed037bf828271cb3eca06.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151313223588bfdc750ed037bf828271cb3eca06.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)\
   \
   [![2020061513132104f2fc4b8e99da8dbbb4712b143653b7.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061513132104f2fc4b8e99da8dbbb4712b143653b7.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
4. Tunggu hingga aplikasi diluncurkan dan lihat progress dalam tampilan **Debug Console**.\
   [![2020061513132263e231c3944985e6a1417f9087e0ca9d.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061513132263e231c3944985e6a1417f9087e0ca9d.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
5. Setelah build aplikasi selesai, Anda akan melihat aplikasi starter di perangkat Anda.\
   [![20200615132018e5eaf6c4febc71cae4c853acf9210f73.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615132018e5eaf6c4febc71cae4c853acf9210f73.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
{% endtab %}

{% tab title="Termina & Editor" %}
1.  Periksa apakah perangkat Android sedang berjalan. Jika tidak ada yang ditampilkan, ikuti petunjuk khusus perangkat pada saat melakukan **Install Flutter SDK**untuk OS Anda.

    ```
    flutter devices
    ```
2. Masuk ke direktori di mana _project_ itu berada.
3.  Jalankan aplikasi dengan perintah berikut:

    ```
    flutter run
    ```
4. Setelah build aplikasi selesai, Anda akan melihat aplikasi starter di perangkat Anda. Selamat Anda telah berhasil menjalankan aplikasi Flutter pertama Anda!\
   [![20200615132200f52a457bc65ce853e3f53ee8af82806a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615132200f52a457bc65ce853e3f53ee8af82806a.jpeg)](https://www.dicoding.com/academies/159/tutorials/8596#)
{% endtab %}
{% endtabs %}
