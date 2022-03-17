# 📖 Scaffold

_Scaffold_ merupakan sebuah widget yang digunakan untuk membuat tampilan dasar _material design_ pada aplikasi Flutter, yang dapat disebut juga dasar sebuah halaman pada aplikasi Flutter. Tampilan dasar tersebut seperti berikut:

[![2020061215231881218dafb3a91c5b31f944bd76e5aef4.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061215231881218dafb3a91c5b31f944bd76e5aef4.jpeg)](https://www.dicoding.com/academies/159/tutorials/6480#)

Tampilan di atas merupakan implementasi dari Scaffold. Scaffold di atas memiliki 3 bagian yaitu **AppBar**, **Body**, dan **FloatingActionButton**. Ketiga bagian tersebut diilustrasikan seperti berikut:

[![2020061215241361da7eebd046c6406eea62a5e45b08bc.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061215241361da7eebd046c6406eea62a5e45b08bc.png)](https://www.dicoding.com/academies/159/tutorials/6480#)

Pada gambar di atas kotak berwarna merah merupakan AppBar; kotak berwarna hijau merupakan body; dan kotak berwarna biru merupakan FloatingActionButton.

Untuk membuat sebuah Scaffold kita hanya cukup memanggil class <mark style="color:yellow;">Scaffold</mark> seperti berikut:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

Pada kode di atas kita membuat sebuah StatelessWidget bernama FirstScreen, yang merupakan widget tampilan kita. Kemudian di dalam method build kita panggil Scaffold.

Jangan lupa untuk memanggil FirstScreen pada Widget MyApp seperti berikut:

```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: FirstScreen(),// Panggil FirstScreen di sini
 
    );
  }
}
 
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

Ketika kita menjalankan aplikasi Flutter, pada layar akan hanya muncul tampilan berwarna putih.

[![2020061215262307b587ded6d58a895a132d85691cda81.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061215262307b587ded6d58a895a132d85691cda81.jpeg)](https://www.dicoding.com/academies/159/tutorials/6480#)

### AppBar

Setelah kita membuat Scaffold pertama kita pada Widget FirstScreen, sekarang kita akan menambahkan AppBar pada Scaffold. Seperti yang kita tahu AppBar merupakan Header (bagian paling atas) aplikasi atau biasa dikenal dengan toolbar. Pada AppBar umumnya terdapat judul dan ActionButton.

Berikut adalah cara menambahkan AppBar pada Scaffold:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
    );
  }
}
```

Pada kode di atas kita menambahkan parameter <mark style="color:yellow;">appBar</mark> pada Scaffold dan menambahkan title pada AppBar tersebut. Title di sini tidak hanya spesifik Text saja, melainkan juga dapat diisi dengan widget lainnya seperti TextField untuk kolom pencarian atau yang lainnya. Setelah menambahkan kode di atas, coba _refresh_ atau _hot reload_ aplikasi Flutter Anda. Selain menambahkan <mark style="color:yellow;">title</mark> kita dapat menambahkan widget-widget actions seperti pada kode berikut:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
        actions: <Widget>[
          IconButton(
            icon: Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
        ],
      ),
    );
  }
}
```

Pada kode di atas kita menambahkan Icon search pada bagian kanan AppBar. Lalu kita juga dapat menambahkan action pada bagian kiri AppBar misalnya untuk tombol yang menampilkan menu (drawer), seperti pada kode berikut:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        leading: IconButton(
          icon: Icon(
            Icons.menu,
            color: Colors.white,
          ),
          onPressed: () {},
        ),
        title: Text('First Screen'),
        actions: [
          IconButton(
            icon: Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
        ],
      ),
    );
  }
}
```

Tidak seperti pada actions, leading hanya dapat menampung satu widget saja. Secara _default_, _leading_ akan berisi tombol untuk kembali ke halaman sebelumnya (jika tersedia), atau tombol untuk menu drawer (jika kita mengatur untuk drawer pada Scaffold tersebut). Untuk melihat hasilnya lakukan refresh atau hot reload pada aplikasi Flutter Anda.

[![2020061215323635afb5ecc6a93e3865c3799349e95bde.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061215323635afb5ecc6a93e3865c3799349e95bde.jpeg)](https://www.dicoding.com/academies/159/tutorials/6480#)

### Body

Setelah menambahkan AppBar kita akan menambahkan _body_. Seperti pada ilustrasi sebelumnya, body merupakan bagian utama dari Scaffold dan kita akan banyak menuliskan kode pada bagian body ini. Untuk implementasi body kita akan menambahkan parameter body pada Scaffold seperti berikut:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        leading: IconButton(
          icon: Icon(Icons.menu, color: Colors.white,),
          onPressed: () {},
        ),
        title: Text('First Screen'),
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.search, color: Colors.white,),
            onPressed: () {},
          )
        ],
      ),
      body: Center(
        child: Text('Hello world!'),
      ),
    );
  }
}
```

Pada kode di atas kita telah menambahkan body yang di dalamnya kita memanggil widget Center yang akan menampilkan Text "Hello World!".

[![20200612153614819c7fee5f4ef03ece5d7d75344e5e1f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200612153614819c7fee5f4ef03ece5d7d75344e5e1f.jpeg)](https://www.dicoding.com/academies/159/tutorials/6480#)

### FloatingActionButton

Selanjutnya, kita akan menambahkan sebuah tombol bulat pada bagian kanan bawah seperti ilustrasi sebelumnya yaitu _FloatingActionButton_. FloatingActionButton ini merupakan bagian dari Scaffold yang digunakan untuk menampilkan sebuah tombol aksi yang posisinya _floating_ (melayang dan posisinya tetap). Untuk menggunakan FloatingActionButton tambahkan kode Anda seperti berikut:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        leading: IconButton(
          icon: Icon(Icons.menu, color: Colors.white,),
          onPressed: () {},
        ),
        title: Text('First Screen'),
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.search, color: Colors.white,),
            onPressed: () {},
          )
        ],
      ),
      body: Center(
        child: Text('Hello world!'),
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
      ),
    );
  }
}
```

### Hasil Akhir

Setelah kita menambahkan AppBar, body, dan FloatingActionButton maka hasil akhirnya akan seperti berikut:

[![202006121538450231a43712351e88bcb051f5db4aaaeb.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006121538450231a43712351e88bcb051f5db4aaaeb.jpeg)](https://www.dicoding.com/academies/159/tutorials/6480#)

Untuk memahami Scaffold lebih dalam, Anda bisa membaca tautan berikut:

* [Scaffold Class](https://api.flutter.dev/flutter/material/Scaffold-class.html)
* [Scaffold Sample Apps](https://flutter.dev/docs/catalog/samples/Scaffold)
