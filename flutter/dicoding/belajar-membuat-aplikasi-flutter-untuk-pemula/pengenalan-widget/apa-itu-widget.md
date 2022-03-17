# 📖 Apa itu Widget

Kita telah berkenalan, menginstal, dan belajar fundamental Flutter. Itu _entrée_ alias hidangan pembukanya. Nah, sekarang kita akan menyibak ke _plat du jour_ alias menu utamanya. Apa inti dari Flutter? Yap, _**widget**_ jawabnya! Sebagian besar yang ada pada Flutter adalah widget. Jadi, relevan jika kita bilang bahwa “Flutter is all about widget.” Text sendiri adalah widget. Button juga widget. Selain itu widget juga dapat dibangun dari kumpulan beberapa widget. Lantas mengapa widget begitu penting dalam flutter? Penasaran? Mari kita bahas!

### World of components

Perlu kita ketahui bahwa konsep Widget pada Flutter itu terinspirasi oleh salah framework JavaScript yang digunakan untuk membangun sebuah website yaitu ReactJS. ReactJS memiliki konsep Component. Mari kita analogikan dengan mainan lego! Di lego terdapat _block-block_ kecil yang nantinya kita susun untuk membangun sebuah istana lego. Berarti _component_ dalam _programming_ adalah sekumpulan _block-block code_ yang digunakan untuk membangun sebuah aplikasi.

[![20200205230026bdc771da608a1ded8c77d30a7ea740d8.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200205230026bdc771da608a1ded8c77d30a7ea740d8.png)](https://www.dicoding.com/academies/159/tutorials/6475#)

Widget sama halnya dengan component yang merupakan kumpulan block code untuk membangun aplikasi Flutter. Ketika membangun aplikasi Flutter kita harus berpikir layaknya bermain lego. Kita harus bisa membuat dan menyusun widget-widget dengan tepat. Tujuannya, agar aplikasi yang kita buat lebih mudah untuk dikembangkan.

### Bagaimana cara menulis widget

Sebetulnya pada pembahasan sebelumnya secara tidak sadar kita telah membuat sebuah widget dan menggunakan widget yang telah disediakan.

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

Pada kode di atas kita telah membuat sebuah Widget MyApp dan telah menggunakan widget-widget bawaan Flutter di antaranya _MaterialApp_, _Scaffold_, _Center_, dan _Text_. Ketika menggunakan widget, kita tinggal panggil nama widget dan bila ada properti atau parameter pada widget tersebut tinggal kita isikan properti atau parameternya.

```dart
Center(
  child: Text('Hello world!'),
)
```

Kode di atas merupakan contoh pemanggilan widget Center. Widget Center ini digunakan untuk membuat widget yang ada di dalamnya berada di posisi tengah (mirip seperti alignment center). Tinggal ketikkan Center lalu tambahkan properti child di dalamnya.

Perlu diketahui bahwa sebagian besar widget bawaan memiliki pola _parent-child_, seperti halnya Center yang memiliki child yang artinya di dalam child bisa terdapat widget lagi. Maka penulisan parent child akan seperti di bawah ini.

```
Center( // parent dari Button
  child: Button( // child dari Center dan parent dari Text
    child: Text(), // child dari Button
  ),
)
```

Pada contoh di atas widget Center dan Button hanya dapat memiliki satu anak atau bisa disebut child. Ada pula widget yang dapat memiliki banyak anak atau bisa disebut children, seperti Row, Column, ListView, GridView, dan semacamnya.

```
Row(
  children: <Widget>[
    //di dalam children akan berisi banyak widget
  ]
)
```

Contoh di atas adalah widget Row yang memiliki children. Di dalam children nantinya kita bisa menambahkan banyak widget. Berbeda dengan child yang diisi langsung dengan sebuah Widget, children akan berisi sebuah list yang di dalamnya diisi dengan banyak widget.
