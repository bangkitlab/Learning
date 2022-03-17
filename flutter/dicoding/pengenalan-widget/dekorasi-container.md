# 📖 Dekorasi Container



Decoration merupakan bagian dari Container untuk _styling_. Pada decoration kita dapat menentukan warna _background_ (_solid/gradient color_), _shadow_, _border_, _border radius_ (membulatkan sudut), mengatur _shape_ (bentuk), dan lain-lain.

### Color

Contoh menentukan warna background dari container dengan decoration seperti berikut:

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40),),
  decoration: BoxDecoration(
    color: Colors.red,
  ),
)
```

Ketika dijalankan maka tampilan aplikasi akan seperti berikut:\
[![20200615192933b608ccce9f54b3ac0e012b53b590c409.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615192933b608ccce9f54b3ac0e012b53b590c409.jpeg)](https://www.dicoding.com/academies/159/tutorials/6490#)

Untuk menggunakan decoration cukup menambahkan parameter decoration pada Container lalu beri nilai BoxDecoration. Pada contoh di atas kita merubah warna Container menjadi merah dengan memberi parameter color pada BoxDecoration. Ada catatan penting ketika menggunakan color pada BoxDecoration, yaitu pastikan tidak memberi parameter color pada Container.

### Shape

Contoh selanjutnya pada decoration adalah kita akan mengatur shape (bentuk) dari Container, contohnya sebagai berikut:

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40),),
  decoration: BoxDecoration(
    color: Colors.red,
    shape: BoxShape.circle,
  ),
)
```

Pada kode di atas kita menambahkan parameter shape dengan nilai BoxShape.circle. Artinya, bentuk dari Container tersebut akan berbentuk lingkaran. BoxShape memiliki opsi _circle_ atau _rectangle_.\
[![202006151929504f732b0253654199eee3af0867529282.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151929504f732b0253654199eee3af0867529282.jpeg)](https://www.dicoding.com/academies/159/tutorials/6490#)

### Shadow

Untuk menambahkan shadow pada Container kita akan menambahkan parameter boxShadow pada BoxDecoration, seperti berikut:

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40)),
  decoration: BoxDecoration(
    color: Colors.red,
    boxShadow: [
      BoxShadow(
        color: Colors.black,
        offset: Offset(3, 6),
        blurRadius: 10,
      ),
    ],
  ),
)
```

Pada kode di atas parameter boxShadow merupakan sebuah Array. Di dalamnya terdapat BoxShadow yang artinya pada Container kita dapat memberikan banyak bayangan atau shadow.\
[![202006151930121a08754655373208b1bfbfb97b163cfd.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151930121a08754655373208b1bfbfb97b163cfd.jpeg)](https://www.dicoding.com/academies/159/tutorials/6490#)

### Border

Border merupakan batas garis dengan content (child). Begini cara menambahkan border pada container:&#x20;

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40),),
  decoration: BoxDecoration(
    color: Colors.red,
    border: Border.all(color: Colors.green, width: 3),
  ),
)
```

[![2020061511423652a013a86d133800a086bda512eb3ff4.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061511423652a013a86d133800a086bda512eb3ff4.jpeg)](https://www.dicoding.com/academies/159/tutorials/6490#)

Apabila Anda ingin membuat border yang tidak berujung lancip cukup tambahkan parameter borderRadius Pada BoxDecoration seperti berikut:

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40),),
  decoration: BoxDecoration(
   color: Colors.red,
   border: Border.all(color: Colors.green,width: 3),
   borderRadius: BorderRadius.circular(10),
  ),
)
```

[![20200615114318fbb34873394dad111e5f8010b4dd48a6.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615114318fbb34873394dad111e5f8010b4dd48a6.jpeg)](https://www.dicoding.com/academies/159/tutorials/6490#)

### Kesimpulan

Dengan menggunakan Widget Container kita dapat membuat variasi widget yang kita buat. Sebenarnya banyak sekali parameter-parameter yang dapat digunakan pada Container dan juga pada BoxDecoration. Anda dapat mengeksplorasi hal tersebut dengan mencarinya di Google atau pada dokumentasi resmi flutter.

* [Container Class](https://api.flutter.dev/flutter/widgets/Container-class.html)
