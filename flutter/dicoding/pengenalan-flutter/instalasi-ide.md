# 📖 Instalasi IDE

### Instalasi IDE

Anda dapat membuat aplikasi dengan Flutter menggunakan editor teks yang dikombinasikan dengan _command-line tools_. Namun, sebaiknya gunakan salah satu _plugin editor_ yang direkomendasikan untuk pengalaman yang lebih baik. Plugin ini memiliki fitur seperti penyelesaian kode, penyorotan sintaks, bantuan pengeditan _widget_, dukungan untuk menjalankan & debug, dan masih banyak lagi.

Instalasi Android Studio sangat dibutuhkan untuk membuat aplikasi Android dengan Flutter, tetapi alternatifnya instal saja Java SDK dan Android SDK sendiri.

Jika sudah menginstal Android Studio, disarankan untuk tidak menginstal Java secara terpisah dan environment Android lainnya seperti _ANDROID\_HOME_ atau _ANDROID\_SDK\_ROOT_. Jika sudah telanjur terinstal dan terjadi eror android licenses pada flutter doctor, cobalah untuk uninstall Java package tersebut.

Ikuti langkah-langkah di bawah ini untuk menambahkan plugin editor untuk Android Studio, IntelliJ, dan Visual Studio Code.

{% tabs %}
{% tab title="Android Studio\IntelliJ " %}


[![20200615153755b563af88a9ca5f50c92022e2a380f87b.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615153755b563af88a9ca5f50c92022e2a380f87b.png)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)[![202006151538447a9495d4ec318885020fe0b7ad7a090d.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151538447a9495d4ec318885020fe0b7ad7a090d.png)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)\
\
Android Studio dan IntelliJ menawarkan pengalaman IDE yang terintegrasi lengkap dengan plugin khusus untuk Flutter. Untuk mengunduh Android Studio, Anda dapat mengunjungi tautan [https://developer.android.com/studio](https://developer.android.com/studio). Sedangkan jika Anda memilih IntelliJ maka dapat melalui tautan [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/).\
\
Berikut adalah cara instalasi Flutter danplugin Dart di Android Studio/IntelliJ:\


1. Pertama, buka terlebih dahulu Android Studio/IntelliJ.
2. Jika menggunakan Android Studio, pada halaman home Anda bisa temukan **Configure** di bagian pojok kanan bawah, Jika tidak terlihat, tampilkan mode full window.\
   [![2020061511413532f28be510ba4119ad507f19c88435a1.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061511413532f28be510ba4119ad507f19c88435a1.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
3. &#x20;Pilih **Plugins**\
   [![20200615114149284bec645ff6e17209f8c778e78a3018.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615114149284bec645ff6e17209f8c778e78a3018.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)&#x20;
4. Jika menggunakan Intellij dengan MacOS langkahnya **Android Studio > Preferences… > Plugins**\
   [![202006151141107db34f72ffbd2e1de9bc6c1d7072944f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151141107db34f72ffbd2e1de9bc6c1d7072944f.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
5. Kemudian ketik **Flutter** pada pencarian _plugins_ dan instal. Saat Anda melakukan instalasi _plugin_ Flutter maka secara otomatis Dart juga ikut terinstal
6. Jika menggunakan Intellij dengan OS Windows atau Linux langkahnya yaitu, **File > Settings > Plugins**\
   [![202006151141075cb02b7f23fb542a559b0ca9c7e9e63b.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151141075cb02b7f23fb542a559b0ca9c7e9e63b.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
7. Cari plugin Flutter dan klik Install.\
   [![2020061511410720fd6ff99a12b123722cc9c619163a12.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061511410720fd6ff99a12b123722cc9c619163a12.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
8. Klik **Yes** ketika diminta untuk menginstal plugin Dart.
9. Klik **Restart** saat diminta. Jika tidak, muat ulang secara manual aplikasi Android Studio/IntelliJ.
{% endtab %}

{% tab title="Visual Studio Code" %}


[![20200615154144ee9fc2de8882db306659a98e0be6d8bd.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615154144ee9fc2de8882db306659a98e0be6d8bd.png)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)

Visual Studio Code (VSCode) adalah editor ringan untuk mengkombinasikan baris perintah khususnya aplikasi Flutter dan dilengkapi dukungan debugging.&#x20;

Untuk mengunduh Visual Studio Code, kunjungi tautan [https://code.visualstudio.com/download](https://code.visualstudio.com/download).

Berikut adalah cara instalasi plugin Flutter dan Dart di VSCode:

1. Buka aplikasi Visual Studio Code yang telah diinstal sebelumnya.
2. Kemudian aktifkan Command Line dengan cara pilih **View > Command Pallete…**\
   [![20200615115544477f6dfb105f86dae3b30e53683ff506.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615115544477f6dfb105f86dae3b30e53683ff506.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
3. Ketik “**Install**” lalu pilih **Extensions: Install Extensions**.\
   [![202006151155447ee4294f077eb2b83e4354a6da4f4bad.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151155447ee4294f077eb2b83e4354a6da4f4bad.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
4. Atau langsung klik pada tab **Extensions** yang ada pada bagian kiri.\
   [![20200615115544fea158635cbfc255f43e33b064074fc2.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615115544fea158635cbfc255f43e33b064074fc2.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
5. Ketik “**Flutter**” pada bidang pencarian Extensions, dan pilih Flutter dalam daftar ekstensi yang tersedia. Kemudian klik tombol **Install**. Secara otomatis plugin Dart juga akan terinstal.\
   [![20200615115546978bc404266cb1d7be29a205e1edfad5.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615115546978bc404266cb1d7be29a205e1edfad5.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
6. Klik **Reload to Activate** untuk memuat ulang VSCode.

Setelah selesai, lakukan validasi plugin Flutter di VSCode dengan cara berikut :

1. Aktifkan Command Line dengan cara pilih **View>Command Pallete…**
2. Ketik “**doctor**”, lalu pilih **Flutter: Run Flutter Doctor.**\
   [![202006151155446de1efd431edf5ca2999c046b087ce9b.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151155446de1efd431edf5ca2999c046b087ce9b.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
3. Tinjau panel OUTPUT untuk melihat masalah apapun.\
   [![202006151155456a5cb0ddd903ee29bd49a354600cd19d.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151155456a5cb0ddd903ee29bd49a354600cd19d.jpeg)](https://www.dicoding.com/academies/159/tutorials/6451?from=6446#)
{% endtab %}
{% endtabs %}



### Instalasi XCode + Simulator

Untuk menjalankan aplikasi Flutter di dalam iOS, diperlukan instalasi XCode terlebih dahulu. XCode adalah IDE yang digunakan untuk mengembangkan dan men-deploy aplikasi iOS.

Yang harus dilakukan untuk mengembangkan aplikasi iOS menggunakan Flutter adalah:&#x20;

1. Unduh XCode, bisa Anda unduh langsung dari AppStore.
2.  Buka terminal dan masukkan perintah di bawah ini:Perintah ini akan memastikan bahwa operasi command-line tools di XCode akan menggunakan versi terbarunya.

    ```
    sudo xcode-select --switch /Applications/Xcode.app/Contents/Developersudo xcodebuild -runFirstLaunch
    ```
3.  Terakhir, sign XCode license agreement-nya dengan membuka XCode dan konfirmasi. Atau bisa juga sign dengan menggunakan terminal dan jalankan perintah ini:

    ```
    sudo xcodebuild -license
    ```

Pastikan juga untuk selalu mengunduh dan memperbarui versi XCode Anda, karena Flutter tidak support versi XCode yang lama.

> **Catatan:** Perlu diketahui bahwa XCode di sini hanya dibutuhkan untuk proses debugging dan deployment saja. Untuk saat ini belum bisa digunakan untuk editing kode program aplikasi Flutter di dalam XCode.

Jadi jika Anda ingin mengembangkan aplikasi iOS menggunakan Flutter, yang disarankan adalah:

* Instalasi Android Studio atau Visual Studio Code.
* Tetap instalasi XCode.
* Lakukan editing kode program di Android Studio atau VIsual Studio Code.
* Jalankan aplikasi menggunakan Android Studio, Visual Studio Code, atau terminal/cmd.
