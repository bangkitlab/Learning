# 📖 Button

{% hint style="info" %}
### **Pembaruan!**

Artikel ini diperbarui pada tanggal 26 April 2021. Pembaruan terakhir adalah: **Update deprecated code**.\
[_Lihat riwayat »_](https://www.dicoding.com/academies/159/tutorials/6504?from=6502#changelog-modal)
{% endhint %}

Kali ini kita akan belajar menggunakan widget button. Widget button ini adalah widget yang dapat menerima trigger sentuhan atau dapat melakukan suatu fungsi ketika disentuh, widget-widget button tersebut antara lain:

### ElevatedButton

ElevatedButton merupakan bagian dari Material Design widget dari Flutter. Untuk menggunakan ElevatedButton caranya seperti berikut:

```
ElevatedButton(
  onPressed: (){
    // Aksi ketika button diklik
  },
  child: Text("Tombol"),
);
```

Pada kode di atas ElevatedButton memiliki 2 parameter yaitu <mark style="color:yellow;">`onPressed`</mark> dan <mark style="color:yellow;">`child`</mark>. Parameter _onPressed_ merupakan sebuah _function event_ ketika tombol ditekan dan sebenarnya ada _event_ lain seperti _onLongPress_ dan _onHighlightChanged_. Parameter _child_ diisi oleh widget pada umumnya.

[![202104251352136a73d33e8f3402d9b38982135894530a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104251352136a73d33e8f3402d9b38982135894530a.jpeg)](https://www.dicoding.com/academies/159/tutorials/6504?from=6502#)

### TextButton

TextButton merupakan widget button yang memiliki tampilan yang polos selayaknya Text. TextButton umumnya digunakan pada toolbars, dialog, atau bersama komponen button lain. Contoh kode dari TextButton adalah seperti berikut:

```
TextButton(
  onPressed: () {
    // Aksi ketika button diklik
  },
  child: Text('Text Button'),
)
```

Sama halnya ElevatedButton, TextButton juga memiliki parameter onPressed dan child.

[![20210425135351db0b26899a4a925bb3b9957298cfa842.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425135351db0b26899a4a925bb3b9957298cfa842.jpeg)](https://www.dicoding.com/academies/159/tutorials/6504?from=6502#)

### OutlinedButton

OutlinedButton juga merupakan bagian dari material design yang menyediakan tampilan TextButton dengan tambahan outline. OutlinedButton umumnya digunakan untuk tombol atau aksi yang penting, tetapi bukan aksi utama dalam aplikasi.

Berikut ini adalah contoh widget OutlinedButton:

```
OutlinedButton(
  onPressed: () {
    // Aksi ketika button diklik
  },
  child: Text('Outlined Button'),
)
```

Tampilan OutlinedButton sendiri akan seperti berikut:

[![20210425135549bec2472c048d1749041c5268861eb51a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425135549bec2472c048d1749041c5268861eb51a.jpeg)](https://www.dicoding.com/academies/159/tutorials/6504?from=6502#)

### IconButton

IconButton merupakan widget button dengan icon. Tak seperti widget tombol lainnya, widget IconButton ini tidak memiliki child. Perhatikan kode di bawah ini:

```
IconButton(
  icon: Icon(Icons.volume_up),
  tooltip: 'Increase volume by 10',
  onPressed: () {
    // Aksi ketika button diklik
  },
)
```

Seperti yang kita lihat di atas, IconButton tidak menggunakan child untuk isi (_content_) melainkan menggunakan parameter icon dan _tooltip_ (penunjuk) untuk memberikan hint pada tombol.\
[![202006151939145295ed95945289ccf061a9250264d33f.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151939145295ed95945289ccf061a9250264d33f.jpeg)](https://www.dicoding.com/academies/159/tutorials/6504?from=6502#)

### DropdownButton

DropdownButton merupakan tombol yang saat diklik, akan muncul _pop-up_ daftar beberapa item yang dapat kita pilih salah satu. Berikut contoh kodenya:

```
class FirstScreen extends StatefulWidget {
  @override
  _FirstScreenState createState() => _FirstScreenState();
}
 
class _FirstScreenState extends State<FirstScreen> {
  String language;
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: DropdownButton<String>(
        items: <DropdownMenuItem<String>>[
          DropdownMenuItem<String>(
            value: 'Dart',
            child: Text('Dart'),
          ),
          DropdownMenuItem<String>(
            value: 'Kotlin',
            child: Text('Kotlin'),
          ),
          DropdownMenuItem<String>(
            value: 'Swift',
            child: Text('Swift'),
          ),
        ],
        value: language,
        hint: Text('Select Language'),
        onChanged: (String value) {
          setState(() {
            language = value;
          });
        },
      ),
    );
  }
}
```

Pada contoh tersebut DropdownButton tidak menggunakan child maupun children, akan tetapi menggunakan <mark style="color:yellow;">`items`</mark> di mana berisi list dari widget <mark style="color:yellow;">`DropdownMenuItem`</mark>. Pada widget <mark style="color:yellow;">`DropdownMenuItem`</mark> terdapat <mark style="color:yellow;">`child`</mark> untuk tiap itemnya dan <mark style="color:yellow;">`value`</mark> yang ada pada DropdownMenuItem adalah nilai dari tiap itemnya. Nantinya akan dibutuhkan parameter <mark style="color:yellow;">`onChanged`</mark> ketika ada perubahan atau ketika memilih salah satu dari item tersebut dan mengubah nilai language atau value dari DropdownButton tersebut. Sedangkan <mark style="color:yellow;">`hint`</mark> berfungsi ketika nilai value dari DropdownButton _null_ atau kosong.

[![20210425135701458334fcadd3cc47c3fbbc0d7379d47d.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425135701458334fcadd3cc47c3fbbc0d7379d47d.gif)](https://www.dicoding.com/academies/159/tutorials/6504?from=6502#)

Selengkapnya tentang berbagai widget Button, bacalah pada tautan berikut:

* [Button Material Components](https://flutter.dev/docs/development/ui/widgets/material#Buttons)
* [ElevatedButton Class](https://api.flutter.dev/flutter/material/ElevatedButton-class.html)
* [TextButton Class](https://api.flutter.dev/flutter/material/TextButton-class.html)
* [OutlinedButton](https://api.flutter.dev/flutter/material/OutlinedButton-class.html)
* [IconButton Class](https://api.flutter.dev/flutter/material/IconButton-class.html)
* [DropdownButton Class](https://api.flutter.dev/flutter/material/DropdownButton-class.html)
