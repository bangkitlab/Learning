# 📖 ListView

Pada Codelab kedua kita telah menggunakan dan menyinggung sedikit tentang widget **ListView**. Widget ini digunakan untuk menampilkan beberapa item dalam bentuk baris atau kolom dan bisa di-_scroll_.

Cara penggunaan _ListView_ ini mirip dengan **Column** atau **Row** di mana Anda memasukkan widget yang ingin disusun sebagai **children** dari **ListView**.

```
class ScrollingScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView(
        children: <Widget>[
          Container(
            height: 250,
            decoration: BoxDecoration(
              color: Colors.grey,
              border: Border.all(color: Colors.black),
            ),
            child: Center(
              child: Text(
                '1',
                style: TextStyle(fontSize: 50),
              ),
            ),
          ),
          Container(
            height: 250,
            decoration: BoxDecoration(
              color: Colors.grey,
              border: Border.all(color: Colors.black),
            ),
            child: Center(
              child: Text(
                '2',
                style: TextStyle(fontSize: 50),
              ),
            ),
          ),
          Container(
            height: 250,
            decoration: BoxDecoration(
              color: Colors.grey,
              border: Border.all(color: Colors.black),
            ),
            child: Center(
              child: Text(
                '3',
                style: TextStyle(fontSize: 50),
              ),
            ),
          ),
          Container(
            height: 250,
            decoration: BoxDecoration(
              color: Colors.grey,
              border: Border.all(color: Colors.black),
            ),
            child: Center(
              child: Text(
                '4',
                style: TextStyle(fontSize: 50),
              ),
            ),
          ),
        ],
      ),
    );
  }
}
```

Ketika dijalankan, aplikasi akan menjadi seperti berikut:

[![20210425152905aa85dcf49bf24cb127274cbc16ea35cd.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425152905aa85dcf49bf24cb127274cbc16ea35cd.gif)](https://www.dicoding.com/academies/159/tutorials/8616?from=6534#)

### Menampilkan Item Secara Dinamis

Selain memasukkan widget satu per satu ke dalam **children** dari **ListView**, Anda juga dapat menampilkan _list_ secara dinamis. Ini sangat berguna ketika Anda memiliki banyak item dengan jumlah yang tidak menentu.

Misalnya kita ingin menampilkan daftar angka dari 1 sampai 10.

```
List<int> numberList = <int>[1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```

Caranya, masukkan variabel atau _list_ Anda sebagai _children_ lalu panggil fungsi <mark style="color:yellow;">`map()`</mark>. Fungsi map ini berguna untuk memetakan atau mengubah setiap item di dalam list menjadi objek yang kita inginkan. Fungsi map ini membutuhkan satu buah parameter berupa fungsi atau lambda.

```
class ScrollingScreen extends StatelessWidget {
  final List<int> numberList = <int>[1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView(
        children: numberList.map((number) {});
      ),
    );
  }
}
```

Karena parameter children ini membutuhkan nilai berupa _list_ widget, maka kita perlu mengembalikan setiap item dari **numberList** menjadi **widget** yang akan ditampilkan. Ubah fungsi **lambda** Anda menjadi seperti berikut:

```
class ScrollingScreen extends StatelessWidget {
  final List<int> numberList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView(
        children: numberList.map((number) {
          return Container(
            height: 250,
            decoration: BoxDecoration(
              color: Colors.grey,
              border: Border.all(color: Colors.black),
            ),
            child: Center(
              child: Text(
                '$number', // Ditampilkan sesuai item
                style: TextStyle(fontSize: 50),
              ),
            ),
          );
        }).toList(),
      ),
    );
  }
}
```

Perhatikan di akhir kita perlu mengembalikan fungsi map menjadi objek _List_ lagi dengan fungsi <mark style="color:yellow;">`.toList()`</mark>. Lakukan **hot reload** pada aplikasi Anda untuk melihat hasil perubahan.

### Menggunakan ListView.builder

Selain mengisi parameter children dari ListView seperti sebelumnya, kita juga bisa memanfaatkan method ListView.builder. ListView.builder lebih cocok digunakan pada ListView dengan jumlah item yang cukup besar. Ini karena Flutter hanya akan merender tampilan item yang terlihat di layar dan tidak me-_render_ seluruh item ListView di awal.

ListView.builder memerlukan dua parameter yaitu itemBuilder dan itemCount. Parameter itemBuilder merupakan fungsi yang mengembalikan widget untuk ditampilkan. Sedangkan itemCount kita isi dengan jumlah seluruh item yang ingin ditampilkan.

Berikut ini adalah contoh kode penggunaan ListView.builder:

```
ListView.builder(
  itemBuilder: (BuildContext context, int index) {
    return Container(
      height: 250,
      decoration: BoxDecoration(
        color: Colors.grey,
        border: Border.all(color: Colors.black),
      ),
      child: Center(
        child: Text(
          '${numberList[index]}',
          style: TextStyle(fontSize: 50),
        ),
      ),
    );
  },
  itemCount: numberList.length,
),
```

### ListView.separated

Cara lain untuk membuat ListView adalah dengan metode ListView.separated. ListView jenis ini akan menampilkan daftar item yang dipisahkan dengan separator. Penggunaan ListView.separated mirip dengan builder, yang membedakan adalah terdapat satu parameter tambahan wajib yaitu separatorBuilder yang mengembalikan Widget yang akan berperan sebagai separator.

Berikut ini adalah contoh kode dari ListView.separated:

```
ListView.separated(
  itemBuilder: (BuildContext context, int index) {
    return Container(
      height: 250,
      decoration: BoxDecoration(
        color: Colors.grey,
        border: Border.all(color: Colors.black),
      ),
      child: Center(
        child: Text(
          '${numberList[index]}',
          style: TextStyle(fontSize: 50),
        ),
      ),
    );
  },
  separatorBuilder: (BuildContext context, int index) {
    return Divider();
  },
  itemCount: numberList.length,
),
```

Jika kode di atas dijalankan, maka tampilan aplikasi adalah seperti ini:

[![2021042515323830411639143a12b084aa247549f4ecb9.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042515323830411639143a12b084aa247549f4ecb9.gif)](https://www.dicoding.com/academies/159/tutorials/8616?from=6534#)

\


Untuk mempelajari fitur ListView selengkapnya dapat Anda baca pada tautan dokumentasi [ListView Class](https://api.flutter.dev/flutter/widgets/ListView-class.html).
