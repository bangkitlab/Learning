# 📖 Web Deployment

Pada materi ini kita akan mempelajari bagaimana melakukan build aplikasi flutter untuk platform web. Sama seperti platform android dan ios, informasi untuk pengaturan aplikasi berada pada folder web.

### Setting Nama Aplikasi

Untuk mengatur nama aplikasi, kita bisa membuka berkas **manifest.json**. Konfigurasi untuk nama aplikasi dapat Anda temukan dan ubah pada key name dan short\_name.

```
{
    "name": "wisata_bandung",
    "short_name": "wisata_bandung"
}
```

### Setting Icon Aplikasi

Platform web juga membutuhkan icon dalam berbagai ukuran. Icon untuk web dapat Anda taruh pada folder **/web/icons**. Kemudian, Anda perlu mendaftarkannya pada berkas **manifest.json**.

```
{
    ...
    "icons": [
        {
            "src": "icons/Icon-192.png",
            "sizes": "192x192",
            "type": "image/png"
        },
        {
            "src": "icons/Icon-512.png",
            "sizes": "512x512",
            "type": "image/png"
        }
    ]
}
```

### Melakukan build web

Sama seperti build aplikasi android dan ios, untuk mem-_build_ aplikasi Flutter web kita menjalankan perintah flutter web. Perintah selengkapnya adalah seperti ini:

```
flutter build web
```

Sama seperti ketika menjalankan flutter web, ketika melakukan _build_, kita juga bisa menentukan _renderer_ yang ingin digunakan. Untuk menentukan _renderer_ yang digunakan, tambahkan parameter --web-renderer pada perintah flutter build. Jika tidak mendefinisikan parameter --web-renderer maka mode auto yang akan digunakan.

Hasil build akan Anda temukan pada folder **/build/web**. Folder inilah yang nantinya bisa Anda _deploy_ ke sebuah _web hosting_ atau _web server_.

Beberapa opsi hosting yang bisa Anda gunakan, antara lain:

* [Firebase Hosting](https://firebase.google.com/docs/hosting)
* [GitHub Pages](https://pages.github.com)
* [Google Cloud Hosting](https://cloud.google.com/solutions/smb/web-hosting/)
