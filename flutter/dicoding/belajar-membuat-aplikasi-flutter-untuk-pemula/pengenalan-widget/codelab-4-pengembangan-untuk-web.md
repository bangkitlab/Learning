# 🧪 Codelab 4: Pengembangan untuk Web

Sejauh ini kita telah mengembangkan aplikasi Wisata Bandung untuk platform mobile. Dengan Flutter mengumumkan Flutter Web yang sudah masuk versi stable, artinya terdapat target platform tambahan yang perlu kita kerjakan jika ingin menyasar pengguna yang lebih luas. Bukan hanya web, pada codelab kali ini kita juga akan menerapkan layout yang responsif untuk platform mobile untuk ukuran layar yang lebih besar seperti tablet.

Hasil akhir dari codelab ini akan seperti berikut:

[![2021042521184504cad335f61fb247bf566b59f39d1bcf.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042521184504cad335f61fb247bf566b59f39d1bcf.gif)](https://www.dicoding.com/academies/159/tutorials/16762#)

Mari kita mulai!

1. Silakan buka project aplikasi Wisata Bandung Anda.
2.  Karena kita akan menambahkan target dukungan untuk web, jalankan perintah berikut pada terminal:

    ```
    flutter create .
    ```

    **Notes**: Saat ini Flutter Web belum mendukung hot reload, tetapi hanya hot restart. Jika Anda ingin menggunakan hot reload untuk proses pengembangan yang lebih cepat, kami sarankan menggunakan platform Flutter Desktop yang bisa Anda aktfkan dengan mengikuti langkah Set up pada tautan [berikut](https://flutter.dev/desktop#set-up).
3. Sekarang jalankan aplikasi Anda. Aplikasi Akan berjalan dengan baik di browser, tetapi kita akan menemui masalah dalam aspek ukuran, seperti list yang terlalu besar seperti berikut:\
   [![20210425212011200cee8d5e13cee4349a47afe62b8894.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425212011200cee8d5e13cee4349a47afe62b8894.jpeg)](https://www.dicoding.com/academies/159/tutorials/16762#)
4.  Karena kita telah membuat aplikasi mobile lalu ingin membuat versi webnya, maka secara tidak langsung kita telah menerapkan _mobile-first design_. Sekarang kita perlu menentukan pada ukuran berapa _layout mobile_ini sudah tidak sesuai dan perlu diubah tampilannya. Untuk memudahkan, mari kita tampilkan lebar browser atau layar ke dalam teks AppBar.

    ```
    AppBar(
      title:
          Text('Wisata Bandung. Size: ${MediaQuery.of(context).size.width}'),
    ),
    ```
5. Cobalah mengubah ukuran window browser dan cari breakpoint atau titik di mana layout sudah tidak sesuai.\
   [![202104252129582c9a151a3718b180eb71a45f3688381e.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252129582c9a151a3718b180eb71a45f3688381e.jpeg)](https://www.dicoding.com/academies/159/tutorials/16762#)\
   Sebagai contoh, pada ukuran lebar di atas 600 sudah banyak ruang kosong yang lebih baik ditempati oleh widget lain. Maka, kita akan gunakan ukuran lebar 600 sebagai batas breakpoint ukuran mobile.
6.  Pada ukuran lebar di atas 600 kita akan buat tampilan yang berbeda menggunakan grid. Sebelumnya, mari pindahkan tampilan ListView menjadi widget tersendiri.

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title:
                Text('Wisata Bandung. Size: ${MediaQuery.of(context).size.width}'),
          ),
          body: TourismPlaceList(),
        );
      }
    }
     
    class TourismPlaceList extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return ListView.builder(...);
      }
    }
    ```
7.  Kemudian buat widget baru untuk menampilkan GridView.

    ```
    class TourismPlaceGrid extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Padding(
          padding: const EdgeInsets.all(24.0),
          child: GridView.count(
            crossAxisCount: 4,
            children: [],
          ),
        );
      }
    }
    ```
8.  Selanjutnya ubah body dari MainScreen untuk menampilkan TourismPlaceList atau TourismPlaceGrid. Kita akan memanfaatkan widget LayoutBuilder untuk mendapatkan ukuran layar.

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title:
                Text('Wisata Bandung. Size: ${MediaQuery.of(context).size.width}'),
          ),
          body: LayoutBuilder(
            builder: (BuildContext context, BoxConstraints constraints) {
              if (constraints.maxWidth <= 600) {
                return TourismPlaceList();
              } else {
                return TourismPlaceGrid();
              }
            },
          ),
        );
      }
    }
    ```

    Tampilan aplikasi di atas lebar 600 akan kosong karena kita belum mendefinisikan item untuk ditampilkan.
9. Tampilan item grid yang akan kita buat akan seperti di bawah ini. Cobalah untuk membuat tampilan Card seperti ini dulu sebelum melihat kode pada langkah berikutnya.\
   [![20210425213315651632e6d76ceea1b377702b23220ba2.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425213315651632e6d76ceea1b377702b23220ba2.jpeg)](https://www.dicoding.com/academies/159/tutorials/16762#)
10. Berikut ini adalah tampilan untuk Card di atas:

    ```
    GridView.count(
      crossAxisCount: 4,
      children: tourismPlaceList.map((place) {
        return InkWell(
          onTap: () {
            Navigator.push(context, MaterialPageRoute(builder: (context) {
              return DetailScreen(place: place);
            }));
          },
          child: Card(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: [
                Expanded(
                  child: Image.asset(
                    place.imageAsset,
                    fit: BoxFit.cover,
                  ),
                ),
                SizedBox(height: 8),
                Padding(
                  padding: const EdgeInsets.only(left: 8.0),
                  child: Text(
                    place.name,
                    style: TextStyle(
                      fontSize: 16.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ),
                Padding(
                  padding: const EdgeInsets.only(left: 8.0, bottom: 8.0),
                  child: Text(
                    place.location,
                  ),
                ),
              ],
            ),
          ),
        );
      }).toList(),
    ),
    ```
11. Jalankan aplikasi untuk melihat perubahan. Anda dapat melakukan duplikasi data dummy agar tampilan data menjadi semakin banyak.\
    [![20210425213432eaeb8f3740bbd790e4e00694a0feeeca.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425213432eaeb8f3740bbd790e4e00694a0feeeca.png)](https://www.dicoding.com/academies/159/tutorials/16762#)\
    Namun, untuk ukuran resolusi layar yang lebih besar lagi tampilan grid dengan empat kolom akan terlihat terlalu besar.\
    [![202104252135262e5672e9b965e68cd1129074d325162a.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252135262e5672e9b965e68cd1129074d325162a.png)](https://www.dicoding.com/academies/159/tutorials/16762#)\
    Geser kembali ukuran jendela browser untuk menemukan titik di mana tampilan sudah harus berubah. Misalnya, kita ambil ukuran lebar di atas 1200 akan menampilkan 6 kolom.
12. Tambahkan lagi kondisi pada LayoutBuilder. Kita akan menentukan jumlah kolom yang digunakan melalui parameter constructor.

    ```
    LayoutBuilder(
      builder: (BuildContext context, BoxConstraints constraints) {
        if (constraints.maxWidth <= 600) {
          return TourismPlaceList();
        } else if (constraints.maxWidth <= 1200) {
          return TourismPlaceGrid(gridCount: 4);
        } else {
          return TourismPlaceGrid(gridCount: 6);
        }
      },
    ),
    ```
13. Tambahkan constructor pada kelas TourismPlaceGrid.

    ```
    class TourismPlaceGrid extends StatelessWidget {
      final int gridCount;
     
      TourismPlaceGrid({required this.gridCount});
     
      @override
      Widget build(BuildContext context) {
        return Padding(
          padding: const EdgeInsets.all(16.0),
          child: GridView.count(
            crossAxisCount: gridCount,
            children: tourismPlaceList.map((place) {
              return InkWell(...);
            }).toList(),
          ),
        );
      }
    }
    ```
14. Jalankan aplikasi dan lihat perubahan. Tampilan untuk lebar resolusi 1920 sudah lebih baik dari sebelumnya.\
    [![20210425214039ed7d05ee1ed33342eff8a68008d64b13.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425214039ed7d05ee1ed33342eff8a68008d64b13.png)](https://www.dicoding.com/academies/159/tutorials/16762#)
15. Selanjutnya mari tambahkan jarak antara item supaya tidak terlalu rapat.

    ```
    GridView.count(
      crossAxisCount: gridCount,
      crossAxisSpacing: 16,
      mainAxisSpacing: 16,
      children: tourismPlaceList.map((place) {
        return InkWell(...);
      }).toList(),
    ),
    ```
16. Terakhir untuk halaman daftar tempat wisata, karena Flutter web belum secara otomatis memiliki scrollbar untuk browser, maka kita perlu menambahkannya sendiri. Tambahkan widget Scrollbar sebagai widget paling atas dari TourismPlaceGrid.

    ```
    Scrollbar(
      isAlwaysShown: true,
      child: Padding(
        padding: const EdgeInsets.all(24.0),
        child: GridView.count(...),
      ),
    );
    ```
17. Jangan lupa untuk menghapus kembali teks ukuran pada AppBar.

    ```
    AppBar(
      title: Text('Wisata Bandung'),
    ),
    ```
18. Selanjutnya kita akan mulai memodifikasi tampilan halaman detail. Seperti yang Anda lihat ketika menjalankan aplikasi, halaman detail tampak kurang estetik untuk ukuran resolusi yang lebar. Untuk ukuran lebar di atas 800, kita akan membuat tampilannya seperti ini:\
    [![2021042521424334e5fa0a54aca6abe1813edcb1470eb0.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042521424334e5fa0a54aca6abe1813edcb1470eb0.png)](https://www.dicoding.com/academies/159/tutorials/16762#)
19. Kita gunakan LayoutBuilder untuk memisahkan tampilan berdasarkan breakpoint.

    ```
    class DetailScreen extends StatelessWidget {
      final TourismPlace place;
     
      DetailScreen({required this.place});
     
      @override
      Widget build(BuildContext context) {
        return LayoutBuilder(
          builder: (BuildContext context, BoxConstraints constraints) {
            if (constraints.maxWidth > 800) {
              return DetailWebPage(place: place);
            } else {
              return DetailMobilePage(place: place);
            }
          },
        );
      }
    }
    ```

    Pindahkan widget yang sudah ada ke dalam kelas DetailMobilePage.

    ```
    class DetailMobilePage extends StatelessWidget {
      final TourismPlace place;
      
      const DetailMobilePage({required this.place});
     
      @override
      Widget build(BuildContext context) {
        return Scaffold(...);
      }
    }
    ```

    Buat juga kelas serupa untuk DetailWebPage.
20. Tidak ada perbedaan konten yang ditampilkan pada halaman detail, tetapi hanya susunannya saja yang berbeda. Dari gambar sebelumnya apakah Anda dapat menganalisis bagaimana layoutnya disusun? Jika belum, maka kurang lebihnya akan seperti berikut:\
    [![202104252144172b6214baa252be35dece119e3ebd0bc6.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252144172b6214baa252be35dece119e3ebd0bc6.png)](https://www.dicoding.com/academies/159/tutorials/16762#)
21. Mari kita mulai dengan Column pertama. Tambahkan Text untuk judul, lalu Row untuk struktur layout di bawahnya. Tambahkan jarak menggunakan widget SizedBox.

    ```
    Scaffold(
      body: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Text(
            'Wisata Bandung',
            style: TextStyle(
              fontFamily: 'Staatliches',
              fontSize: 32,
            ),
          ),
          SizedBox(height: 32),
          Row(
            children: [],
          ),
        ],
      ),
    );
    ```
22. Widget Row akan berisi children seperti berikut:

    ```
    Row(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Expanded(
          child: Column(
            children: [],
          ),
        ),
        SizedBox(width: 32),
        Expanded(
          child: Card(...),
        ),
      ],
    ),
    ```

    Sementara Card untuk detail informasi tempat wisata memiliki widget seperti berikut:

    ```
    Card(
      child: Container(
        padding: const EdgeInsets.all(16),
        child: Column(
          mainAxisSize: MainAxisSize.max,
          children: <Widget>[
            Container(
              child: Text(
                place.name,
                textAlign: TextAlign.center,
                style: TextStyle(
                  fontSize: 30.0,
                  fontFamily: 'Staatliches',
                ),
              ),
            ),
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                Row(
                  children: <Widget>[
                    Icon(Icons.calendar_today),
                    SizedBox(width: 8.0),
                    Text(
                      place.openDays,
                      style: informationTextStyle,
                    ),
                  ],
                ),
                FavoriteButton(),
              ],
            ),
            Row(
              children: <Widget>[
                Icon(Icons.access_time),
                SizedBox(width: 8.0),
                Text(
                  place.openTime,
                  style: informationTextStyle,
                ),
              ],
            ),
            SizedBox(height: 8.0),
            Row(
              children: <Widget>[
                Icon(Icons.monetization_on),
                SizedBox(width: 8.0),
                Text(
                  place.ticketPrice,
                  style: informationTextStyle,
                ),
              ],
            ),
            Container(
              padding: EdgeInsets.symmetric(vertical: 16.0),
              child: Text(
                place.description,
                textAlign: TextAlign.justify,
                style: TextStyle(
                  fontSize: 16.0,
                  fontFamily: 'Oxygen',
                ),
              ),
            ),
          ],
        ),
      ),
    ),

    ```
23. Widget Column terakhir kita gunakan untuk menampilkan gambar dari aset dan daftar gambar dari internet.

    ```
    Column(
      children: [
        ClipRRect(
          child: Image.asset(place.imageAsset),
          borderRadius: BorderRadius.circular(10),
        ),
        SizedBox(height: 16),
        Container(
          height: 150,
          padding: const EdgeInsets.only(bottom: 16),
          child: ListView(
            scrollDirection: Axis.horizontal,
            children: place.imageUrls.map((url) {
              return Padding(
                padding: const EdgeInsets.all(4.0),
                child: ClipRRect(
                  borderRadius: BorderRadius.circular(10),
                  child: Image.network(url),
                ),
              );
            }).toList(),
          ),
        ),
      ],
    ),
    ```

    Sekarang tampilan aplikasi akan seperti ini:\
    [![202104252146170e250c800527cf4c484f2170eb260d20.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252146170e250c800527cf4c484f2170eb260d20.png)](https://www.dicoding.com/academies/159/tutorials/16762#)
24. Mari tambahkan Padding untuk memberikan jarak antara konten dengan pinggir halaman.

    ```
    Scaffold(
      body: Padding(
        padding: const EdgeInsets.symmetric(
          vertical: 16,
          horizontal: 64,
        ),
        child: Column(...),
      ),
    );
    ```
25. Kita juga dapat menentukan ukuran lebar maksimum dari konten yang tampil menggunakan Container.

    ```
    Padding(
      padding: const EdgeInsets.symmetric(
        vertical: 16,
        horizontal: 64,
      ),
      child: Center(
        child: Container(
          width: 1200,
          child: Column(...),
        ),
      ),
    ),
    ```

    Lihat perubahan aplikasi, sekarang halaman detail akan memiliki ukuran lebar maksimal 1200 pixel.\
    [![202104252148180888709da1500c76c8055f582eb966b2.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202104252148180888709da1500c76c8055f582eb966b2.png)](https://www.dicoding.com/academies/159/tutorials/16762#)
26. Satu hal yang penting untuk kita perhatikan adalah menghadirkan pengalaman pengguna yang nyaman saat menggunakan platform apa pun. Untuk itu, tambahkan Scrollbar pada daftar gambar. Selain itu, tambahkan juga widget Container untuk memberikan ukuran tinggi pada ListView.

    ```
    Scrollbar(
      isAlwaysShown: true,
      child: Container(
        height: 150,
        padding: const EdgeInsets.only(bottom: 16),
        child: ListView(
          scrollDirection: Axis.horizontal,
          children: widget.place.imageUrls.map((url) {
            return Padding(...);
          }).toList(),
        ),
      ),
    ),
    ```
27. Jika Anda menggunakan touchpad pada laptop, gestur swipe pada scrollbar akan berjalan dengan normal. Namun, ketika melakukan drag menggunakan mouse, fitur scrollbar tidak berjalan. Solusi yang bisa Anda lakukan adalah menggunakan ScrollController. Inisialisasikan objek ScrollController di atas method build().

    ```
    final _scrollController = ScrollController();
    ```

    Tambahkan \_scrollController pada Scrollbar dan ListView.

    ```
    Scrollbar(
      isAlwaysShown: true,
      controller: _scrollController,
      child: Container(
        height: 150,
        padding: const EdgeInsets.only(bottom: 16),
        child: ListView(
          controller: _scrollController,
          scrollDirection: Axis.horizontal,
          children: widget.place.imageUrls.map((url) {
            return Padding(...);
          }).toList(),
        ),
      ),
    ),

    ```
28. Seperti halnya TextEditingController, ScrollController juga harus di-dispose ketika widget sudah tidak lagi digunakan. Ubahlah DetailWebPage menjadi StatefulWidget supaya kita bisa memanggil method dispose.\
    [![20210425215045a90eb71cda047e081068c3b2be85e746.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425215045a90eb71cda047e081068c3b2be85e746.gif)](https://www.dicoding.com/academies/159/tutorials/16762#)
29. Tambahkan method dispose setelah method build() lalu panggil \_scrollController.dispose();

    ```
    @override
    void dispose() {
      _scrollController.dispose();
      super.dispose();
    }
    ```
30. Selamat! Sekarang tampilan aplikasi Wisata Bandung sudah lebih sesuai untuk ukuran resolusi layar yang lebih besar. Anda telah belajar banyak menyusun halaman menggunakan widget, hingga membuat halaman yang dapat responsif terhadap perbedaan ukuran layar. Kode selengkapnya untuk codelab ini dapat Anda temukan pada tautan: [https://github.com/dicodingacademy/a159-flutter-pemula-labs/tree/codelab4-final](https://github.com/dicodingacademy/a159-flutter-pemula-labs/tree/codelab4-final).
