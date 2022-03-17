# 📖 Image

Dalam pengembangan suatu aplikasi kita tidak akan lepas dari image atau gambar untuk membuat tampilan semakin menarik. Pada materi kali ini kita akan belajar bagaimana menampilkan gambar dari internet dan project asset.

### Image.network

Untuk menampilkan gambar yang bersumber dari internet, kita akan menggunakan method <mark style="color:yellow;">`Image.network`</mark>. Cara penulisan method ini sebagai berikut:

```
Image.network(url)
```

Method ini cukup menambahkan URL gambar dari internet dan kita pun dapat menambahkan width dan height juga. Di bawah ini adalah contoh penggunaan <mark style="color:yellow;">`Image.network`</mark>:

```
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Center(
        child: Image.network(
          'https://picsum.photos/200/300',
          width: 200,
          height: 200,
        ),
      ),
    );
  }
}
```

Pada kode di atas kita panggil method <mark style="color:yellow;">`Image.network`</mark> dengan url _https://picsum.photos/200/300_ lalu beri _width_ dan _height_ masing-masing 200. Sehingga hasilnya seperti berikut:\
[![20200615142935f4ba1003836215c90853a5a436620dc4.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615142935f4ba1003836215c90853a5a436620dc4.jpeg)](https://www.dicoding.com/academies/159/tutorials/6519?from=8606#)

### Image.asset

Selain melalui internet, kita juga dapat menampilkan gambar yang bersumber dari asset _project_.. Asset di sini berupa gambar-gambar yang nantinya didaftarkan pada _project_. Untuk mendaftarkan asset gambar pada project kita harus menambahkannya pada berkas **pubspec.yaml**.

Pertama kita harus menambahkan terlebih dahulu gambar yang akan didaftarkan ke dalam folder project kita. Saat ini Flutter mendukung beberapa jenis format gambar, seperti JPEG, PNG, GIF, Animated GIF, WebP, Animated WebP, BMP, dan WBMP. Di luar format tersebut, Flutter akan memanfaatkan API dari masing-masing platform. Jika platform native mendukung format gambar yang digunakan, maka gambar tersebut akan bisa di-render oleh Flutter.

Pada contoh berikut kita menambahkan folder **images/** pada folder project.

[![20210425141500f20e24ccaaaaeb832eb7c2e089b8ad4b.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425141500f20e24ccaaaaeb832eb7c2e089b8ad4b.jpeg)](https://www.dicoding.com/academies/159/tutorials/6519?from=8606#)

Masukkan berkas gambar yang ingin Anda gunakan ke dalam folder **image**. Sebagai contoh kita menggunakan gambar bernama **android.png**.

Setelah menambahkan gambar pada _project_, saatnya kita mendaftarkan gambar tersebut pada **pubspec.yaml**.

Di dalam berkas **pubspec.yaml**, kita bisa mendaftarkan aset gambar pada bagian flutter seperti di bawah ini:

```
...
flutter:
 
  uses-material-design: true
 
  # To add assets to your application, add an assets section, like this:
  # assets:
  #  - images/a_dot_burr.jpeg
  #  - images/a_dot_ham.jpeg
  
...
```

Daftarkan asset gambar seperti berikut:

```
...
flutter:
  uses-material-design: true
 
  assets:
    - images/android.png
...
```

Hapus juga tanda pagar (#) atau komentar yang tidak diperlukan. Perhatikan pula indentasi kodenya. <mark style="color:yellow;">`assets`</mark>: berada sejajar dengan <mark style="color:yellow;">`uses-material-design`</mark>: yaitu berjarak 2 spasi dari ujung dan berada di dalam <mark style="color:yellow;">`flutter`</mark>: sedangkan - <mark style="color:yellow;">`images/android.png`</mark> berada di dalam assets: dan berjarak 4 spasi dari ujung.

Pada contoh di atas kita telah menambahkan asset yang berisi lokasi gambar atau aset yang ingin kita gunakan. Karena kita menambahkan gambar **android.png** pada folder _images_, maka lokasi gambar tersebut adalah **images/android.png**.

Apabila ada banyak gambar yang kita masukkan ke dalam lokasi folder, dibandingkan menuliskan lokasi gambar satu per satu, kita bisa langsung menuliskan folder **images/** seperti berikut:

```
...
flutter:
 
  uses-material-design: true
 
  assets:
    - images/
...
```

Setelah menambahkan _assets_, kita harus me-_refresh_ **pubspec.yaml** dengan cara _save file_ pubspec.yaml bila menggunakan Visual Studio Code atau menekan 'Packages get' yang ada di pojok kanan atas untuk Android Studio.

Setelah kita menambahkan asset ke dalam pubspec.yaml kita perlu melakukan full restart agar asset yang baru dapat digunakan dalam aplikasi.

Kita telah mendaftarkan suatu asset. Sekarang kita akan panggil asset tersebut pada kode kita dengan method <mark style="color:yellow;">`Image.asset`</mark>. Cara penulisannya seperti berikut:

```
Image.asset(lokasi_asset)
```

Contoh dalam kodenya akan seperti berikut:

```
class FirstScreen extends StatelessWidget {
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        leading: IconButton(
          icon: Icon(Icons.menu, color: Colors.white,),
        ),
        title: Text('First Screen'),
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.search, color: Colors.white,),
          )
        ],
      ),
      body: Center(
        child: Image.asset('images/android.png', width: 200, height: 200),
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
      ),
    );
  }
}
```

Jika kita jalankan aplikasi Flutter, maka gambar akan tampil seperti berikut:\
[![20200615144816e33b037a302476e6ab08c8021c1a6651.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615144816e33b037a302476e6ab08c8021c1a6651.jpeg)](https://www.dicoding.com/academies/159/tutorials/6519?from=8606#)

Untuk mempelajari widget Image lebih lanjut, Anda dapat membaca dokumentasinya pada tautan [Image Class](https://api.flutter.dev/flutter/widgets/Image-class.html).
