# 📖 Font

Dalam pengembangan suatu aplikasi, seorang _User Interface_ desainer dapat menggunakan font berbeda dengan _default_ font yang ada. Sebagai pengembang aplikasi kita diharuskan menambahkan font pada aplikasi yang dirancang oleh desainer agar sesuai dengan desain User Interface.

Pada pembelajaran kali ini kita akan belajar bagaimana menambahkan _font_ pada Flutter. Sebelum kita memulai pembelajaran, kita akan mengunduh font yang ada di internet atau menggunakan _font_ yang telah dimiliki. Pada contoh ini kita akan mengunduh salah satu _font_ dari [Google Fonts](https://fonts.google.com) yaitu [Oswald](https://fonts.google.com/specimen/Oswald).

### Menambahkan Font ke Project

Setelah mengunduh font, langkah selanjutnya kita akan memasukkan _file-file_ font tersebut ke folder _project_. Pada contoh ini kita akan membuat folder fonts pada _project_ kita, dan masukkan _file-file_ font yang telah diunduh, seperti berikut:\
[![20200615194557c0f63961b549064c8aa1bcde62857d41.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615194557c0f63961b549064c8aa1bcde62857d41.jpeg)](https://www.dicoding.com/academies/159/tutorials/6533?from=6519#)  &#x20;

### Mendaftarkan Font di pubspec.yaml

Sama halnya dengan gambar, kita perlu mendaftarkan font pada berkas **pubspec.yaml** sebagai asset seperti berikut:

```
flutter:
 
  uses-material-design: true
  assets:
    - images/
 
  fonts:
    - family: Oswald
      fonts:
       - asset: fonts/Oswald/Oswald-Regular.ttf
```

Sama halnya dengan gambar, font ada dalam bagian flutter. Untuk mendaftarkan font, kita membuat bagian fonts yang ada dalam blok flutter.

Untuk mendaftarkan font _Oswald_ kita tuliskan _Oswald_ pada bagian _family_ yang nantinya akan menjadi nama font yang kita panggil pada kode dart. Lalu dalam _family_ kita masukkan fonts yang di dalamnya terdapat asset yang nanti akan mengarah pada _file_ font.ttf. **** Contoh di atas kita menambahkan asset _fonts/oswald/Oswald-Regular.ttf_.

### Menggunakan Font pada Kode

Setelah kita mendaftarkan font pada **pubspec.yaml** kita akan gunakan font tersebut pada kode kita. Seperti contoh di bawah ini kita akan menggunakan font pada widget **Text**:

```
Text('Custom Font', style: TextStyle(fontFamily: 'Oswald', fontSize: 30,),)
```

Pada kode di atas kita menambahkan <mark style="color:yellow;">`fontFamily`</mark> pada <mark style="color:yellow;">`TextStyle`</mark>. Kita cukup panggil nama font family yang telah kita daftarkan pada **pubspec.yaml**. Hasilnya akan seperti berikut:\
[![2020061515033808bde98184696bc73348e5d30abb6b46.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061515033808bde98184696bc73348e5d30abb6b46.jpeg)](https://www.dicoding.com/academies/159/tutorials/6533?from=6519#)

Tulisan "**Custom Font**" akan berubah menjadi font **Oswald** sesuai dengan yang telah kita daftarkan.&#x20;

Jangan lupa! Setelah kita menambahkan _package_ atau pun asset ke dalam **pubspec.yaml** kita perlu melakukan **full restart** agar asset yang baru dapat digunakan dalam aplikasi.

### Mengubah Font Default

Selain kita dapat mengubah font family pada satu per satu _widget Text_, kita dapat membuat font yang kita daftarkan menjadi _default_. Caranya dengan menambahkan parameter <mark style="color:yellow;">`fontFamily`</mark> pada kelas <mark style="color:yellow;">`ThemeData`</mark> yang ada pada _parameter_ _theme_ di **MaterialApp** seperti berikut:

```
class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        fontFamily: 'Oswald',
        primarySwatch: Colors.blue,
      ),
      home: FirstScreen(),
    );
  }
}
```
