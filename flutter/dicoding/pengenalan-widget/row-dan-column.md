# 📖 Row dan Column

Selanjutnya kita akan mempelajari bagaimana cara membuat widget yang kita gunakan berjajar secara vertikal atau horizontal. Lalu apa yang dimaksud dengan membuat widget yang berjajar? Perhatikan gambar berikut:\
[![20200615193337da9cc18beb6419c05d025dc651a4d837.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615193337da9cc18beb6419c05d025dc651a4d837.jpeg)](https://www.dicoding.com/academies/159/tutorials/6498#)

Pada gambar di atas kita memiliki tampilan ikon-ikon yang merupakan kumpulan tombol, di antaranya _share_, _like_ dan _dislike_. Tombol-tombol tersebut tersusun berjajar secara horizontal. Nah, untuk membuat berjajar horizontal atau membentuk baris kita menggunakan widget Row. Sedangkan untuk menyusun widget yang membentuk kolom atau vertikal, kita bisa menggunakan widget Column.

### Widget Row

Seperti yang dicontohkan sebelumnya, widget Row merupakan suatu widget yang digunakan untuk membuat widget-widget tersusun berjajar secara horizontal. Row memiliki sintaks seperti berikut:

```
Row(
  children: <Widget>[
    //di sini berisi widget-widget
  ],
)
```

Untuk membuat widget-widget berjajar secara horizontal kita harus memasukkan widget-widget tersebut ke dalam parameter children. Parameter children berisi kumpulan atau list dari widget karena kita dapat menyusun beberapa widget sekaligus di dalamnya. Jika mengacu pada contoh tombol-tombol di atas kodenya seperti berikut:

```
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: <Widget> [
    Icon(Icons.share),
    Icon(Icons.thumb_up),
    Icon(Icons.thumb_down),
  ],
)
```

Seperti yang kita lihat, kita membuat sebuah IconButton berada di dalam parameter children. Kita menambahkan pula <mark style="color:yellow;">`mainAxisAlignment`</mark> yang merupakan parameter _alignment_ pada Row. Parameter mainAxisAlignment yang berfungsi untuk mengatur _alignment_ vertikal dari Row (_alignment_ utama). Selain itu Row juga memiliki parameter _crossAxisAlignment_ yang berfungsi untuk mengatur _alignment_ secara horizontal. Kedua parameter ini juga berlaku sebaliknya untuk widget Column.\
[![20200615193413854d522ae9635ddef73b39277708f37f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615193413854d522ae9635ddef73b39277708f37f.jpeg)](https://www.dicoding.com/academies/159/tutorials/6498#)

Berikut ini adalah contoh penerapan mainAxisAlignment pada Row:

[![2021042512000412e4c53a9d35daed279e1163d70a284b.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042512000412e4c53a9d35daed279e1163d70a284b.jpeg)](https://www.dicoding.com/academies/159/tutorials/6498#)

### Widget Column

Kebalikan dari Row, Column merupakan suatu widget yang digunakan untuk membuat widget-widget tersusun berjajar secara vertikal. Column memiliki sintaks mirip dengan Row, seperti berikut:

```
Column(
  children: <Widget>[
    //di sini berisi widget-widget
  ]
)
```

Contoh penerapan Column seperti berikut:

```
Column(
  children: <Widget>[
    Text(
      'Sebuah Judul',
      style: TextStyle(fontSize: 32, fontWeight: FontWeight.bold),
    ),
    Text('Lorem ipsum dolor sit amet'),
  ],
)
```

Maka akan menghasilkan tampilan seperti berikut:\
[![20200615193505c7892546a782aa0f2a5a31e129c9eee1.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615193505c7892546a782aa0f2a5a31e129c9eee1.jpeg)](https://www.dicoding.com/academies/159/tutorials/6498#)

### **Kesimpulan**

Untuk membuat sebuah widget-widget berjajar kita dapat menggunakan widget _Row_ atau _Column_. Sebenarnya penggunaan Row dan Column dapat dipadukan sehingga dapat membuat sebuah layout yang kompleks seperti berikut:[![202006151955516672a62f6d332c620b45752249265c90.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151955516672a62f6d332c620b45752249265c90.png)](https://www.dicoding.com/academies/159/tutorials/6498#)

[![20200205234120de1d94646ed7fc9d450b0abb543ae326.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200205234120de1d94646ed7fc9d450b0abb543ae326.png)](https://www.dicoding.com/academies/159/tutorials/6498#)

Untuk memahami Row, Column, dan bagaimana menyusun layout dengan Flutter secara mendalam, silakan pelajari dokumentasi berikut:

* [Row Class](https://api.flutter.dev/flutter/widgets/Row-class.html)
* [Column Class](https://api.flutter.dev/flutter/widgets/Column-class.html)
* [Layouts in Flutter](https://flutter.dev/docs/development/ui/layout)
