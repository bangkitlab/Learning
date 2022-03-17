# 📖 Apa itu Flutter

{% hint style="info" %}
### **Pembaruan!**

Artikel ini diperbarui pada tanggal 26 April 2021. Pembaruan terakhir adalah: **Flutter 2**.\
[_Lihat riwayat »_](https://www.dicoding.com/academies/159/tutorials/6444#changelog-modal)
{% endhint %}

### Apa itu Flutter

Flutter adalah SDK (_Software Development Kit_) yang dikembangkan oleh Google untuk membuat aplikasi yang bagus dan bisa berjalan pada berbagai platform. Flutter 2 yang merupakan versi terbaru memberikan dukungan pada Anda untuk membangun aplikasi pada sistem operasi Android, iOS, Web, Windows, Linux, dan MacOS. Dengan ini, Anda cukup sekali _coding_ atau dikenal dengan _single codebase_. Flutter juga sudah digunakan oleh banyak _developer_ maupun organisasi di seluruh dunia, selain itu Flutter bersifat _open source_.

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061515270160d84634647daaadd3e949fb3875d364.png)

### Mengapa Flutter?

Flutter berbeda dari kebanyakan SDK Cross-platform lainnya untuk membuat aplikasi _mobile_. Untuk menarik _widget_, Flutter bukan menggunakan _WebView_ maupun _widget OEM_, melainkan mesin _rendering_ berkinerja tinggi. Flutter dapat digunakan bersamaan dengan aplikasi _native_ yang sudah ada atau digunakan secara keseluruhan untuk aplikasi baru.&#x20;

Ada beberapa kelebihan dari Flutter, antara lain:

1. **Flutter memungkinkan kita untuk membuat aplikasi yang indah (beautiful)**\
   Desainer dapat dengan bebas berkreasi tanpa adanya banyak batasan dari _framework_. Flutter juga dapat mengontrol setiap piksel yang ada di layar, sehingga memudahkan dalam membuat animasi. Flutter menyediakan banyak komponen _material design_ yang dapat berjalan baik pada Android, iOS, dan web.
2. **Flutter berjalan dengan sangat cepat (fast)**\
   Flutter menggunakan _graphic engine_ bernama _Skia-2D_ yang juga digunakan pada Chrome dan Android. Kode Flutter menggunakan bahasa Dart, yang memungkinkan untuk dikompilasi ke kode _native_ 32-bit dan 64-bit ARM untuk iOS dan Android.
3. **Flutter sangat produktif (productive)**\
   Flutter memiliki fitur hot-reload yang memungkinkan Anda untuk melihat hasil kompilasi secara _real-time_. Dengan _hot-reload_, Anda dapat dengan mudah melihat perubahan kode pada perangkat, tanpa perlu menunggu _restart_ dan kehilangan _state_.
4. **Flutter bersifat terbuka (open source)**\
   Flutter adalah proyek _open source_ dengan lisensi BSD. Kode yang ada di Flutter berasal dari kontribusi ratusan developer dari seluruh dunia. Banyak _plugin_ yang sudah dibuat oleh developer. Anda dapat ikut berkontribusi mengembangkan Flutter dengan melaporkan _bug/issue_ atau ikut memperbaiki kode yang sudah ada. _Source code_ dari Flutter dapat Anda temukan pada tautan [https://github.com/flutter/flutter](https://github.com/flutter/flutter).

### Sejarah Perkembangan Flutter

Versi pertama dari Flutter bernama Sky yang diumumkan pada Dart Developer Summit 2015. Pada saat itu, Sky hanya berjalan pada sistem operasi Android.&#x20;

Lalu, pada Google Developer Days di Shanghai, Google mengumumkan Flutter versi Release Preview 2 yang merupakan rilis sebelum versi _stable_ 1.0.

Pada 3 Maret 2021 kemarin, Flutter mengumumkan versi Flutter 2 dengan pembaruan yang cukup besar, yaitu dukungan Flutter untuk platform web dan desktop (Windows, Linux, dan macOS) yang memasuki versi _stable_.

Sejak rilis beta pertama, Flutter sudah banyak digunakan untuk mengembangkan aplikasi _mobile_. Contohnya adalah perusahaan Abbey Road Studios, Alibaba, Capital One, Groupon, Hamilton, JD.com, Philips Hue, Reflectly, Tencent, dan GITS Indonesia.

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615152739df52d843cff1af48e2d1929c2e0378af.png)

### Dart&#x20;

Seperti yang telah kita ketahui, aplikasi Flutter ditulis dengan bahasa Dart. Seharusnya Anda telah mempelajari tentang fundamental Dart di kelas [Memulai Pemrograman dengan Dart](https://www.dicoding.com/academies/191). Untuk menyegarkan kembali ingatan Anda kami akan mengulas sedikit tentang Dart.

Bahasa pemrograman Dart merupakan bahasa pemrograman _general-purpose_ yang dirancang oleh Lars Bak dan Kasper Lund. Bahasa pemrograman ini dikembangkan sebagai bahasa pemrograman aplikasi yang dapat dengan mudah dipelajari dan disebarkan.

Bahasa pemrograman besutan Google ini dapat digunakan untuk mengembangkan berbagai macam platform termasuk di dalamnya adalah web, aplikasi mobile, server, dan perangkat yang mengusung teknologi _Internet of Things_ (IoT).

Bahasa pemrograman tersebut dapat digunakan untuk mengembangkan aplikasi yang dijalankan pada berbagai macam peramban (browser) modern. Dart juga dapat digunakan untuk mengembangkan aplikasi dari _codebase_ tunggal menjadi aplikasi Android maupun iOS.

Bahasa pemrograman Dart dapat digunakan secara bebas oleh para developer karena bahasa ini dirilis secara _open-source_ oleh Google di bawah lisensi BSD. Bahasa pemrograman Dart merupakan bahasa pemrograman berbasis kelas dan berorientasi terhadap objek dengan menggunakan _Syntax_ bahasa pemrograman C.

Bahasa ini dikenalkan oleh Google sebagai pengganti bahasa pemrograman JavaScript, akan tetapi secara opsional bahasa ini dapat dikompilasi ke dalam JavaScript dengan menggunakan _Dart-to-JavaScript compiler_. Sedikit berbeda dengan bahasa pemrograman JavaScript yang bertipe dinamis, bahasa pemrograman Dart merupakan bahasa pemrograman bertipe statis.

Oke, sampai sini kita telah mempelajari tentang apa itu Flutter, termasuk sejarah dan kenapa kita perlu belajar mengembangkan aplikasi dengan Flutter. Di kelas ini Anda akan belajar dasar pengembangan aplikasi Flutter, seperti _package_, _widget_ yang umum digunakan, cara berpindah halaman menggunakan Navigation, hingga proses _build_ menjadi APK yang bisa diinstal pada smartphone Anda

\


> Catatan: Materi-materi di kelas ini akan disampaikan dalam banyak opsi, mulai dari sistem operasi (OS), platform Android atau iOS, dan Integrated Development Environment (IDE). Silakan sesuaikan dengan spesifikasi hardware/software Anda dan lewatilah materi yang dirasa tidak diperlukan.&#x20;

Untuk lulus dari kelas ini cukup dengan mengirimkan submission dari satu platform saja, misal Anda memilih platform Android maka tidak perlu mengirimkan versi iOS atau webnya.&#x20;

Mari kita lanjut ke materi selanjutnya, yaitu instalasi Flutter.&#x20;
