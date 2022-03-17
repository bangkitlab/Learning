# 🧪 Codelab 1

Pada kelas ini kita akan mengembangkan sebuah aplikasi yang menampilkan tempat-tempat wisata di Bandung. Hasil akhir dari keseluruhan codelab akan seperti berikut:

[![20210425131945a4abeea012bc2e46e31538884424008b.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425131945a4abeea012bc2e46e31538884424008b.gif)](https://www.dicoding.com/academies/159/tutorials/6502#)

Dalam codelab pertama ini kita akan membuat sebuah tampilan yang menggabungkan semua widget-widget yang sebelumnya kita pelajari. Tampilannya adalah seperti berikut:

[![202104251320085fde1442232fc33aa20602bef39b2eb2.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251320085fde1442232fc33aa20602bef39b2eb2.png)](https://www.dicoding.com/academies/159/tutorials/6502#)

Sebelum kita membuat tampilan di atas, kita akan bedah terlebih dahulu _layout_-nya.

Pada layout di atas kita dapat memetakan widget-widget dalam bentuk diagram seperti di bawah ini:

[![20200615123022ba51f3071b1abe12d3704a7ce5db8b4d.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615123022ba51f3071b1abe12d3704a7ce5db8b4d.png)](https://www.dicoding.com/academies/159/tutorials/6502#)

1. Buat project Flutter baru dan berikan nama yang sesuai, misalnya wisata\_bandung. Hapus kode aplikasi counter yang diberikan ketika project dibuat.
2.  Tuliskan kode dasar yang menampilkan widget <mark style="color:yellow;">`MaterialApp`</mark> seperti berikut:

    ```
    import 'package:flutter/material.dart';
     
    void main() => runApp(MyApp());
     
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Wisata Bandung',
          theme: ThemeData(),
        );
      }
    }
    ```
3.  Lalu kita akan membuat kode untuk susunan widget sesuai diagram yang telah kita buat. Untuk membuat kode kita lebih rapi kita akan membuat kelas Stateless Widget baru untuk menampung kode tampilan kita. Mari namakan kelas ini <mark style="color:yellow;">`DetailScreen`</mark>.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold();
      }
    }
    ```

    Jangan lupa untuk menambahkan widget DetailScreen sebagai home dari MaterialApp.

    ```
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Wisata Bandung',
          theme: ThemeData(),
          home: DetailScreen(),
        );
      }
    }
    ```
4.  Sesuai diagram di atas, kita akan menyusun beberapa widget secara vertikal sehingga kita perlu menggunakan widget Column.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Column(),
        );
      }
    }
    ```

    Jalankan aplikasi Anda. Saat ini device atau emulator Anda memang masih belum menampilkan apa pun. Namun, kita akan memanfaatkan fitur hot reload untuk melihat perubahan-perubahan yang akan kita lakukan ke depan.
5.  Komponen pertama yang akan kita buat adalah bagian judul dari halaman. Tentunya untuk menampilkan teks kita akan menggunakan widget Text.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Column(
            children: <Widget>[
              Text('Farm House Lembang'),
            ],
          ),
        );
      }
    }
    ```
6.  Ketika Anda menyimpan project atau menjalankan hot reload, tampilan aplikasi Anda sekarang mungkin tidak sesuai dengan keinginan, seperti teks terlalu ke atas dan juga terlalu kecil.\
    [![202104251322093fcb5140ee8a825f4ec2150ec6b9fe84.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251322093fcb5140ee8a825f4ec2150ec6b9fe84.jpeg)](https://www.dicoding.com/academies/159/tutorials/6502#)\
    Untuk itulah kita perlu membungkus widget Text ke dalam Container supaya kita dapat memberikan property seperti margin atau padding. Jika Anda menggunakan IDE Android Studio, Anda dapat memanfaatkan shortcut **Alt+Enter** untuk membungkus widget ke widget \


    ![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251322465819b8c1d2b88fdd3ec6d029a0689961.gif)
7.  Tambahkan margin atas supaya teks memiliki jarak terhadap bagian atas layar.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Column(
            children: <Widget>[
              Container(
                margin: EdgeInsets.only(top: 16.0),
                child: Text('Farm House Lembang'),
              ),
            ],
          ),
        );
      }
    }
    ```

    Pada kode di atas kita hanya memberikan margin atas sebesar sebesar 16.0. Anda dapat memanfaatkan metode <mark style="color:yellow;">`EdgeInsets`</mark> lain seperti <mark style="color:yellow;">`all()`</mark> untuk memberikan margin ke semua sisi atau <mark style="color:yellow;">`symmetric()`</mark> apabila Anda ingin memberikan margin ke sisi vertikal atau horizontal.
8.  Jika Anda kesulitan menentukan margin atas, khususnya pada perangkat yang memiliki notch yang umumnya memiliki status bar yang lebih besar, Anda dapat memanfaatkan widget <mark style="color:yellow;">`SafeArea`</mark>.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              children: <Widget>[
                Container(
                  margin: EdgeInsets.only(top: 16.0),
                  child: Text('Farm House Lembang'),
                )
              ],
            ),
          ),
        );
      }
    }
    ```

    Widget ini akan memberikan padding yang secara otomatis menyesuaikan perangkat yang digunakan.\
    [![20210425132439c166c585093014ef522ac1457bf9e448.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425132439c166c585093014ef522ac1457bf9e448.png)](https://www.dicoding.com/academies/159/tutorials/6502#)
9.  Selanjutnya, sesuai contoh kita akan membuat teks judul berada di tengah. Tambahkan parameter atau properti <mark style="color:yellow;">`textAlign`</mark> pada widget <mark style="color:yellow;">`Text`</mark>.

    ```
    Container(
      margin: EdgeInsets.only(top: 16.0),
      child: Text(
        'Farm House Lembang',
        textAlign: TextAlign.center,
        style: TextStyle(
          fontSize: 30.0,
          fontWeight: FontWeight.bold,
        ),
      ),
    ),
    ```

    Lakukan hot reload. Tidak ada perubahan, apa sebabnya? Jika menggunakan Android Studio Anda dapat memanfaatkan fitur Flutter Inspector untuk melihat layout widget di dalam aplikasi.\


    ![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425132539b83ca0cdc01669f05d97fbb95f9e5c4c.gif)

    \
    Dari gambar di atas bisa kita lihat ternyata layout aplikasi kita tidak penuh hingga seluruh halaman. Ini disebabkan sisi horizontal dari Column hanya menyesuaikan dengan konten yang ada di dalamnya. Untuk memaksimalkan ukuran lebar dari Column, tambahkan kode berikut:

    ```
    body: SafeArea(
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: <Widget>[
          Container(
            margin: EdgeInsets.only(top: 16.0),
            child: Text(
              'Farm House Lembang',
              textAlign: TextAlign.center,
              style: TextStyle(
                fontSize: 30.0,
                fontWeight: FontWeight.bold,
              ),
            ),
          ),
        ],
      ),
    ),
    ```
10. Setelah menyelesaikan judul, selanjutnya kita akan membuat bagian kedua yaitu informasi dari tempat wisata.\
    [![20210425132634936b9f6bc4d83c33d804ba3918392edd.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425132634936b9f6bc4d83c33d804ba3918392edd.jpeg)](https://www.dicoding.com/academies/159/tutorials/6502#)\
    Seperti yang terlihat kita perlu menyusun widget secara horizontal dan vertikal. Mari tambahkan child kedua dari Column dengan sebuah Container berisi Row. Tambahkan juga margin pada sisi atas dan bawah untuk memberikan jarak antar widget.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Container(...),
                Container(
                  margin: EdgeInsets.symmetric(vertical: 16.0),
                  child: Row(
                    children: <Widget>[],
                  ),
                ),
              ],
            ),
          ),
        );
      }
    }
    ```
11. Buat widget Column untuk menyusun Icon dan Text.

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Container(...),
                Container(
                  margin: EdgeInsets.symmetric(vertical: 16.0),
                  child: Row(
                    children: <Widget>[
                      Column(
                        children: <Widget>[
                          Icon(Icons.calendar_today),
                          Text('Open Everyday'),
                        ],
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

    Jika Anda merasa jarak antara Icon dan Text terlalu rapat, Anda dapat menambahkan widget <mark style="color:yellow;">`SizedBox`</mark> untuk membuat “kotak” yang berguna untuk memberikan jarak.

    ```
    Column(
      children: <Widget>[
        Icon(Icons.calendar_today),
        SizedBox(height: 8.0),
        Text('Open Everyday'),
      ],
    ),
    ```
12. Selanjutnya sebagai tantangan, lengkapilah informasi tempat wisata dengan pasangan ikon dan teks sesuai contoh yang diberikan.\
    [![202104251342330837dda51f8fac145cf27983934d5640.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251342330837dda51f8fac145cf27983934d5640.jpeg)](https://www.dicoding.com/academies/159/tutorials/6502#)
13. Untuk menyusun Row seperti di atas, pastikan menggunakan mainAxisAlignment seperti ini:

    ```
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Container(...),
                Container(
                  margin: EdgeInsets.symmetric(vertical: 16.0),
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                    children: <Widget>[
                      Column(...),
                      Column(...),
                      Column(...)
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
14. Pada langkah ini harusnya Anda sudah bisa menampilkan teks deskripsi sesuai langkah yang diberikan sebelumnya. Anda cukup menambahkan widget <mark style="color:yellow;">`Container`</mark> dan <mark style="color:yellow;">`Text`</mark> untuk menampilkan konten deskripsi. Anda juga dapat menambahkan style sesuai selera Anda.

    ```
    Container(
      padding: EdgeInsets.all(16.0),
      child: Text(
        'Berada di jalur utama Bandung-Lembang, Farm House menjadi objek wisata yang tidak pernah sepi pengunjung. Selain karena letaknya strategis, kawasan ini juga menghadirkan nuansa wisata khas Eropa. Semua itu diterapkan dalam bentuk spot swafoto Instagramable.',
        textAlign: TextAlign.center,
        style: TextStyle(fontSize: 16.0),
      ),
    ),
    ```
15. Keseluruhan kode Anda akan seperti berikut:

    ```
    import 'package:flutter/material.dart';
     
    void main() => runApp(MyApp());
     
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Wisata Bandung',
          theme: ThemeData(),
          home: DetailScreen(),
        );
      }
    }
     
    class DetailScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: SafeArea(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Container(
                  margin: EdgeInsets.only(top: 16.0),
                  child: Text(
                    'Farm House Lembang',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 30.0,
                      fontWeight: FontWeight.bold,
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
                          Text('Open Everyday'),
                        ],
                      ),
                      Column(
                        children: <Widget>[
                          Icon(Icons.access_time),
                          SizedBox(height: 8.0),
                          Text('09:00 - 20:00'),
                        ],
                      ),
                      Column(
                        children: <Widget>[
                          Icon(Icons.monetization_on),
                          SizedBox(height: 8.0),
                          Text('RP 25.000'),
                        ],
                      ),
                    ],
                  ),
                ),
                Container(
                  padding: EdgeInsets.all(16.0),
                  child: Text(
                    'Berada di jalur utama Bandung-Lembang, Farm House menjadi objek wisata yang tidak pernah sepi pengunjung. Selain karena letaknya strategis, kawasan ini juga menghadirkan nuansa wisata khas Eropa. Semua itu diterapkan dalam bentuk spot swafoto Instagramable.',
                    textAlign: TextAlign.center,
                    style: TextStyle(fontSize: 16.0),
                  ),
                )
              ],
            ),
          ),
        );
      }
    }
    ```

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251322465819b8c1d2b88fdd3ec6d029a0689961.gif)

Anda juga dapat mengunduh keseluruhan kodenya pada tautan berikut: [https://github.com/dicodingacademy/a159-flutter-pemula-labs](https://github.com/dicodingacademy/a159-flutter-pemula-labs)
