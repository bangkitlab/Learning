# 🧪 Codelab 3: Menampilkan Daftar Tempat Wisata

Sekarang kita telah sampai pada _codelab_ ketiga. Di akhir codelab ini kita akan menyelesaikan project aplikasi Wisata Bandung. Hasil akhir aplikasi akan seperti berikut:

[![20210425155910c1f9014e6bab709cf11f00357e752ae2.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425155910c1f9014e6bab709cf11f00357e752ae2.gif)](https://www.dicoding.com/academies/159/tutorials/8621?from=16760#)

Mari kita mulai. Buka kembali project codelab Anda sebelumnya.

1.  Pertama kali yang kita lakukan adalah membuat halaman baru untuk menampilkan daftar tempat wisata. Buat berkas baru **main\_screen.dart** lalu buat widget untuk halaman **MainScreen**.

    ```
    import 'package:flutter/material.dart';
     
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold();
      }
    }
    ```
2.  Jangan lupa untuk mengganti halaman utama yang ditampilkan pada berkas **main.dart.**

    ```
    void main() => runApp(MyApp());
     
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Wisata Bandung',
          theme: ThemeData(),
          home: MainScreen(),
        );
      }
    }
    ```
3.  Pada **MainScreen** tambahkan **AppBar**untuk judul halaman.

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Wisata Bandung'),
          ),
        );
      }
    }
    ```
4.  Sebagai body dari Scaffold kita akan menggunakan widget Card. Widget ini adalah widget material design yang menghasilkan tampilan seperti kartu dengan ujung yang membulat dan bayangan di belakang. Kemudian susun _Row_ dan _Column_ seperti contoh untuk menyusun _child_ dari _Card_. Kodenya akan seperti berikut:

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Wisata Bandung'),
          ),
          body: Card(
            child: Row(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: <Widget>[
                Image.asset('images/farm-house.jpg'),
                Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    mainAxisSize: MainAxisSize.min,
                    children: <Widget>[
                      Text(
                        'Farm House Lembang',
                        style: TextStyle(fontSize: 16.0),
                      ),
                      SizedBox(
                        height: 10,
                      ),
                      Text('Lembang'),
                    ],
                  ),
                )
              ],
            ),
          ),
        );
      }
    }
    ```
5.  Jalankan aplikasinya. Aplikasi akan mengalami _overflow_karena aset gambar yang terlalu besar. Kita bisa saja mengatur tinggi gambar secara manual, namun kali ini kita akan memanfaatkan widget Expanded agar tampilan juga dapat menyesuaikan di perangkat yang lebih besar atau kecil. Bungkus masing-masing item dari widget row ke dalam Expanded. Berikan parameter flex yang menurut Anda cocok.

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Wisata Bandung'),
          ),
          body: Card(
            child: Row(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: <Widget>[
                Expanded(
                  flex: 1,
                  child: Image.asset('images/farm-house.jpg'),
                ),
                Expanded(
                  flex: 2,
                  child: Padding(
                    padding: const EdgeInsets.all(8.0),
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      mainAxisSize: MainAxisSize.min,
                      children: <Widget>[
                        Text(
                          'Farm House Lembang',
                          style: TextStyle(fontSize: 16.0),
                        ),
                        SizedBox(
                          height: 10,
                        ),
                        Text('Lembang'),
                      ],
                    ),
                  ),
                ),
              ],
            ),
          ),
        );
      }
    }
    ```
6.  Item pertama Anda sudah siap. Selanjutnya kita akan membuat kartu ini bisa diklik untuk berpindah ke halaman detail. Kita bisa menggunakan widget InkWell yang menyediakan parameter onTap. Pindahkan widget Card Anda menjadi child dari InkWell.

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Wisata Bandung'),
          ),
          body: InkWell(
            onTap: () {},
            child: Card(...),
          ),
        );
      }
    }
    ```
7.  Parameter <mark style="color:yellow;">`onTap`</mark> menerima argumen berupa sebuah fungsi lambda. Di sini kita akan menambahkan Navigator untuk berpindah ke halaman detail.

    ```
    onTap: () {
      Navigator.push(context, MaterialPageRoute(builder: (context) {
        return DetailScreen();
      }));
    },
    ```

    Jalankan aplikasi. Seharusnya sampai langkah ini aplikasi Anda sudah dapat berpindah halaman ketika item diklik.
8. Selanjutnya kita akan menampilkan beberapa item ke MainScreen. Di kelas ini kita masih menggunakan data statis dan lokal yang disimpan pada objek _List_. Sebelumnya, buatlah kelas sebagai _blueprint_ untuk menyimpan objek tempat wisata kita. Buat folder baru di dalam folder **lib** dengan cara klik kanan folder **lib -> New -> Package,** lalu berikan nama **model**. Di dalam folder model buat berkas dart bernama **tourism\_place.dart**.
9.  Di dalam **tourism\_place.dart** buat data _class_ yang akan menjadi _blueprint_ objek tempat wisata.

    ```
    class TourismPlace {
      String name;
      String location;
      String description;
      String openDays;
      String openTime;
      String ticketPrice;
      String imageAsset;
      List<String> imageUrls;
     
      TourismPlace({
        required this.name,
        required this.location,
        required this.description,
        required this.openDays,
        required this.openTime,
        required this.ticketPrice,
        required this.imageAsset,
        required this.imageUrls,
      });
    }
    ```
10. Siapkan data statis yang ingin ditampilkan Anda dapat menyalin kode berikut dan taruh di berkas **tourism\_place.dart** paling bawah.

    ```
    var tourismPlaceList = [
      TourismPlace(
        name: 'Farm House Lembang',
        location: 'Lembang',
        description:
            'Berada di jalur utama Bandung-Lembang, Farm House menjadi objek wisata yang tidak pernah sepi pengunjung. Selain karena letaknya strategis, kawasan ini juga menghadirkan nuansa wisata khas Eropa. Semua itu diterapkan dalam bentuk spot swafoto Instagramable.',
        openDays: 'Open Everyday',
        openTime: '09:00 - 20:00',
        ticketPrice: 'Rp 25000',
        imageAsset: 'images/farm-house.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'
        ],
      ),
      TourismPlace(
        name: 'Observatorium Bosscha',
        location: 'Lembang',
        description:
            'Memiliki beberapa teleskop, antara lain, Refraktor Ganda Zeiss, Schmidt Bimasakti, Refraktor Bamberg, Cassegrain GOTO, dan Teleskop Surya. Refraktor Ganda Zeiss adalah jenis teleskop terbesar untuk meneropong bintang. Benda ini diletakkan pada atap kubah sehingga saat teropong digunakan, atap tersebut harus dibuka. Observatorium Bosscha boleh dikunjungi oleh siapa pun, tanpa tiket. Namun, bagi yang ingin menggunakan teleskop Zeiss, wajib mendaftarkan diri. Untuk instansi atau lembaga pendidikan, diberikan jadwal hari Selasa sampai Jumat. Sementara itu, kunjungan individu dibuka setiap hari Sabtu.',
        openDays: 'Open Tuesday - Saturday',
        openTime: '09:00 - 14:30',
        ticketPrice: 'Rp 20000',
        imageAsset: 'images/bosscha.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/12/6b/63/0b/bosscha-observatory.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-p/0d/6a/88/9b/photo3jpg.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-o/11/3f/04/39/p-20171111-110220-largejpg.jpg',
        ],
      ),
      TourismPlace(
        name: 'Jalan Asia Afrika',
        location: 'Kota Bandung',
        description:
            'Jalan Asia Afrika di Bandung memiliki kaitan yang sangat erat dengan pendirian kota Kembang ini. Karena pada saat itu, Gubernur Jenderal Herman Willem Deaendels dari Belanda menancapkan tongkatnya saat memerintahkan pendirian kota ini, yang kemudian diabadikan menjadi tugu Bandung Nol Kilometer.',
        openDays: 'Open Everyday',
        openTime: '24 hours',
        ticketPrice: 'Free',
        imageAsset: 'images/jalan-asia-afrika.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/0d/c2/e7/e6/quotes-kota-bandung.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-w/17/f4/44/01/jalan-asia-afrika.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-s/0a/ef/36/e2/jalan-asia-afrika.jpg',
        ],
      ),
      TourismPlace(
        name: 'Stone Garden',
        location: 'Padalarang',
        description:
            'Stone Garden atau Taman Batu di Padalarang – Bandung ini adalah nama secara harafiah untuk apa yang akan kita lihat jika berada di sana. Hamparan batu yang artistik membuat kita merasa tidak sedang berada di Bandung, apalagi di Padalarang. Hamparan batu yang dimaksud bukan terhampar begitu saja di atas tanah luas yang menjadi permukaannya. Batu-batu besar yang ukuran pastinya bervariasi tersusun seperti memiliki suatu formasi matematis.',
        openDays: 'Open Everyday',
        openTime: '06:00 - 17:00',
        ticketPrice: 'Rp 3000',
        imageAsset: 'images/stone-garden.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/15/01/d7/4b/p-20180510-153310-01.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-w/15/68/00/32/stone-garden-citatah.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-o/0d/a2/cb/05/stone-garden-citatah.jpg',
        ],
      ),
      TourismPlace(
        name: 'Taman Film Pasopati',
        location: 'Kota Bandung',
        description:
            'Menjadi salah satu tempat wisata di Bandung yang favorit, tentu Taman Film ini memiliki fasilitas cukup memadai. Pemberian fasilitas ini memiliki harapan para pengunjung akan merasa nyaman dan tak segan2 untuk kembali berkunjung terus menerus kesini. Beberapa fasilitas taman yang bisa kamu nikmati diantaranya seperti layar videotron besar berukuran 4×8 untuk memutar berbagai macam pilihan film seperti Film Indonesia, Bollywood, Korea, ataupun Indie Bandung.',
        openDays: 'Open Everyday',
        openTime: '24 hours',
        ticketPrice: 'Free',
        imageAsset: 'images/taman-film.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/08/8b/87/50/bandung-movie-park.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-o/17/67/d5/53/img-20190505-114509-largejpg.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-w/09/73/33/05/taman-film-pasopati.jpg',
        ],
      ),
      TourismPlace(
        name: 'Museum Geologi',
        location: 'Kota Bandung',
        description:
            'Museum Geologi didirikan pada tanggal 16 Mei 1929. Museum ini telah direnovasi dengan dana bantuan dari JICA (Japan International Cooperation Agency). Setelah mengalami renovasi, Museum Geologi dibuka kembali dan diresmikan oleh Wakil Presiden RI, Megawati Soekarnoputri pada tanggal 23 Agustus 2000. Sebagai salah satu monumen bersejarah, museum berada di bawah perlindungan pemerintah dan merupakan peninggalan nasional. Dalam Museum ini, tersimpan dan dikelola materi-materi geologi yang berlimpah, seperti fosil, batuan, mineral. Kesemuanya itu dikumpulkan selama kerja lapangan di Indonesia sejak 1850.',
        openDays: 'Open Saturday - Thursday',
        openTime: '09:00 - 15:30',
        ticketPrice: 'Rp 3000',
        imageAsset: 'images/museum-geologi.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-w/19/1c/8e/f7/geology-museum.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-o/11/a7/35/b7/geology-museum.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-s/1a/55/e0/dc/geology-museum.jpg',
        ],
      ),
      TourismPlace(
        name: 'Floating Market',
        location: 'Lembang',
        description:
            'Tempat wisata ini sepertinya memang ditujukan untuk wisata keluarga di Bandung. Di sini kita bisa menikmati suasana kawasan yang tertata rapi dan alami. Pada awalnya, floating market Lembang tidak begitu luas. Tapi sekarang sudah ekspansi dan memiliki banyak objek menarik baru. Nama floating market ini sepertinya merujuk pada stand tempat jualan makanan yang berada dalam perahu.',
        openDays: 'Open Everyday',
        openTime: '09:00 - 17:00',
        ticketPrice: 'Rp 20000',
        imageAsset: 'images/floating-market.png',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/17/f9/ff/f8/floating-market-bandung.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-p/1a/86/d3/cd/20200103-125059-largejpg.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-p/19/ce/b4/9b/img20181224120857-largejpg.jpg',
        ],
      ),
      TourismPlace(
        name: 'Kawah Putih',
        location: 'Ciwidey',
        description:
            'Kawah Putih adalah tempat wisata di Bandung yang paling terkenal. Berlokasi di Ciwidey, Jawa Barat, kurang lebih sekitar 50 KM arah selatan kota Bandung, Kawah Putih adalah sebuah danau yang terbentuk akibat dari letusan Gunung Patuha. Sesuai dengan namanya, tanah yang ada di kawasan ini berwarna putih akibat dari pencampuran unsur belerang.',
        openDays: 'Open Everyday',
        openTime: '07:00 - 17:00',
        ticketPrice: 'Rp 15000',
        imageAsset: 'images/kawah-putih.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/0b/6e/7c/ce/rocks-sticking-out-of.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-p/0b/35/30/14/white-crater.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-o/0a/8b/9a/79/2945-t00572-www-initempatwisat.jpg',
        ],
      ),
      TourismPlace(
        name: 'Ranca Upas',
        location: 'Ciwidey',
        description:
            'Ranca Upas Ciwidey adalah kawasan bumi perkemahan di bawah pengelolaan perhutani. Tempat ini berada di kawasan wisata Bandung Selatan, satu lokasi dengan kawah putih, kolam Cimanggu dan situ Patenggang. Banyak hal yang bisa dilakukan di kawasan wisata ini, seperti berkemah, berinteraksi dengan rusa, sampai bermain di water park dan mandi air panas.',
        openDays: 'Open Everyday',
        openTime: '24 hours',
        ticketPrice: 'Rp 20000',
        imageAsset: 'images/ranca-upas.jpg',
        imageUrls: [
          'https://media-cdn.tripadvisor.com/media/photo-o/1a/e0/7f/9c/kampung-cai-ranca-upas.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-w/13/ee/2f/87/ranca-upas.jpg',
          'https://media-cdn.tripadvisor.com/media/photo-w/13/ee/27/0a/ranca-upas.jpg',
        ],
      ),
    ];
    ```

    Jangan lupa untuk menambahkan _import_ berkas **tourism\_place.dart** pada file **main\_screen.dart**.

    ```
    import 'package:wisatabandung/model/tourism_place.dart';
    ```

    Untuk berkas aset yang digunakan dapat Anda unduh pada tautan [berikut](https://github.com/dicodingacademy/assets/raw/main/flutter\_pemula\_academy/assets\_wisata.zip).
11. Sesuai yang telah kita pelajari pada materi _ListView_, kita akan menampilkan variabel <mark style="color:yellow;">`tourismPlaceList`</mark> di atas menjadi item card yang dapat diklik. Tambahkan widget ListView sebagai _body_ dari Scaffold**.** Pindahkan widget FlatButton dan seluruh konten di dalamnya sebagai widget dari setiap item di dalam <mark style="color:yellow;">`tourismPlaceList`</mark>.

    ```
    class MainScreen extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text('Wisata Bandung'),
          ),
          body: ListView.builder(
            itemBuilder: (context, index) {
              final TourismPlace place = tourismPlaceList[index];
              return InkWell(
                onTap: () {
                  Navigator.push(context, MaterialPageRoute(builder: (context) {
                    return DetailScreen();
                  }));
                },
                child: Card(
                  child: Row(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: <Widget>[
                      Expanded(
                        flex: 1,
                        child: Image.asset(place.imageAsset),
                      ),
                      Expanded(
                        flex: 2,
                        child: Padding(
                          padding: const EdgeInsets.all(8.0),
                          child: Column(
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: <Widget>[
                              Text(
                                place.name,
                                style: TextStyle(fontSize: 16.0),
                              ),
                              SizedBox(
                                height: 10,
                              ),
                              Text(place.location),
                            ],
                          ),
                        ),
                      )
                    ],
                  ),
                ),
              );
            },
            itemCount: tourismPlaceList.length,
          ),
        );
      }
    }
    ```

    Jangan lupa untuk mengganti tampilan item secara dinamis sesuai data dari objek TourismPlace. Jalankan aplikasi untuk melihat hasil perubahan.
12. Agar halaman detail bisa menampilkan informasi sesuai tempat wisata yang dipilih, kita perlu mengirimkan data TourismPlace melalui _constructor_. Buka berkas **detail\_screen.dart** lalu tambahkan variabel serta _constructor_-nya.

    ```
    class DetailScreen extends StatelessWidget {
      final TourismPlace place;
      DetailScreen({required this.place});
     
      @override
      Widget build(BuildContext context) {...}
    }
    ```

    Tambahkan keyword required agar parameter place wajib disertakan ketika membuat objek **DetailScreen**. Sesuaikan juga informasi yang ditampilkan dengan property yang didapat dari _constructor_.

    ```
    class DetailScreen extends StatelessWidget {
      final TourismPlace place;
     
      DetailScreen({required this.place});
     
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          backgroundColor: Colors.black,
          body: SingleChildScrollView(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
                Image.asset(place.imageAsset),
                Container(
                  margin: EdgeInsets.only(top: 16.0),
                  child: Text(
                    place.name,
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 30.0,
                      fontFamily: 'Staatliches',
                    ),
                  ),
                ),
                Container(
                  margin: EdgeInsets.symmetric(vertical: 16.0),
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                    children: <Widget>[
                      Column(
                        children: <Widget>[
                          Icon(Icons.calendar_today),
                          SizedBox(height: 8.0),
                          Text(
                            place.openDays,
                            style: informationTextStyle,
                          ),
                        ],
                      ),
                      Column(
                        children: <Widget>[
                          Icon(Icons.access_time),
                          SizedBox(height: 8.0),
                          Text(
                            place.openTime,
                            style: informationTextStyle,
                          ),
                        ],
                      ),
                      Column(
                        children: <Widget>[
                          Icon(Icons.monetization_on),
                          SizedBox(height: 8.0),
                          Text(
                            place.ticketPrice,
                            style: informationTextStyle,
                          ),
                        ],
                      ),
                    ],
                  ),
                ),
                Container(
                  padding: EdgeInsets.all(16.0),
                  child: Text(
                    place.description,
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 16.0,
                      fontFamily: 'Oxygen',
                    ),
                  ),
                ),
                Container(
                  height: 150,
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
          ),
        );
      }
    }
    ```

    Jangan lupa untuk menambahkan data **place** pada _constructor_.

    ```
    Navigator.push(context, MaterialPageRoute(builder: (context) {
      return DetailScreen(place: place);
    }));
    ```
13. Selanjutnya, kita akan menambahkan tombol navigasi untuk kembali ke halaman daftar tempat wisata. Tombol ini akan kita taruh di atas gambar utama atau gambar dari aset. Kita akan menggunakan widget Stack. Widget ini digunakan untuk menyusun widget seperti Column atau Row, bedanya widget pada Stack disusun secara bertumpuk (stacked). Ubah kode Anda menjadi seperti berikut:

    ```
    Stack(
      children: <Widget>[
        Image.asset(place.imageAsset),
        IconButton(icon: Icon(Icons.arrow_back), onPressed: () {})
      ],
    ),
    ```

    Tambahkan fungsionalitas agar ketika icon back ini diklik akan kembali ke halaman sebelumnya.

    ```
    IconButton(
      icon: Icon(Icons.arrow_back),
      onPressed: () {
        Navigator.pop(context);
      },
    ),
    ```
14. Jika Anda jalankan aplikasi, ikon ini akan sedikit menabrak notification bar pada perangkat Android. Hal ini akan semakin terlihat apabila Anda menggunakan perangkat yang memiliki _notch_.\
    [![20200615174250855d26bbda154a8513f293024270f4a2.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615174250855d26bbda154a8513f293024270f4a2.jpeg)](https://www.dicoding.com/academies/159/tutorials/8621?from=16760#)\
    Lalu bagaimana mengatasinya? Masih ingat dengan SafeArea? Kita akan memanfaatkan widget SafeArea yang akan memberikan _padding_sesuai dengan sistem operasi yang digunakan sehingga widget akan berada di area yang aman. Buat widget SafeArea lalu pindahkan IconButton ke dalamnya.

    ```
    SafeArea(
      child: IconButton(
        icon: Icon(Icons.arrow_back),
        onPressed: () {
          Navigator.pop(context);
        },
      ),
    ),
    ```

    Lakukan juga beberapa perubahan tampilan supaya ikon navigasi tidak bertabarakan dengan latar belakangnya.

    ```
    SafeArea(
      child: Padding(
        padding: const EdgeInsets.all(8.0),
        child: CircleAvatar(
          backgroundColor: Colors.grey,
          child: IconButton(
            icon: Icon(
              Icons.arrow_back,
              color: Colors.white,
            ),
            onPressed: () {
              Navigator.pop(context);
            },
          ),
        ),
      ),
    ),
    ```
15. Terakhir, kita akan membuat fitur untuk menambahkan favorit. Fitur favorit ini memang belum lengkap, namun setidaknya cukup memberikan Anda gambaran bagaimana mengubah _state_ aplikasi dan bagaimana _widget_ dapat tampil sesuai dengan state yang ada.\
    \
    Buat StatefulWidget pada berkas **detail\_screen.dart**. Widget ini akan kita gunakan untuk menampilkan ikon favorit.

    ```
    class FavoriteButton extends StatefulWidget {
      @override
      _FavoriteButtonState createState() => _FavoriteButtonState();
    }
     
    class _FavoriteButtonState extends State<FavoriteButton> {
      @override
      Widget build(BuildContext context) {
        return IconButton(
          icon: Icon(Icons.favorite_border),
          onPressed: () {},
        );
      }
    }
    ```
16. Tambahkan variabel _boolean_ pada _class_ <mark style="color:yellow;">`_FavoriteButtonState`</mark>. Variabel ini merupakan sebuah _state_ yang dapat berubah dan widget kita akan tampil sesuai _state_-nya.

    ```
    bool isFavorite = false;
    ```

    _State_ isFavorite ini akan berubah ketika ikon favorit diklik. Sehingga tambahkan kode untuk mengubah variabel **isFavorite**. Pastikan Anda memanggil fungsi setState untuk mengubah _state_.

    ```
    onPressed: () {
      setState(() {
        isFavorite = !isFavorite;
      });
    },
    ```

    Ubah ikon yang ditampilkan sesuai dengan kondisi _state_. Pada kode di bawah ini kita menggunakan ekspresi _ternary_.

    ```
    icon: Icon(  isFavorite ? Icons.favorite : Icons.favorite_border,  color: Colors.red,),
    ```
17. Tambahkan _widget_ FavoriteButton ini sejajar dengan _icon_ navigasi _back_.

    ```
    SafeArea(
      child: Padding(
        padding: const EdgeInsets.all(8.0),
        child: Row(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          children: [
            CircleAvatar(
              backgroundColor: Colors.grey,
              child: IconButton(
                icon: Icon(
                  Icons.arrow_back,
                  color: Colors.white,
                ),
                onPressed: () {
                  Navigator.pop(context);
                },
              ),
            ),
            FavoriteButton(),
          ],
        ),
      ),
    ),
    ```

    Jalankan aplikasi dan lihat perubahannya. Ketika ikon favorit diklik dan fungsi <mark style="color:yellow;">setState()</mark> dipanggil, maka _method build_ akan kembali dijalankan dan _widget_ akan dibuat dan ditampilkan menurut _state_-nya.

Selamat! Anda telah menyelesaikan seluruh codelab dan projek Wisata Bandung. Seluruh kodenya adalah seperti berikut:

{% tabs %}
{% tab title="main_screen.dart" %}
```
import 'package:flutter/material.dart';
import 'package:wisatabandung/detail_screen.dart';
import 'package:wisatabandung/model/tourism_place.dart';
 
 
class MainScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Wisata Bandung'),
      ),
      body: ListView.builder(
        itemBuilder: (context, index) {
          final TourismPlace place = tourismPlaceList[index];
          return InkWell(
            onTap: () {
              Navigator.push(context, MaterialPageRoute(builder: (context) {
                return DetailScreen(place: place);
              }));
            },
            child: Card(
              child: Row(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: <Widget>[
                  Expanded(
                    flex: 1,
                    child: Image.asset(place.imageAsset),
                  ),
                  Expanded(
                    flex: 2,
                    child: Padding(
                      padding: const EdgeInsets.all(8.0),
                      child: Column(
                        crossAxisAlignment: CrossAxisAlignment.start,
                        children: <Widget>[
                          Text(
                            place.name,
                            style: TextStyle(fontSize: 16.0),
                          ),
                          SizedBox(
                            height: 10,
                          ),
                          Text(place.location),
                        ],
                      ),
                    ),
                  )
                ],
              ),
            ),
          );
        },
        itemCount: tourismPlaceList.length,
      ),
    );
  }
}
```
{% endtab %}

{% tab title="detail_screen.dart" %}
```
import 'package:flutter/material.dart';
import 'package:flutter/widgets.dart';
import 'package:wisatabandung/model/tourism_place.dart';
 
var informationTextStyle = TextStyle(fontFamily: 'Oxygen');
 
class DetailScreen extends StatelessWidget {
  final TourismPlace place;
 
  DetailScreen({required this.place});
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SingleChildScrollView(
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.stretch,
          children: <Widget>[
            Stack(
              children: <Widget>[
                Image.asset(place.imageAsset),
                SafeArea(
                  child: Padding(
                    padding: const EdgeInsets.all(8.0),
                    child: Row(
                      mainAxisAlignment: MainAxisAlignment.spaceBetween,
                      children: [
                        CircleAvatar(
                          backgroundColor: Colors.grey,
                          child: IconButton(
                            icon: Icon(
                              Icons.arrow_back,
                              color: Colors.white,
                            ),
                            onPressed: () {
                              Navigator.pop(context);
                            },
                          ),
                        ),
                        FavoriteButton(),
                      ],
                    ),
                  ),
                ),
              ],
            ),
            Container(
              margin: EdgeInsets.only(top: 16.0),
              child: Text(
                place.name,
                textAlign: TextAlign.center,
                style: TextStyle(
                  fontSize: 30.0,
                  fontFamily: 'Staatliches',
                ),
              ),
            ),
            Container(
              margin: EdgeInsets.symmetric(vertical: 16.0),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                children: <Widget>[
                  Column(
                    children: <Widget>[
                      Icon(Icons.calendar_today),
                      SizedBox(height: 8.0),
                      Text(
                        place.openDays,
                        style: informationTextStyle,
                      ),
                    ],
                  ),
                  Column(
                    children: <Widget>[
                      Icon(Icons.access_time),
                      SizedBox(height: 8.0),
                      Text(
                        place.openTime,
                        style: informationTextStyle,
                      ),
                    ],
                  ),
                  Column(
                    children: <Widget>[
                      Icon(Icons.monetization_on),
                      SizedBox(height: 8.0),
                      Text(
                        place.ticketPrice,
                        style: informationTextStyle,
                      ),
                    ],
                  ),
                ],
              ),
            ),
            Container(
              padding: EdgeInsets.all(16.0),
              child: Text(
                place.description,
                textAlign: TextAlign.center,
                style: TextStyle(
                  fontSize: 16.0,
                  fontFamily: 'Oxygen',
                ),
              ),
            ),
            Container(
              height: 150,
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
      ),
    );
  }
}
 
 
class FavoriteButton extends StatefulWidget {
  @override
  _FavoriteButtonState createState() => _FavoriteButtonState();
}
 
 
class _FavoriteButtonState extends State<FavoriteButton> {
  bool isFavorite = false;
 
 
  @override
  Widget build(BuildContext context) {
    return IconButton(
      icon: Icon(
        isFavorite ? Icons.favorite : Icons.favorite_border,
        color: Colors.red,
      ),
      onPressed: () {
        setState(() {
          isFavorite = !isFavorite;
        });
      },
    );
  }
}
```
{% endtab %}

{% tab title="tourism_place.dart" %}
```
class TourismPlace {
  String name;
  String location;
  String description;
  String openDays;
  String openTime;
  String ticketPrice;
  String imageAsset;
  List<String> imageUrls;
 
  TourismPlace({
    required this.name,
    required this.location,
    required this.description,
    required this.openDays,
    required this.openTime,
    required this.ticketPrice,
    required this.imageAsset,
    required this.imageUrls,
  });
}
 
var tourismPlaceList = [
  TourismPlace(
    name: 'Farm House Lembang',
    location: 'Lembang',
    description:
        'Berada di jalur utama Bandung-Lembang, Farm House menjadi objek wisata yang tidak pernah sepi pengunjung. Selain karena letaknya strategis, kawasan ini juga menghadirkan nuansa wisata khas Eropa. Semua itu diterapkan dalam bentuk spot swafoto Instagramable.',
    openDays: 'Open Everyday',
    openTime: '09:00 - 20:00',
    ticketPrice: 'Rp 25000',
    imageAsset: 'images/farm-house.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-s/0d/7c/59/70/farmhouse-lembang.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-w/13/f0/22/f6/photo3jpg.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-m/1280/16/a9/33/43/liburan-di-farmhouse.jpg'
    ],
  ),
  TourismPlace(
    name: 'Observatorium Bosscha',
    location: 'Lembang',
    description:
        'Memiliki beberapa teleskop, antara lain, Refraktor Ganda Zeiss, Schmidt Bimasakti, Refraktor Bamberg, Cassegrain GOTO, dan Teleskop Surya. Refraktor Ganda Zeiss adalah jenis teleskop terbesar untuk meneropong bintang. Benda ini diletakkan pada atap kubah sehingga saat teropong digunakan, atap tersebut harus dibuka. Observatorium Bosscha boleh dikunjungi oleh siapa pun, tanpa tiket. Namun, bagi yang ingin menggunakan teleskop Zeiss, wajib mendaftarkan diri. Untuk instansi atau lembaga pendidikan, diberikan jadwal hari Selasa sampai Jumat. Sementara itu, kunjungan individu dibuka setiap hari Sabtu.',
    openDays: 'Open Tuesday - Saturday',
    openTime: '09:00 - 14:30',
    ticketPrice: 'Rp 20000',
    imageAsset: 'images/bosscha.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/12/6b/63/0b/bosscha-observatory.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-p/0d/6a/88/9b/photo3jpg.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-o/11/3f/04/39/p-20171111-110220-largejpg.jpg',
    ],
  ),
  TourismPlace(
    name: 'Jalan Asia Afrika',
    location: 'Kota Bandung',
    description:
        'Jalan Asia Afrika di Bandung memiliki kaitan yang sangat erat dengan pendirian kota Kembang ini. Karena pada saat itu, Gubernur Jenderal Herman Willem Deaendels dari Belanda menancapkan tongkatnya saat memerintahkan pendirian kota ini, yang kemudian diabadikan menjadi tugu Bandung Nol Kilometer.',
    openDays: 'Open Everyday',
    openTime: '24 hours',
    ticketPrice: 'Free',
    imageAsset: 'images/jalan-asia-afrika.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/0d/c2/e7/e6/quotes-kota-bandung.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-w/17/f4/44/01/jalan-asia-afrika.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-s/0a/ef/36/e2/jalan-asia-afrika.jpg',
    ],
  ),
  TourismPlace(
    name: 'Stone Garden',
    location: 'Padalarang',
    description:
        'Stone Garden atau Taman Batu di Padalarang – Bandung ini adalah nama secara harafiah untuk apa yang akan kita lihat jika berada di sana. Hamparan batu yang artistik membuat kita merasa tidak sedang berada di Bandung, apalagi di Padalarang. Hamparan batu yang dimaksud bukan terhampar begitu saja di atas tanah luas yang menjadi permukaannya. Batu-batu besar yang ukuran pastinya bervariasi tersusun seperti memiliki suatu formasi matematis.',
    openDays: 'Open Everyday',
    openTime: '06:00 - 17:00',
    ticketPrice: 'Rp 3000',
    imageAsset: 'images/stone-garden.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/15/01/d7/4b/p-20180510-153310-01.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-w/15/68/00/32/stone-garden-citatah.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-o/0d/a2/cb/05/stone-garden-citatah.jpg',
    ],
  ),
  TourismPlace(
    name: 'Taman Film Pasopati',
    location: 'Kota Bandung',
    description:
        'Menjadi salah satu tempat wisata di Bandung yang favorit, tentu Taman Film ini memiliki fasilitas cukup memadai. Pemberian fasilitas ini memiliki harapan para pengunjung akan merasa nyaman dan tak segan2 untuk kembali berkunjung terus menerus kesini. Beberapa fasilitas taman yang bisa kamu nikmati diantaranya seperti layar videotron besar berukuran 4×8 untuk memutar berbagai macam pilihan film seperti Film Indonesia, Bollywood, Korea, ataupun Indie Bandung.',
    openDays: 'Open Everyday',
    openTime: '24 hours',
    ticketPrice: 'Free',
    imageAsset: 'images/taman-film.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/08/8b/87/50/bandung-movie-park.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-o/17/67/d5/53/img-20190505-114509-largejpg.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-w/09/73/33/05/taman-film-pasopati.jpg',
    ],
  ),
  TourismPlace(
    name: 'Museum Geologi',
    location: 'Kota Bandung',
    description:
        'Museum Geologi didirikan pada tanggal 16 Mei 1929. Museum ini telah direnovasi dengan dana bantuan dari JICA (Japan International Cooperation Agency). Setelah mengalami renovasi, Museum Geologi dibuka kembali dan diresmikan oleh Wakil Presiden RI, Megawati Soekarnoputri pada tanggal 23 Agustus 2000. Sebagai salah satu monumen bersejarah, museum berada di bawah perlindungan pemerintah dan merupakan peninggalan nasional. Dalam Museum ini, tersimpan dan dikelola materi-materi geologi yang berlimpah, seperti fosil, batuan, mineral. Kesemuanya itu dikumpulkan selama kerja lapangan di Indonesia sejak 1850.',
    openDays: 'Open Saturday - Thursday',
    openTime: '09:00 - 15:30',
    ticketPrice: 'Rp 3000',
    imageAsset: 'images/museum-geologi.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-w/19/1c/8e/f7/geology-museum.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-o/11/a7/35/b7/geology-museum.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-s/1a/55/e0/dc/geology-museum.jpg',
    ],
  ),
  TourismPlace(
    name: 'Floating Market',
    location: 'Lembang',
    description:
        'Tempat wisata ini sepertinya memang ditujukan untuk wisata keluarga di Bandung. Di sini kita bisa menikmati suasana kawasan yang tertata rapi dan alami. Pada awalnya, floating market Lembang tidak begitu luas. Tapi sekarang sudah ekspansi dan memiliki banyak objek menarik baru. Nama floating market ini sepertinya merujuk pada stand tempat jualan makanan yang berada dalam perahu.',
    openDays: 'Open Everyday',
    openTime: '09:00 - 17:00',
    ticketPrice: 'Rp 20000',
    imageAsset: 'images/floating-market.png',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/17/f9/ff/f8/floating-market-bandung.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-p/1a/86/d3/cd/20200103-125059-largejpg.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-p/19/ce/b4/9b/img20181224120857-largejpg.jpg',
    ],
  ),
  TourismPlace(
    name: 'Kawah Putih',
    location: 'Ciwidey',
    description:
        'Kawah Putih adalah tempat wisata di Bandung yang paling terkenal. Berlokasi di Ciwidey, Jawa Barat, kurang lebih sekitar 50 KM arah selatan kota Bandung, Kawah Putih adalah sebuah danau yang terbentuk akibat dari letusan Gunung Patuha. Sesuai dengan namanya, tanah yang ada di kawasan ini berwarna putih akibat dari pencampuran unsur belerang.',
    openDays: 'Open Everyday',
    openTime: '07:00 - 17:00',
    ticketPrice: 'Rp 15000',
    imageAsset: 'images/kawah-putih.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/0b/6e/7c/ce/rocks-sticking-out-of.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-p/0b/35/30/14/white-crater.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-o/0a/8b/9a/79/2945-t00572-www-initempatwisat.jpg',
    ],
  ),
  TourismPlace(
    name: 'Ranca Upas',
    location: 'Ciwidey',
    description:
        'Ranca Upas Ciwidey adalah kawasan bumi perkemahan di bawah pengelolaan perhutani. Tempat ini berada di kawasan wisata Bandung Selatan, satu lokasi dengan kawah putih, kolam Cimanggu dan situ Patenggang. Banyak hal yang bisa dilakukan di kawasan wisata ini, seperti berkemah, berinteraksi dengan rusa, sampai bermain di water park dan mandi air panas.',
    openDays: 'Open Everyday',
    openTime: '24 hours',
    ticketPrice: 'Rp 20000',
    imageAsset: 'images/ranca-upas.jpg',
    imageUrls: [
      'https://media-cdn.tripadvisor.com/media/photo-o/1a/e0/7f/9c/kampung-cai-ranca-upas.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-w/13/ee/2f/87/ranca-upas.jpg',
      'https://media-cdn.tripadvisor.com/media/photo-w/13/ee/27/0a/ranca-upas.jpg',
    ],
  ),
];
```
{% endtab %}
{% endtabs %}

Anda dapat mengunduh seluruh kodenya pada tautan berikut: [https://github.com/dicodingacademy/a159-flutter-pemula-labs/tree/codelab3-final](https://github.com/dicodingacademy/a159-flutter-pemula-labs/tree/codelab3-final)

**Tambahan**: Flutter dikenal dengan _framework_-nya yang sangat mudah dalam menghadirkan tampilan yang menarik termasuk menambahkan animasi. Salah satu yang paling mudah adalah _Hero Animation_. Sebagai tantangan, bisakah Anda menambahkan _Hero Animation_ pada aplikasi Anda? Dicoding sudah pernah mengulasnya dalam blog berikut: [https://www.dicoding.com/blog/menerapkan-animasi-pada-project-flutter/](https://www.dicoding.com/blog/menerapkan-animasi-pada-project-flutter/)
