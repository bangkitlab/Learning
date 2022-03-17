# 📖 Pengenalan Container

Bagaimana sejauh ini? Semoga materinya dapat Anda praktikkan dengan mulus ya.

Pada bagian sebelumnya kita mempelajari widget Scaffold. Kini saatnya belajar tentang widget Container. Container adalah widget yang digunakan untuk melakukan _styling_, membuat sebuah _shape_ (bentuk), dan _layout_ pada widget _child_-nya. Sebagai contoh:

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40)),
  color: Colors.blue,
)
```

Pada kode di atas kita membuat sebuah Text "Hi" yang dibungkus oleh widget Container dan kita beri parameter <mark style="color:yellow;">`color`</mark> dengan nilai `C`<mark style="color:yellow;">`olors.blue`</mark>. Kita letakkan Container di dalam parameter body. Apa hasilnya? Text "Hi" akan memiliki background berwarna biru. Jalankan project Anda untuk menampilkan hasil seperti berikut:\
[![202006151925510970dfdff0d8d3707d2e2398375e1a60.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151925510970dfdff0d8d3707d2e2398375e1a60.jpeg)](https://www.dicoding.com/academies/159/tutorials/6485#)

### Width & Height

Kita dapat mengatur lebar (_width_) dan tinggi (_height_) suatu Container seperti berikut:

```
Container(
  child: Text('Hi', style: TextStyle(fontSize: 40),),
  color: Colors.blue,
  width: 200,
  height: 100,
)
```

Kode di atas ketika dijalankan hasilnya akan seperti berikut:\
[![202006151926106c3cd59344ca17857072130d6352701a.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151926106c3cd59344ca17857072130d6352701a.jpeg)](https://www.dicoding.com/academies/159/tutorials/6485#)

### Padding & Margin

Container menyediakan padding & margin. Padding merupakan jarak antara konten (_child_) dengan Container, sedangkan margin merupakan jarak antara Container dengan bagian luar container.

Penggunaan padding adalah seperti berikut:

```
Container(
 child: Text('Hi', style: TextStyle(fontSize: 40),),
 color: Colors.blue,
 padding: EdgeInsets.all(10),
)
```

Pada kode di atas kita menambahkan padding pada semua sisi container secara merata dengan nilai 10. Maka jika me-_refresh_ aplikasi flutter, akan ada jarak antara Text "Hi" dengan batas (_border_) dari container.\
[![2020061519270856b04fa599ff5df0262b764052542ac8.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061519270856b04fa599ff5df0262b764052542ac8.jpeg)](https://www.dicoding.com/academies/159/tutorials/6485#)

Lalu penggunaan margin pun sama seperti halnya padding, maka contoh kodenya seperti berikut:

```
Container(
 child: Text('Hi', style: TextStyle(fontSize: 40),),
 color: Colors.blue, 
 margin: EdgeInsets.all(10), 
)
```

Maka hasil dari kode di atas Container akan bergeser lebih ke dalam karena ada jarak antara Container dengan bagian luar Container.

[![20200615113243b2f8da0cf1d7be70d09c0e922fde6ee9.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615113243b2f8da0cf1d7be70d09c0e922fde6ee9.jpeg)](https://www.dicoding.com/academies/159/tutorials/6485#)
