# 📖 Hello World App

Ketika pertama kali membuat project Flutter, kita akan diberikan aplikasi contoh yaitu aplikasi _counter_. _Source code_ utama Flutter kita ada pada file **lib/main.dart** dan kodenya kurang lebih seperti berikut:

```
import 'package:flutter/material.dart';
 
void main() {
  runApp(MyApp());
}
 
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      home: MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}
 
class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
 
  final String title;
 
  @override
  _MyHomePageState createState() => _MyHomePageState();
}
 
class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;
 
  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}
```

Kode di atas merupakan kode _starter_ yang di-_generate_ sebagai contoh ketika Anda membuat project. Anda dapat mempelajari kode tersebut untuk mengetahui bagaimana sebuah aplikasi Flutter disusun.

Untuk saat ini kita tidak akan menggunakan kode tersebut. Jadi, hapus semua isi berkas **main.dart** tersebut dan tulis kode untuk aplikasi kita sendiri, yaitu aplikasi sederhana untuk menampilkan teks Hello world.

```
import 'package:flutter/material.dart';
 
void main() {
 runApp(MyApp());
}
 
class MyApp extends StatelessWidget {
 @override
 Widget build(BuildContext context) {
   return MaterialApp(
     title: 'Flutter Demo',
     theme: ThemeData(
       primarySwatch: Colors.blue,
     ),
     home: Scaffold(
       appBar: AppBar(
         title: Text('Hello, world!'),
       ),
       body: Center(
         child: Text('Hello, world!'),
       ),
     ),
   );
 }

```

Mari kita bahas satu per satu kodenya!

```
import 'package:flutter/material.dart';
```

Import digunakan untuk memanggil fungsi-fungsi dari berkas Flutter yang lain. Pada kode di atas, kita meng-_import_ kode-kode yang terdapat dalam _library_ material bawaan Flutter. Library tersebut menyediakan widget yang termasuk dalam _material design_. Pastikan kode ini ada pada bagian atas sebelum kode lain dijalankan.

```
void main() => runApp(MyApp());
```

main() merupakan kode dasar dari project Flutter kita. Flutter akan menjalankan fungsi main() pertama kali, yang nantinya akan menjalankan runApp() dan memanggil MyApp().

```
class MyApp extends StatelessWidget {
 @override
 Widget build(BuildContext context) {
   return MaterialApp(
     title: 'Flutter Demo',
     theme: ThemeData(
       primarySwatch: Colors.blue,
     ),
     home: Scaffold(
       appBar: AppBar(
         title: Text('Hello, world!'),
       ),
       body: Center(
         child: Text('Hello, world!'),
       ),
     ),
   );
 }
}
```

MyApp di sini merupakan sebuah _class_ yang menampilkan komponen Flutter ke layar atau dikenal dengan Widgets.

Jika aplikasi dijalankan maka akan seperti berikut:

[![20210425110409ca27ae3cd84c618399aa4631216ce07c.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425110409ca27ae3cd84c618399aa4631216ce07c.png)](https://www.dicoding.com/academies/159/tutorials/6474?from=6454#)

Setiap komponen di dalam Flutter terdiri dari widget. Bahkan aplikasi Flutter itu sendiri merupakan sebuah widget. Pada contoh kode di atas kelas MyApp yang merupakan sebuah widget mengembalikan atau menampilkan widget MaterialApp. MaterialApp ini adalah widget bawaan Flutter yang akan menjadi fondasi dari aplikasi Anda. Ia umum digunakan supaya aplikasi bisa menerapkan material design. Widget ini mengatur beberapa hal, termasuk tema aplikasi, tampilan utama aplikasi, rute untuk navigasi antar halaman, dan lain-lain.

Selanjutnya Scaffold memungkinkan kita mendesain struktur layout dasar yang sesuai dengan material design. Dengan Scaffold Anda dapat mengatur App Bar, Floating Action Button, Drawer, dan lain-lain.

Ibarat rumah, MaterialApp ini adalah sebagai tanah yang umumnya digunakan hanya sekali saja, sedangkan Scaffold ini adalah sebagai tembok atau bangunannya.

Terakhir, seharusnya sudah cukup jelas kita menggunakan widget Text untuk menampilkan teks. Pada contoh di atas widget Text dibungkus dengan widget Center yang berfungsi supaya widget di dalamnya (_child_) tampil pada posisi tengah.

> **Tips**: _Documentation is your best friend_.&#x20;

Flutter memiliki banyak sekali widget dan tentunya akan menjadi tugas yang berat untuk menghafalkan semuanya. Namun tenang, Flutter dilengkapi dengan dokumentasi yang cukup lengkap sebagai panduan kita dalam mempelajari dan mengembangkan Flutter. Misalnya, penjelasan lebih lengkap tentang widget yang kita gunakan di atas dapat dilihat pada tautan berikut:

* [https://api.flutter.dev/flutter/material/MaterialApp-class.html](https://api.flutter.dev/flutter/material/MaterialApp-class.html)
* [https://api.flutter.dev/flutter/material/Scaffold-class.html](https://api.flutter.dev/flutter/material/Scaffold-class.html)
* [https://api.flutter.dev/flutter/widgets/Center-class.html](https://api.flutter.dev/flutter/widgets/Center-class.html)
* [https://api.flutter.dev/flutter/widgets/Text-class.html](https://api.flutter.dev/flutter/widgets/Text-class.html)
