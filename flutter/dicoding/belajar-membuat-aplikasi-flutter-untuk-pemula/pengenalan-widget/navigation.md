# 📖 Navigation

Kita telah bisa membuat satu tampilan _screen_ (layar/_page_) pada pembelajaran sebelumnya. Namun, pada saat membangun sebuah aplikasi kita akan membuat banyak sekali _screen_ dan kita akan berpindah dari satu _screen_ ke _screen_ lainnya.

Dalam pemrograman Android kita mengenal Intent lalu pada pemrograman website terdapat _tag_ untuk berpindah dari satu _page_ ke _page_ lain. Pada Flutter kita akan menggunakan sebuah _class_ bernama **Navigator**. Dengan Navigator ini kita akan berpindah dari satu screen ke screen lainnya. Berikut ini contohnya:

[![202104251549548111f35cce880b070c4dbe6ba38bfe9e.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251549548111f35cce880b070c4dbe6ba38bfe9e.gif)](https://www.dicoding.com/academies/159/tutorials/8611?from=8610#)

Perlu kita ketahui bahwa konsep navigasi pada Flutter mirip sekali dengan pemrograman Android, yakni bahwa ketika berpindah _screen_/_activity_ akan menjadi tumpukan (_stack_). Jadi ketika berpindah dari satu _screen_ ke _screen_ lain (_push_), maka _screen_ pertama akan ditumpuk oleh _screen_ kedua. Kemudian apabila kembali dari screen kedua ke pertama, maka screen kedua akan dihapus (pop).\
[![202006151626413acd4cdf460618271f88df4e5a1b7653.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151626413acd4cdf460618271f88df4e5a1b7653.png)](https://www.dicoding.com/academies/159/tutorials/8611?from=8610#)

Kita akan membuat kode seperti contoh di atas. Kita membutuhkan halaman kedua yang kodenya seperti berikut:

```
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second Screen'),
      ),
      body: Center(
        child: OutlinedButton(
          child: Text('Kembali'),
          onPressed: () {},
        ),
      ),
    );
  }
}
```

Lalu, kode untuk halaman pertama akan seperti berikut:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          child: Text('Pindah Screen'),
          onPressed: () {},
        ),
      ),
    );
  }
}
```

### Navigator.push

Untuk berpindah ke _screen_ kedua kita akan menggunakan sebuah method <mark style="color:yellow;">`Navigator.push`</mark>, method tersebut ditulis seperti berikut:

```
Navigator.push(context, MaterialPageRoute(builder: (context) {
   return WidgetScreen();
}));
```

Pada kode di atas <mark style="color:yellow;">`Navigator.push`</mark> memiliki dua parameter. Pertama ialah context dan yang kedua Route. Parameter _context_ ini merupakan variabel _BuildContext_ yang ada pada _method build_. Parameter _route_ berguna untuk menentukan tujuan ke mana kita akan berpindah _screen_. Route tersebut kita isikan dengan MaterialPageRoute yang di dalamnya terdapat _builder_ yang nantinya akan diisi dengan tujuan _screen_-nya. Maka untuk melakukan perpindahan _screen_ kita akan membuat event <mark style="color:yellow;">`onPressed`</mark> pada tombol ElevatedButton yang ada pada _screen_ pertama:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          child: Text('Pindah Screen'),
          onPressed: () {
            Navigator.push(context, MaterialPageRoute(builder: (context) {
              return SecondScreen();
            }));
          },
        ),
      ),
    );
  }
}

```

### Navigator.pop

Setelah dapat berpindah ke _screen_ lain dan kembali ke _screen_ sebelumnya, maka kita akan belajar menggunakan <mark style="color:yellow;">`Navigator.pop`</mark>. Penulisan <mark style="color:yellow;">`Navigator.pop`</mark> seperti berikut:

```
Navigator.pop(context)
```

Pada `Navigator.pop` kita hanya cukup menambahkan parameter _context_ yang merupakan variabel dari _method build_.

Untuk kembali dari screen kedua kita dapat menambahkan _event_ <mark style="color:yellow;">`onPressed`</mark> pada OutlinedButton yang ada pada _screen_ kedua dan kita masukkan <mark style="color:yellow;">`Navigator.pop`</mark> pada _event_, seperti berikut:

```
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second Screen'),
      ),
      body: Center(
        child: OutlinedButton(
          child: Text('Kembali'),
          onPressed: () {
            Navigator.pop(context);
          },
        ),
      ),
    );
  }
}
```

### Mengirimkan Data Antar Halaman

Seringkali beberapa halaman pada aplikasi perlu saling berinteraksi dengan berbagi dan saling mengirimkan data. Pada Flutter kita memanfaatkan _constructor_ dari sebuah class untuk mengirimkan data antar halaman.

Sebagai contoh kita memiliki pesan yang akan dikirimkan dari _First Screen_ menuju _Second Screen_.

```
String message = 'Hello from First Screen!';
```

Untuk mengirimkan variabel message tersebut ke Second Screen, maka kita akan mengirimkannya sebagai parameter dari constructor kelas SecondScreen seperti berikut:

```
class FirstScreen extends StatelessWidget {
  final String message = 'Hello from First Screen!';
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          child: Text('Pindah Screen'),
          onPressed: () {
            Navigator.push(context,
                MaterialPageRoute(builder: (context) => SecondScreen(message)));
          },
        ),
      ),
    );
  }
}
```

Agar _Second Screen_ bisa menerima data tersebut, maka kita perlu mengubah _default constructor_-nya dan menambahkan variabel untuk menampung datanya.

```
class SecondScreen extends StatelessWidget {
  final String message;
 
  SecondScreen(this.message);
}
```

Kemudian kita dapat menampilkan data yang diterima melalui variabel yang kita buat.

```
class SecondScreen extends StatelessWidget {
  final String message;
 
  SecondScreen(this.message);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second Screen'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(message),
            OutlinedButton(
              child: Text('Kembali'),
              onPressed: () {
                Navigator.pop(context);
              },
            ),
          ],
        ),
      ),
    );
  }
}
```

Sehingga tampilan _Second Screen_ akan menampilkan pesan dari _First Screen_ seperti berikut:

[![20210425155717abf5a880687b3e054a214cab4a5f7173.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425155717abf5a880687b3e054a214cab4a5f7173.png)](https://www.dicoding.com/academies/159/tutorials/8611?from=8610#)

Anda dapat memahami _Navigation_ secara mendalam dengan membaca dokumentasi [Navigation Cookbook](https://flutter.dev/docs/cookbook/navigation).
