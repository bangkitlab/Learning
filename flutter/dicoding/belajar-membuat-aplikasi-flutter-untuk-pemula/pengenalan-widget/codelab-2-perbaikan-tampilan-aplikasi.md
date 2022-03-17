# 🧪 Codelab 2: Perbaikan Tampilan Aplikasi

Setelah mempelajari beberapa materi tambahan, sekarang saatnya kita melanjutkan _project_ aplikasi wisata kita. Pada codelab ini kita akan membuat aplikasi dengan tampilan seperti berikut:

[![20210425151301613e561824a64ad9e6e0a0b737161d98.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425151301613e561824a64ad9e6e0a0b737161d98.png)](https://www.dicoding.com/academies/159/tutorials/6534#)

1. Mari kita mulai dengan membuka dan melanjutkan codelab kita sebelumnya.
2. Untuk memudahkan dalam membaca sekaligus merapikan kode, mari kita pindahkan widget atau kelas **DetailScreen** ke sebuah _file_ dart baru. Anda dapat membuat _file_ baru dengan cara **klik kanan pada folder lib -> New -> Dart File**. Berikan nama **detail\_screen.dart**.\
   [![20200615150957fd8e43b29beb5265379ca431e7fe9bc9.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615150957fd8e43b29beb5265379ca431e7fe9bc9.jpeg)](https://www.dicoding.com/academies/159/tutorials/6534#)
3.  Anda akan mendapati beberapa eror akibat adanya _library_ atau _package_ yang belum terpasang. Pada _file_ **detail\_screen.dart** tambahkan kode **import** berikut di baris paling atas untuk menggunakan _package_ material design di dalam _file_.

    ```
    import 'package:flutter/material.dart';
    ```
4.  Selanjutnya karena kita akan menggunakan _file widget_ **DetailScreen** di file **main.dart**, maka kita juga perlu melakukan **import** berkas **detail\_screen.dart** ke dalam berkasi **main.dart**.

    ```
    import 'package:wisatabandung/detail_screen.dart';
    ```
5.  Kemudian kita akan menambahkan sebuah gambar ke tampilan paling atas halaman. Gambar ini akan kita ambil dari asset. Untuk itu, kita perlu menambahkan berkas yang ingin ditampilkan ke dalam _project_ dan menambahkannya pada _file_ **pubspec.yaml**. Aset gambar dapat Anda unduh pada tautan [berikut](https://github.com/dicodingacademy/assets/raw/main/flutter\_pemula\_academy/assets\_wisata.zip).

    ```
    flutter:  
      uses-material-design: true
      assets:
        - images/
    ```

    Tambahkan widget Image di child paling atas dari Column.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Image.asset('images/farm-house.jpg'),
                Container(...),
                Container(...),
                Container(...),
              ],
            ),
          ),
        );
      }
    }
    ```

    Jalankan aplikasi Anda untuk melihat perubahan.
6.  Selanjutnya kita akan menampilkan beberapa gambar lagi di bagian bawah. Kali ini kita akan mengambil gambar melalui url. Mari kita mulai dengan satu gambar terlebih dahulu.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Image.asset('images/farm-house.jpg'),
                Container(...),
                Container(...),
                Container(...),
                Image.network(
        'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
              ],
            ),
          ),
        );
      }
    }
    ```

    Apabila gambar yang kita tampilkan terlalu besar sementara layar pada perangkat terlalu kecil, maka akan terlihat tampilan garis hitam-kuning yang menunjukkan terjadi _overflow_. Kondisi _overflow_ ini terjadi ketika konten yang kita tampilkan melebihi luas layar yang ada.\
    [![202104251514462a9b036febe87ecac2458480ad6afaae.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251514462a9b036febe87ecac2458480ad6afaae.png)](https://www.dicoding.com/academies/159/tutorials/6534#)
7.  Sebagai solusi, tentunya kita bisa mengubah ukuran dari gambar, namun tentunya tidak praktis jika kita harus mengubah ukuran setiap gambar yang ditampilkan. Tentu ada banyak sekali ukuran layar yang tersedia, bukan? Solusi lainnya yaitu dengan menerapkan scrolling. Salah satu _widget scrolling_ yang bisa kita manfaatkan adalah <mark style="color:yellow;">`SingleChildScrollView`</mark>. Widget ini membutuhkan satu child yang nantinya bisa di-_scroll_ pada layar. Pindahkan _widget Column_ ke dalam <mark style="color:yellow;">`SingleChildScrollView`</mark> supaya nantinya bisa di-_scroll_.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: SingleChildScrollView(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.stretch,
                children: <Widget>[
                  Image.asset('images/farm-house.jpg'),
                  Container(...),
                  Container(...),
                  Container(...),
                  Image.network(
                      'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
                ],
              ),
            ),
          ),
        );
      }
    }
    ```

    Jalankan _hot reload. S_eharusnya masalah _overflow_ sudah teratasi dengan adanya _scrolling_.
8.  Selanjutnya kita akan menambahkan beberapa gambar lagi yang disusun secara horizontal. Anda mungkin mengira untuk menggunakan widget Row supaya gambar bisa tersusun secara horizontal. Namun, perlu diingat bahwa kita juga memerlukan fitur scrolling agar tidak terjadi overflow. Oleh karena itu, kita akan menggunakan <mark style="color:yellow;">`ListView`</mark>. Widget ini memungkinkan kita untuk menerapkan scrolling terhadap beberapa item (children).

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: SingleChildScrollView(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.stretch,
                children: <Widget>[
                  Image.asset('images/farm-house.jpg'),
                  Container(...),
                  Container(...),
                  Container(...),
                  ListView(
                    children: [
                      Image.network(
                          'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
                      Image.network(
                          'https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg'),
                      Image.network(
                          'https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'),
                    ],
                  ),
                ],
              ),
            ),
          ),
        );
      }
    }
    ```

    Jika Anda menjalankan aplikasi atau melakukan hot reload, aplikasi Anda akan menjadi blank dan muncul pesan eror pada log. Kenapa ya? ListView diletakkan di dalam Column, di mana keduanya sama-sama memiliki atribut height yang memakan space di sepanjang layar. Sebagai solusi kita perlu memberikan ukuran tinggi yang statis terhadap ListView. Namun ListView tidak memiliki parameter height, lantas bagaimana nih? Caranya, gunakan widget lain yang memiliki parameter height. Anda dapat membungkus widget ListView ke dalam Container atau pun SizedBox. Ukuran tinggi ini nantinya juga digunakan sebagai tinggi Image yang tampil.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: SingleChildScrollView(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.stretch,
                children: <Widget>[
                  Image.asset('images/farm-house.jpg'),
                  Container(...),
                  Container(...),
                  Container(...),
                  Container(
                    height: 150,
                    child: ListView(
                      children: [
                        Image.network(
                            'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
                        Image.network(
                            'https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg'),
                        Image.network(
                            'https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'),
                      ],
                    ),
                  ),
                ],
              ),
            ),
          ),
        );
      }
    }
    ```
9.  Secara _default_ arah _scroll_ dari <mark style="color:yellow;">`ListView`</mark> adalah vertikal. Untuk mengubahnya menjadi horizontal kita cukup menambahkan parameter <mark style="color:yellow;">`scrollDirection`</mark> bernilai <mark style="color:yellow;">`Axis.horizontal`</mark>.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: SingleChildScrollView(
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.stretch,
                children: <Widget>[
                  Image.asset('images/farm-house.jpg'),
                  Container(...),
                  Container(...),
                  Container(...),
                  Container(
                    height: 150,
                    child: ListView(
                      scrollDirection: Axis.horizontal,
                      children: [
                        Image.network(
                            'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
                        Image.network(
                            'https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg'),
                        Image.network(
                            'https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'),
                      ],
                    ),
                  ),
                ],
              ),
            ),
          ),
        );
      }
    }
    ```
10. Selanjutnya, kita akan sedikit merapikan tampilan gambar supaya terlihat lebih rapi dan menarik. Tambahkan _Padding_ pada masing-masing Image supaya antar gambar tidak terlalu rapat.

    ```
    Container(
      height: 150,
      child: ListView(
        scrollDirection: Axis.horizontal,
        children: <Widget>[
          Padding(
            padding: const EdgeInsets.all(4.0),
            child: Image.network(         'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
          ),
          Padding(
            padding: const EdgeInsets.all(4.0),
            child: Image.network('https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg'),
          ),
          Padding(
           padding: const EdgeInsets.all(4.0),
           child: Image.network('https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'),
          ),
        ],
      ),
    ),
    ```
11. Bagaimana membuat gambar memiliki sudut yang membulat seperti pada contoh? Sekali lagi, dokumentasi adalah sahabat terbaik Anda dalam mengembangkan aplikasi Flutter. Anda dapat memanfaatkan mesin pencari untuk menemukan widget sesuai keinginan. Misalnya, dengan memanfaatkan Google Anda dapat menemukan bahwa ada _widget_ yang memungkinkan gambar memiliki _radius_, yaitu **ClipRRect**. Masukkan _widget Image_ Anda sebagai **child** dari **ClipRRect** dan berikan **borderRadius**, maka Anda akan mendapatkan _Image_ dengan sudut yang tak bersiku.\
    [![2021042515180371df7464d156bc7ca61496f08722a1d2.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042515180371df7464d156bc7ca61496f08722a1d2.gif)](https://www.dicoding.com/academies/159/tutorials/6534#)
12. Terakhir, kita akan menggunakan _custom Font_. Anda bebas menggunakan font kesukaan Anda. Pada contoh ini akan menggunakan font [Staatliches](https://fonts.google.com/specimen/Staatliches) dan [Oxygen](https://fonts.google.com/specimen/Oxygen). Tambahkan font yang akan digunakan ke dalam _project_ dan daftarkan pada **pubscpec.yaml**.

    ```
    fonts:
        - family: Staatliches
          fonts:
            - asset: fonts/Staatliches-Regular.ttf
        - family: Oxygen
          fonts:
            - asset: fonts/Oxygen-Regular.ttf
    ```
13. Tambahkan parameter **fontFamily** pada widget **TextStyle** untuk menerapkan _style_ pada Text.

    ```
    Container(
      margin: EdgeInsets.only(top: 16.0),
      child: Text(
        'Farm House Lembang',
        textAlign: TextAlign.center,
        style: TextStyle(
          fontSize: 30.0,
          fontFamily: 'Staatliches',
        ),
      ),
    ),

    ```
14. Jika Anda memiliki beberapa teks dengan _style_ yang sama, Anda dapat menggunakan variabel untuk menyimpan **TextStyle**dan meringkas kode.

    ```
    var informationTextStyle = TextStyle(fontFamily: 'Oxygen');
    ```

    Gunakan variabel tersebut pada masing-masing _widget_yang membutuhkan.

    ```
    children: <Widget>[
      Column(
        children: <Widget>[
          Icon(Icons.calendar_today),
          SizedBox(height: 8.0),
          Text(
            'Open Everyday',
            style: informationTextStyle,
          ),
        ],
      ),
      Column(
        children: <Widget>[
          Icon(Icons.access_time),
          SizedBox(height: 8.0),
          Text(
            '09:00 - 20:00',
            style: informationTextStyle,
          ),
        ],
      ),
      Column(
        children: <Widget>[
          Icon(Icons.monetization_on),
          SizedBox(height: 8.0),
          Text(
            'Rp 25.000',
            style: informationTextStyle,
          ),
        ],
      ),
    ],
    ```
15. Jalankan aplikasi untuk melihat hasil akhir dari codelab ini.[![2021042515193770d78a996c7312b6c878b22cde15ad6a.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042515193770d78a996c7312b6c878b22cde15ad6a.png)](https://www.dicoding.com/academies/159/tutorials/6534#)\
    Anda dapat menghapus widget SafeArea jika dirasa tampilan tanpa SafeArea jadi lebih baik.
16. Seluruh kodenya adalah seperti berikut:

    ```
    import 'package:flutter/material.dart';
     
    var informationTextStyle = TextStyle(fontFamily: 'Oxygen');
     
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SingleChildScrollView(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Image.asset('images/farm-house.jpg'),
                Container(
                  margin: EdgeInsets.only(top: 16.0),
                  child: Text(
                    'Farm House Lembang',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 30.0,
                      fontFamily: 'Staatliches',
                    ),
                  ),
                ),
                Container(
                  margin: EdgeInsets.symmetric(vertical: 16.0),
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                    children: <Widget>[
                      Column(
                        children: <Widget>[
                          Icon(Icons.calendar_today),
                          SizedBox(height: 8.0),
                          Text(
                            'Open Everyday',
                            style: informationTextStyle,
                          ),
                        ],
                      ),
                      Column(
                        children: <Widget>[
                          Icon(Icons.access_time),
                          SizedBox(height: 8.0),
                          Text(
                            '09:00 - 20:00',
                            style: informationTextStyle,
                          )
                        ],
                      ),
                      Column(
                        children: <Widget>[
                          Icon(Icons.monetization_on),
                          SizedBox(height: 8.0),
                          Text(
                            'Rp 25.000',
                            style: informationTextStyle,
                          ),
                        ],
                      )
                    ],
                  ),
                ),
                Container(
                  padding: EdgeInsets.all(16.0),
                  child: Text(
                    'Berada di jalur utama Bandung-Lembang, Farm House menjadi objek wisata yang tidak pernah sepi pengunjung. Selain karena letaknya strategis, kawasan ini juga menghadirkan nuansa wisata khas Eropa. Semua itu diterapkan dalam bentuk spot swafoto Instagramable.',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 16.0,
                      fontFamily: 'Oxygen',
                    ),
                  ),
                ),
                Container(
                  height: 150,
                  child: ListView(
                    scrollDirection: Axis.horizontal,
                    children: <Widget>[
                      Padding(
                        padding: const EdgeInsets.all(4.0),
                        child: ClipRRect(
                          borderRadius: BorderRadius.circular(10),
                          child: Image.network(
                              'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg'),
                        ),
                      ),
                      Padding(
                        padding: const EdgeInsets.all(4.0),
                        child: ClipRRect(
                          borderRadius: BorderRadius.circular(10),
                          child: Image.network(
                              'https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg'),
                        ),
                      ),
                      Padding(
                        padding: const EdgeInsets.all(4.0),
                        child: ClipRRect(
                          borderRadius: BorderRadius.circular(10),
                          child: Image.network(
                              'https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'),
                        ),
                      ),
                    ],
                  ),
                ),
              ],
            ),
          ),
        );
      }
    }
    ```

Anda juga dapat mengunduh seluruh kodenya pada tautan berikut: [https://github.com/dicodingacademy/a159-flutter-pemula-labs/tree/codelab2-final](https://github.com/dicodingacademy/a159-flutter-pemula-labs/tree/codelab2-final).
