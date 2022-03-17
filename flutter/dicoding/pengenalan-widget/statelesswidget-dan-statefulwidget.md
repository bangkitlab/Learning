# 📖 StatelessWidget dan StatefulWidget

Seperti yang kita tahu jantung dari aplikasi Flutter adalah widget. Sebagian besar yang ada pada Flutter merupakan widget. Membuat tombol, menampilkan gambar, text, dan membuat tampilan berada di tengah pada Flutter semuanya menggunakan widget. Kita juga dapat membuat widget sendiri untuk dapat digunakan lain waktu ataupun dibagikan kepada Flutter developer lain (dalam bentuk packages).

Widget pada Flutter memiliki dua jenis, yaitu StatelessWidget dan StatefulWidget. Sebagai developer Flutter, kita harus memahami betul kedua jenis widget tersebut, maka pada bagian ini kita akan mempelajari apa itu StatelessWidget dan StatefulWidget.

### Apa itu State?

Sebelum membahas kedua jenis widget tersebut, kita harus berkenalan terlebih dahulu dengan istilah _State_. Kenapa demikian? Widget kita akan terus berurusan dengan State. Lalu apa itu State?

Untuk teman-teman dengan background _frontend web developer_, tentu tak akan asing dengan istilah State ini, terutama menggunakan framework ReactJS. Tetapi untuk Anda tanpa _background_ tersebut tidak perlu risau. State tidaklah sulit untuk dimengerti. Jadi State adalah data yang ada pada suatu widget. Widget menyimpan data yang nantinya dapat berubah sesuai interaksi pengguna.

Karena Flutter menggunakan paradigma OOP (Object-Oriented Programming), state biasanya menjadi suatu properti dari sebuah class. Contohnya sebagai berikut:

```dart
class ContohWidget extends StatelessWidget{
    final String _judul    
    ...
}
```

Variabel <mark style="color:yellow;">`_judul`</mark> di atas merupakan contoh pendeklarasian state pada suatu widget.

### StatelessWidget

Setelah mengenal apa itu state, maka yang pertama kita akan bahas adalah StatelessWidget. StatelessWidget adalah widget yang nilai _state_-nya tidak dapat berubah (_immutable_) maka widget tersebut lebih bersifat statis dan memiliki interaksi yang terbatas.

Sekarang kita akan membuat sebuah Widget sederhana:

```
class Heading extends StatelessWidget {
 
  final String text;
 
  Heading({required this.text});
 
  @override
  Widget build(BuildContext context){
    return Text(
      text,
      style: TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```

Widget di atas merupakan sebuah widget untuk membuat Heading (sebuah text yang digunakan untuk judul). Kita akan panggil widget yang telah diubah ke kode project pertama kita.

```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        body: Center(
          child: Text("Hello world!"),
        ),
      ),
    );
  }
}
 
class Heading extends StatelessWidget {
  final String text;
 
  Heading({required this.text});
 
  @override
  Widget build(BuildContext context){
    return Text(
      text,
      style: TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```

Kita coba ubah widget <mark style="color:yellow;">`Text`</mark> yang menampilkan "Hello world!" dengan widget <mark style="color:yellow;">`Heading`</mark> yang kita buat.

```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        body: Center(
          child: Heading( // mengubah widget Text
            text:"Hello world!",
          ),
        ),
      ),
    );
  }
}
 
class Heading extends StatelessWidget {
  final String text;
 
  Heading({required this.text});
 
  @override
  Widget build(BuildContext context){
    return Text(
      text,
      style: TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```

Maka ketika kita ubah <mark style="color:yellow;">`Text`</mark> dengan widget <mark style="color:yellow;">`Heading`</mark>, hasilnya akan berubah. Tulisan "Hello world!" jadi lebih besar.

[![202006121457125b453dfd86f3dc997d9fe7fe2bc005b9.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006121457125b453dfd86f3dc997d9fe7fe2bc005b9.jpeg)](https://www.dicoding.com/academies/159/tutorials/6479#)

Sesuai definisi StatelessWidget, _state_-nya tidak dapat berubah (_immutable_), maka state yang ada di dalam kelas tersebut harus dibuat <mark style="color:yellow;">`final`</mark>. Nilainya hanya dapat diisi melalui _constructor class_-nya.

```
final String text; // state text bersifat final
 
Heading({required this.text}); // lalu state text masuk ke constructor
```

### StatefulWidget

Kebalikan dari StatelessWidget, StatefulWidget ialah widget yang _state_-nya dapat berubah-ubah nilainya, yang berarti StatefulWidget bersifat dinamis dan memiliki interaksi yang tak terbatas.

Penulisan StatefulWidget sangat berbeda dengan StatelessWidget, berikut penulisannya:

```
class ContohStateful extends StatefulWidget {
 
    final String parameterWidget; // ini parameter widget
 
    const ContohStateful({required this.parameterWidget});
 
    @override
    _ContohStatefulState createState() => _ContohStatefulState();
}
 
class _ContohStatefulState extends State<ContohStateful>{
    String _dataState; // ini state dari Widget ContohStateful
 
    @override
    Widget build(BuildContext context){
        // isi sebuah widget
    }
}
```

Contoh di atas adalah cara penulisan StatefulWidget. Seperti yang kita lihat, penulisan StatefulWidget lebih panjang. Tetapi yang harus diperhatikan adalah properti dari setiap _class_-nya. Pada class <mark style="color:yellow;">`ContohStateful`</mark> propertinya hanya berupa parameter ketika memanggil ContohStateful, parameter tersebut tidak wajib ada. Sedangkan pada class <mark style="color:yellow;">`_ContohStatefulState`</mark>, properti <mark style="color:yellow;">`_dataState`</mark> merupakan state yang sebenarnya. Kita akan mengubah nilai <mark style="color:yellow;">`_dataState`</mark>.

Misalnya kita coba membuat contoh StatefulWidget sederhana:

```
class BiggerText extends StatefulWidget {
  final String text;
 
  const BiggerText({required this.text});
 
  @override
  _BiggerTextState createState() => _BiggerTextState();
}
 
 
class _BiggerTextState extends State<BiggerText> {
  double _textSize = 16.0;
 
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text(widget.text, style: TextStyle(fontSize: _textSize)),
        ElevatedButton(
          child: Text("Perbesar"),
          onPressed: () {
            setState(() {
              _textSize = 32.0;
            });
          },
        )
      ],
    );
  }
}
```

Letakkan kode di atas setelah StatelessWidget Heading yang telah kita buat sebelumnya lalu panggil StatefulWidget <mark style="color:yellow;">`BiggerText`</mark> pada MyApp.

```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: Scaffold(
        body: Center(
          child: BiggerText(text:"Hello world!"), // Ubah widget Heading ke PerubahanText
        ),
      ),
    );
  }
}
 
class Heading extends StatelessWidget {
  final String text;
 
  Heading({required this.text});
 
  @override
  Widget build(BuildContext context) {
    return Text(
      text,
      style: TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
 
class BiggerText extends StatefulWidget {
  final String text;
  const BiggerText({required this.text});
  @override
  _BiggerTextState createState() => _BiggerTextState();
}
class _BiggerTextState extends State<BiggerText> {
  double _textSize = 16.0;
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text(widget.text, style: TextStyle(fontSize: _textSize)),
        ElevatedButton(
          child: Text("Perbesar"),
          onPressed: () {
            setState(() {
              _textSize = 32.0;
            });
          },
        )
      ],
    );
  }
}
```

Maka hasilnya akan seperti berikut:

[![202104251139068719290e0b73a9a61d2ead48c389c6d7.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251139068719290e0b73a9a61d2ead48c389c6d7.gif)](https://www.dicoding.com/academies/159/tutorials/6479#)

Ketika tombol "Perbesar" ditekan, text "Hello world!" akan membesar karena state <mark style="color:yellow;">`_textSize`</mark> diubah nilainya. Mengubah nilai state harus dilakukan pada fungsi <mark style="color:yellow;">`setState`</mark> seperti berikut:

```
setState(() {
  _textSize = 32.0; // ukuran text diubah menjadi 32
});
```

Anda dapat memahami lebih dalam terkait Stateless dan Stateful Widget dengan membaca dokumentasi berikut ini:

* [StatelessWidget Class](https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html)
* [StatefulWidget Class](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)
