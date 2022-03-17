# 📖 Menjalankan Emulator Android atau iOS

### Menjalankan Emulator Android atau iOS

Sebelumnya kita telah berhasil menginstal flutter SDK, IDE, dan membuat project baru berdasarkan IDE yang digunakan. Sekarang kita akan mulai belajar cara menjalankan project Android menggunakan emulator atau device, maupun project iOS dengan menggunakan simulator.

### Menjalankan di Android

Kita akan menggunakan project Flutter yang telah dibuat sebelumnya untuk dijalankan di emulator atau device Android. Ada beberapa hal yang perlu diperhatikan untuk dapat menjalankan project-nya, uraiannya adalah sebagai berikut:

#### **Android Emulator**

Sebelum menggunakan emulator, Anda perlu memastikan beberapa syarat.&#x20;

1. Virtualization\
   Untuk menjalankan emulator di dalam Android Studio, pastikan aspek virtualization. Sistem Anda harus memenuhi persyaratan, yakni ketentuan prosesor dan sistem operasi dari laptop/PC yang Anda gunakan.
2. Processor
   1. Intel: Jika Anda menggunakan processor Intel, maka pastikan bahwa processor tersebut mendukung Intel VT-X, Intel EM64T (Intel 64), dan Execute Disable (XD) Bit functionality.\
      Processor Intel mampu menjalankan emulator di sistem operasi Windows, Linux, mau pun MacOS.
   2. AMD: Jika Anda menggunakan AMD, maka pastikan bahwa ia mendukung AMD Virtualization (AMD-V) dan Supplemental Streaming SIMD Extensions 3 atau yang biasa disebut dengan SSSE3.\
      Processor AMD hanya bisa menjalankan emulator di sistem operasi Linux.

#### **Persiapan Running menggunakan Emulator**

1. Untuk menjalankan aplikasi, klik menu **Tools** lalu pilih **AVD Manager**, kemudian akan muncul halaman seperti ini.\
   [![202006151257289cd6a72fb2c096c5f57b7b82c6418306.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151257289cd6a72fb2c096c5f57b7b82c6418306.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)\
   Mari kita coba buat emulator baru dengan memilih **Create Virtual Device**.
2. Halaman Select Hardware akan muncul.\
   Jika Anda ingin membuat spesifikasi hardware (perangkat keras) sendiri, pilih **New Hardware Profile**. Anda dapat menentukan konfigurasi hardware sesuai dengan kebutuhan Anda. Ingatlah untuk menggunakan konfigurasi emulator yang sesuai dengan kemampuan laptop atau komputer yang Anda gunakan. Setelah itu klik **Next**.
3. Halaman System Image akan muncul.\
   Pada halaman ini Anda akan memilih versi Android dari emulator yang akan Anda buat. Pilih versi yang sudah diunduh, yaitu Pie. Lihat tombol download di sebelah kanan. Anda perlu mengunduh terlebih dahulu jika ingin menggunakannya. Setelah itu klik **Next**.
4. Halaman Verify Configuration akan muncul.\
   Pada halaman ini Anda bisa mengubah konfigurasi _hardware_ yang telah ditentukan sebelumnya. Tekan tombol **Show Advanced Setting** pada bagian kiri bawah. Jika sudah selesai, klik **Finish**. Pengaturan emulator sudah selesai dan bisa langsung dijalankan. Anda dapat membuka emulatornya dengan menekan tombol hijau yang ada di sebelah kanan.

#### **Android Device**

Selain menggunakan Android Emulator, Anda juga dapat melakukan _run_ atau _debugging_ menggunakan perangkat _smartphone_ asli. Menjalankan aplikasi menggunakan perangkat fisik memiliki beberapa kelebihan jika dibandingkan dengan emulator, yaitu:

* Lebih cepat,
* Lebih ringan, dan
* Lebih mudah.

Dengan menggunakan peranti smartphone asli, kita dapat memastikan bahwa aplikasi kita berjalan dengan wajar ketika sudah sampai di tangan pengguna. Kendala dari pendekatan ini adalah beragamnya model peranti yang ada di pasaran. Namun, pembahasan mengenai hal tersebut tidak tercakup dalam kelas ini.

Mari ikuti langkah-langkah untuk menjalankan proses run atau debugging. Tampilan dari langkah berikut bisa dipastikan akan berbeda dengan peranti yang Anda pakai. Akan tetapi secara garis besar langkahnya akan sama.

1. Pastikan peranti yang akan dipakai sesuai dengan target SDK atau paling tidak mendukung versi SDK terendah yang digunakan aplikasi.
2. Buka **setting** dan masuk ke dalam menu **About**. Pada halaman menu ini, Anda perlu menemukan informasi tentang Build number.\
   [![202006151301370ce94d41ec05258908013a29945c5e7a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151301370ce94d41ec05258908013a29945c5e7a.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)[![20200615130138a856912cf4c0da2a20cb91a98f77a2dd.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615130138a856912cf4c0da2a20cb91a98f77a2dd.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)[![202006151301373cf03697adff29ea5e41adf742488b6e.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151301373cf03697adff29ea5e41adf742488b6e.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)
3. Kemudian tekan **Build number** sebanyak 7 kali.\
   [![20200615130138f12d4337d64c331fe4ce34ffdee30213.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615130138f12d4337d64c331fe4ce34ffdee30213.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)[![20200615130137316bbb6f36b96195af3ec03142732582.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615130137316bbb6f36b96195af3ec03142732582.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)
4. Kembali ke menu **setting** di awal dan akan muncul menu baru di bawah about yaitu **Developer Options**.\
   [![20200615130140a9ee6a49d93ee4affc1326bbb958db2f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615130140a9ee6a49d93ee4affc1326bbb958db2f.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)
5. Masuk ke dalam menu **Developer Options** dan pastikan opsi **USB Debugging Mode** sudah dalam keadaan **On**.\
   [![202006151301372b188edf381bb0116732376c8681c574.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151301372b188edf381bb0116732376c8681c574.jpeg)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)
6. Setelah menyelesaikan pengaturan pada peranti, peranti pun dapat dihubungkan dengan laptop atau komputer yang Anda pakai.

> **Catatan:** Beberapa vendor _smartphone_ memiliki sistem operasi yang unik. Tampilan _setting_ dan letak opsi bisa jadi berbeda dengan gambar di atas. Beberapa vendor juga mengharuskan Anda untuk mengunduh driver khusus sebelum bisa menghubungkannya ke Android Studio. Kami sarankan untuk mengunjungi website atau membaca petunjuk yang sesuai dengan vendor dari peranti Anda.

### Menjalankan di iOS

Kita akan menggunakan project Flutter yang telah dibuat sebelumnya untuk dijalankan di iOS simulator. Ada beberapa hal yang perlu diperhatikan untuk dapat menjalankan project-nya, uraiannya adalah sebagai berikut:

#### **iOS Simulator**

iOS Simulator atau Simulator adalah aplikasi yang digunakan untuk menjalankan aplikasi iOS. Simulator merupakan aplikasi bawaan dari XCode.

Selain dari Simulator, sebenarnya kita bisa menggunakan device iphone asli. Akan tetapi untuk menjalankan di device asli kita memerlukan akun Apple developer. Jadi untuk menyederhanakan masalah, di modul ini hanya akan diajarkan dengan media Simulator saja.

Ikuti langkah berikut ini untuk membuka Simulator:

1.  Buka terminal dan jalankan kode berikut ini:

    ```
    open -a Simulator
    ```
2. Aplikasi simulator akan muncul, contohnya seperti gambar di bawah ini:\
   [![20200615183418748ec5eb05066ff786da4e119f6ef1c6.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615183418748ec5eb05066ff786da4e119f6ef1c6.png)](https://www.dicoding.com/academies/159/tutorials/8591?from=8586#)
3. Pastikan Simulator yang Anda jalankan adalah 64-bit (Iphone 5 ke atas), jika belum maka ganti konfigurasinya dengan mengakses lewat Device atau **File -> Open Devices (versi terbaru)**.

> **Catatan:** Contoh di atas diambil dengan MacOS Catalina. Jika Anda menggunakan versi di bawahnya ada kemungkinan perbedaan tampilan. Jika Anda menemui masalah silakan bertanya di forum diskusi.
