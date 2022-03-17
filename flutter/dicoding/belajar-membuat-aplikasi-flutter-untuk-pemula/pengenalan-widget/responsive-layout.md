# 📖 Responsive Layout

Seperti yang kita tahu, Flutter merupakan framework untuk mengembangkan aplikasi pada berbagai platform. Pada platform mobile sendiri tersedia banyak ukuran layar dari ukuran jam hingga tablet. Ditambah Flutter baru saja mengumumkan dukungan untuk platform web dan desktop. Itu artinya, satu hal yang penting untuk kita pahami adalah bagaimana menerapkan layout yang mampu beradaptasi dengan berbagai ukuran layar yang berbeda.

Pada materi ini kita akan mulai membahas bagaimana mengimplementasikan layout yang responsif.

### MediaQuery

Pendekatan pertama yang akan kita lakukan adalah menggunakan Media Query. Jika Anda sudah familier dengan pengembangan web, mungkin Anda sudah tidak asing dengan konsep ini. MediaQuery adalah kelas yang dapat kita gunakan untuk mendapatkan ukuran dan juga orientasi layar.

Mari kita lihat contoh penerapan MediaQuery.

```
class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    Size screenSize = MediaQuery.of(context).size;
    Orientation orientation = MediaQuery.of(context).orientation;
 
    return Scaffold(
      backgroundColor: Colors.blueGrey,
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          Text(
            'Screen width: ${screenSize.width.toStringAsFixed(2)}',
            style: TextStyle(color: Colors.white, fontSize: 18),
            textAlign: TextAlign.center,
          ),
          Text(
            'Orientation: $orientation',
            style: TextStyle(color: Colors.white, fontSize: 18),
            textAlign: TextAlign.center,
          ),
        ],
      ),
    );
  }
}
```

Sekarang jalankan aplikasi untuk melihat ukuran layarnya.

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425210419157adacac812a00588581d94981a1f9b.png)

[![202104252104366b3ce04197eb18619ce31b70c431e387.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252104366b3ce04197eb18619ce31b70c431e387.png)](https://www.dicoding.com/academies/159/tutorials/16760?from=8611#)

### LayoutBuilder

Cara lain yang bisa kita gunakan adalah dengan widget LayoutBuilder. Perbedaan umum antara MediaQuery dan Layout Builder adalah MediaQuery akan mengembalikan ukuran layar yang digunakan, sedangkan LayoutBuilder mengembalikan ukuran maksimum dari widget tertentu.

Berikut ini adalah contoh kode yang menunjukkan perbedaan antara MediaQuery dan LayoutBuilder:

```
class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    Size screenSize = MediaQuery.of(context).size;
 
    return Scaffold(
      backgroundColor: Colors.blueGrey,
      body: Row(
        children: [
          Expanded(
            child: LayoutBuilder(
              builder: (BuildContext context, BoxConstraints constraints) {
                return Column(
                  mainAxisAlignment: MainAxisAlignment.center,
                  crossAxisAlignment: CrossAxisAlignment.stretch,
                  children: [
                    Text(
                      'MediaQuery: ${screenSize.width.toStringAsFixed(2)}',
                      style: TextStyle(color: Colors.white, fontSize: 18),
                      textAlign: TextAlign.center,
                    ),
                    Text(
                      'LayoutBuilder: ${constraints.maxWidth}',
                      style: TextStyle(color: Colors.white, fontSize: 18),
                      textAlign: TextAlign.center,
                    ),
                  ],
                );
              },
            ),
          ),
          Expanded(
            flex: 3,
            child: LayoutBuilder(
              builder: (BuildContext context, BoxConstraints constraints) {
                return Container(
                  color: Colors.white,
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    crossAxisAlignment: CrossAxisAlignment.stretch,
                    children: [
                      Text(
                        'MediaQuery: ${screenSize.width.toStringAsFixed(2)}',
                        style: TextStyle(color: Colors.blueGrey, fontSize: 18),
                        textAlign: TextAlign.center,
                      ),
                      Text(
                        'LayoutBuilder: ${constraints.maxWidth}',
                        style: TextStyle(color: Colors.blueGrey, fontSize: 18),
                        textAlign: TextAlign.center,
                      ),
                    ],
                  ),
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}
```

Hasil ketika dijalankan pada browser akan seperti ini:

[![20210425210552b66b987a61408699450be54573c3dc0b.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425210552b66b987a61408699450be54573c3dc0b.png)](https://www.dicoding.com/academies/159/tutorials/16760?from=8611#)

Ubahlah ukuran jendela browser untuk melihat perubahan ukuran layar atau media yang digunakan.

Dengan mendapatkan ukuran lebar dan tinggi layar seperti di atas, kita bisa menentukan tampilan konten berdasarkan ukuran layar yang digunakan. Dalam responsive design, terdapat breakpoint yang merupakan “titik” di mana layout akan beradaptasi untuk memberikan pengalaman pengguna sebaik mungkin.

Dengan kode di bawah ini berarti akan terdapat tiga model tampilan berdasarkan ukuran layar:

```
class ResponsivePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(),
      body: LayoutBuilder(
        builder: (BuildContext context, BoxConstraints constraints) {
          if (constraints.maxWidth < 600) {
            return ListView(
              children: _generateContainers(),
            );
          } else if (constraints.maxWidth < 900) {
            return GridView.count(
              crossAxisCount: 2,
              children: _generateContainers(),
            );
          } else {
            return GridView.count(
              crossAxisCount: 6,
              children: _generateContainers(),
            );
          }
        },
      ),
    );
  }
 
  List<Widget> _generateContainers() {
    return List<Widget>.generate(20, (index) {
      return Container(
        margin: const EdgeInsets.all(8),
        color: Colors.blueGrey,
        height: 200,
      );
    });
  }
}
```

Berikut adalah tampilan dari kode di atas ketika dijalankan:

![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425211022224c0de6d6751d5c57b5e4b7e39712a3.gif)
