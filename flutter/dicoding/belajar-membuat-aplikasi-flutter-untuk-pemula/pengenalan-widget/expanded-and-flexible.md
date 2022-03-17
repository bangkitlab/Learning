# 📖 Expanded & Flexible

Sejauh ini kita telah mempelajari beberapa _widget_ dasar dan bagaimana menyusunnya secara horizontal maupun vertikal. Dalam pengembangan aplikasi _mobile_ kita tahu bahwa terdapat banyak sekali perangkat dengan ukuran layar yang berbeda pula. Untuk itu penting bagi kita untuk bisa menyusun tampilan yang responsif terhadap ukuran layar.

Kira-kira bagaimana Anda akan menyusun layout dengan tampilan seperti berikut?\
[![20200615161011d0bb9c837344b597049b67d0898cbf75.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615161011d0bb9c837344b597049b67d0898cbf75.jpeg)](https://www.dicoding.com/academies/159/tutorials/8610?from=8616#)

Tentunya akan sangat merepotkan apabila kita mengatur tinggi dari masing-masing kotak, bukan? Belum lagi jika harus mengembangkan aplikasi di ukuran yang lebih besar seperti perangkat tablet.&#x20;

### Expanded

Flutter memiliki widget Expanded yang dapat mengembangkan child dari Row atau Column sesuai dengan ruang yang tersedia. Cara menggunakannya Anda cukup membungkus masing-masing child ke dalam Expanded.

```
class Rainbow extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: <Widget>[
        Expanded(
          child: Container(
            color: Colors.red,
          ),
        ),
        Expanded(
          child: Container(
            color: Colors.orange,
          ),
        ),
        Expanded(
          child: Container(
            color: Colors.yellow,
          ),
        ),
        Expanded(
          child: Container(
            color: Colors.green,
          ),
        ),
        Expanded(
          child: Container(
            color: Colors.blue,
          ),
        ),
        Expanded(
          child: Container(
            color: Colors.indigo,
          ),
        ),
        Expanded(
          child: Container(
            color: Colors.purple,
          ),
        ),
      ],
    );
  }
}
```

Saat aplikasi dijalankan, masing-masing container akan menempati ruang kosong yang ada. Jika Anda menjalankan di ukuran layar yang berbeda, maka ukuran container juga akan menyesuaikan.\
[![2020061516111745a046ee02c506aa469a828fe8cb8cdd.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061516111745a046ee02c506aa469a828fe8cb8cdd.jpeg)](https://www.dicoding.com/academies/159/tutorials/8610?from=8616#)

Bisa kita lihat seluruh container menempati ruang dengan ukuran yang sama. Ini disebabkan Expanded memiliki parameter flex yang memiliki nilai default 1. Anda dapat mengubah nilai flex ini sesuai perbandingan yang diinginkan. Misalnya Anda memberikan nilai flex 2 pada salah satu container.

```
Expanded(
  flex: 2,
  child: Container(
    color: Colors.blue,
  ),
),
```

Maka container berwarna biru ini akan menjadi lebih besar dengan perbandingan 2/(1 + 1 + 1 + 1 + 2 + 1 + 1) atau 2/8 dari halaman.\
[![20200615161338103190234521f130325fd1dabc87f651.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615161338103190234521f130325fd1dabc87f651.jpeg)](https://www.dicoding.com/academies/159/tutorials/8610?from=8616#)

### Flexible

Sama seperti Expanded, widget Flexible digunakan untuk mengatur ukuran widget di dalam Row atau Column secara fleksibel. Perbedaan Flexible dan Expanded adalah widget Flexible memungkinkan _child widget_-nya berukuran lebih kecil dibandingkan ukuran ruang yang tersisa. Sementara, child widget dari Expanded harus menempati ruang yang tersisa dari Column atau Row.

Berikut ini adalah contoh perbedaan antara Expanded dan Flexible:

[![2021042515350622310934015b880e289e8ece3afdeb48.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042515350622310934015b880e289e8ece3afdeb48.png)](https://www.dicoding.com/academies/159/tutorials/8610?from=8616#)

Kode untuk tampilan seperti di atas adalah seperti berikut:

```
class ExpandedFlexiblePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Column(
          children: [
            Row(
              children: [
                ExpandedWidget(),
                FlexibleWidget(),
              ],
            ),
            Row(
              children: [
                ExpandedWidget(),
                ExpandedWidget(),
              ],
            ),
            Row(
              children: [
                FlexibleWidget(),
                FlexibleWidget(),
              ],
            ),
            Row(
              children: [
                FlexibleWidget(),
                ExpandedWidget(),
              ],
            ),
          ],
        ),
      ),
    );
  }
}
 
class ExpandedWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Expanded(
      child: Container(
        decoration: BoxDecoration(
          color: Colors.teal,
          border: Border.all(color: Colors.white),
        ),
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Text(
            'Expanded',
            style: TextStyle(
              color: Colors.white,
              fontSize: 24,
            ),
          ),
        ),
      ),
    );
  }
}
 
class FlexibleWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Flexible(
      child: Container(
        decoration: BoxDecoration(
          color: Colors.tealAccent,
          border: Border.all(color: Colors.white),
        ),
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Text(
            'Flexible',
            style: TextStyle(
              color: Colors.teal,
              fontSize: 24,
            ),
          ),
        ),
      ),
    );
  }
}

```

Dokumentasi berikut ini dapat Anda pelajari untuk memaksimalkan penggunaan widget Expanded dan Flexible:

* [Expanded Class](https://api.flutter.dev/flutter/widgets/Expanded-class.html)
* [Flexible Class](https://api.flutter.dev/flutter/widgets/Flexible-class.html)
