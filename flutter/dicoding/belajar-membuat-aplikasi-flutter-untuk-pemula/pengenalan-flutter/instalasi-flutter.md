# 📖 Instalasi Flutter

### Instalasi Flutter

Sebelum mulai mengembangkan aplikasi menggunakan Flutter, tentunya kita perlu menyiapkan dan menginstal _tools_ apa saja yang dibutuhkan untuk membuat aplikasi Flutter. Untuk melakukan instalasi Flutter, ada perbedaan cara di setiap sistem operasi. Simak caranya berikut ini sesuai dengan sistem operasi yang Anda gunakan:

### Persyaratan Minimum

Sebelum melakukan instalasi dan menjalankan Flutter, perangkat milik Anda harus memenuhi persyaratan minimum seperti di bawah ini:

{% tabs %}
{% tab title="Windows" %}
[![2020061515204436f70d01b7c87b0441de2a2894baddd5.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061515204436f70d01b7c87b0441de2a2894baddd5.png)](https://www.dicoding.com/academies/159/tutorials/6446#)

* Sistem Operasi : Windows 7 SP1 atau lebih baru (64-bit).
* Ruang Penyimpanan : 1.64 GB dan tidak termasuk IDE dan tools lainnya.
* Flutter bergantung pada tools yang ada di dalam environment:
  * Windows Powershell 5.0 atau versi terbaru (sudah terdapat pada paket instalasi Windows 10), dapat Anda unduh pada link berikut ini [https://docs.microsoft.com/en-us/powershell/scripting/install/installing-windows-powershell](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-windows-powershell).
  * Git for Windows 2.x, dengan opsi "Use Git from the Windows Command Prompt", dapat Anda unduh pada link berikut ini [https://git-scm.com/download/win](https://git-scm.com/download/win).

Jika Git untuk Windows sudah diinstal, pastikan Anda dapat menjalankan perintah git dari Command Prompt (CMD) atau PowerShell.
{% endtab %}

{% tab title="MacOS" %}


[![20200615151548e4513d939e14839fd0cc4e8ae92f3ded.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200615151548e4513d939e14839fd0cc4e8ae92f3ded.png)](https://www.dicoding.com/academies/159/tutorials/6446#)

* Sistem Operasi : Mac OS 64-bit.
* Ruang penyimpanan : 2.8 GB dan tidak termasuk IDE dan tools lainnya.
* Flutter tergantung pada command-line tools ini yang tersedia di environment:
  * bash
  * curl
  * git 2.x
  * Mkdir&#x20;
  * rm
  * unzip
  * which
{% endtab %}

{% tab title="Linux" %}


[![202006151516005b66ff3befe3600cf3f5d31a7846f6fb.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006151516005b66ff3befe3600cf3f5d31a7846f6fb.png)](https://www.dicoding.com/academies/159/tutorials/6446#)

* Sistem Operasi : Linux 64-bit.
* Ruang penyimpanan : 1.8 GB dan tidak termasuk IDE dan tools lainnya.
* Flutter tergantung pada command-line tools ini yang tersedia di environment:
  * bash
  * curl
  * git 2.x
  * mkdir
  * rm
  * unzip
  * which
  * xz-utils
* Shared Libraries : Perintah test pada Flutter tergantung pada library yang tersedia di environment.
  * libGLU.so.1 - disediakan oleh mesa packages seperti, libglu1-mesa di Ubuntu/Debian.
{% endtab %}
{% endtabs %}

### Flutter SDK

Setelah persyaratan minimum terpenuhi, Anda dapat mulai melakukan instalasi Flutter SDK. Cara untuk mendapatkan Flutter SDK sebagai berikut:

{% tabs %}
{% tab title="Windows" %}


1. Unduh paket instalasi untuk mendapatkan versi stabil terbaru dari Flutter SDK di alamat web [https://flutter.dev/docs/development/tools/sdk/releases](https://flutter.dev/docs/development/tools/sdk/releases). Ambil versi terbaru pada stable channel sesuai sistem operasi yang digunakan.
2. Ekstrak berkas zip dan tempatkan folder flutter pada lokasi instalasi yang diinginkan untuk Flutter SDK. Misalnya C:\Development, jangan pasang Flutter di direktori seperti C:\Program Files atau yang membutuhkan hak istimewa seperti administrator.
3.  Temukan berkas flutter\_console.bat di dalam direktori flutter tersebut. Mulai dengan klik dua kali atau jalankan script tersebut dan Anda sekarang siap untuk menjalankan perintah Flutter di Flutter Console.

    ![](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006101131070f740c0b99f5711865b603c906e79bc8.jpeg)
4. Tampilan dari flutter\_console.bat seperti di bawah ini:\
   [![2020061011314434d70709c2e6fee6cd9e72ec51c11122.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061011314434d70709c2e6fee6cd9e72ec51c11122.jpeg)](https://www.dicoding.com/academies/159/tutorials/6446#)
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

### Update Path

Langkah selanjutnya kita akan melakukan _update path_ supaya perintah Flutter bisa digunakan pada command prompt/terminal. Berikut langkah-langkahnya:

{% tabs %}
{% tab title="Windows" %}


1. Dari bar pencarian di Start menu, ketik ‘env’ dan pilih Edit Environment Variable untuk akun Anda.\
   [![202006101206155a71e83adcf8b6f6215bc177e388f952.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006101206155a71e83adcf8b6f6215bc177e388f952.jpeg)](https://www.dicoding.com/academies/159/tutorials/6446#)
2. Klik pada tombol Environment Variables.\
   [![2020061012061449b8a5029acec12bf39f297aa8498824.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2020061012061449b8a5029acec12bf39f297aa8498824.jpeg)](https://www.dicoding.com/academies/159/tutorials/6446#)
3. Di bawah User variabel periksa apakah ada entri yang disebut PATH, jika ada maka pilih lalu edit, jika tidak ada maka buat baru dengan nama variabel Path.\
   [![202006101206156459086dbe93f73f44ac9c36920d2372.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006101206156459086dbe93f73f44ac9c36920d2372.jpeg)](https://www.dicoding.com/academies/159/tutorials/6446#)
4. Edit atau tambahkan value-nya dengan direktori Flutter SDK.
   * Jika terdapat entri, tambahkan path lengkap ke flutter\bin menggunakan tanda titik koma (;) sebagai pemisah dari nilai yang ada (jika menggunakan mode edit satu baris).
   * Jika entri tidak ditemukan, buat user variabel baru dan beri nama Path dan beri nilai flutter\bin sebagai nilainya.\
     [![202006101207271e7bef6fb113a55b53786d237bcc8035.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202006101207271e7bef6fb113a55b53786d237bcc8035.jpeg)](https://www.dicoding.com/academies/159/tutorials/6446#)[![20200610120737ae597d11817c59bc0d02693ac04b96e7.jpeg](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20200610120737ae597d11817c59bc0d02693ac04b96e7.jpeg)](https://www.dicoding.com/academies/159/tutorials/6446#)&#x20;

Perhatikan bahwa Anda harus menutup dan membuka kembali semua jendela konsol yang ada agar perubahan dapat terlihat.
{% endtab %}

{% tab title="MacOS" %}


Anda dapat memperbarui variabel PATH, hanya untuk sesi _command-line_ saat ini (sementara). Anda mungkin ingin memperbarui variabel secara permanen, sehingga dapat menjalankan perintah flutter di sesi terminal apa pun.

Langkah-langkah untuk memodifikasi variabel PATH secara permanen untuk semua sesi terminal akan tergantung perangkat yang digunakan. Umumnya, Anda dapat menambahkan variabel PATH seperti ini:

1. Tentukan direktori tempat Anda meletakkan Flutter SDK. Anda akan membutuhkannya di tahap ke-3 contoh ini.
2. Buka (atau buat) **$HOME/.bash\_profile**. Direktori dan nama file mungkin berbeda pada perangkat Anda (bisa .profile, .bash\_profile, .zshrc, .bashrc, atau yang lainnya).
3.  Tambahkan baris berikut dan ubah \[FLUTTER\_DIRECTORY] menjadi direktori dimana Anda menaruh Flutter SDK:

    ```
    export PATH="$PATH:[FLUTTER_DIRECTORY]/flutter/bin"
    ```
4. Jalankan source $HOME/.bash\_profile untuk memuat ulang terminal saat ini.
5.  Pastikan direktori flutter/bin sekarang ada di PATH Anda dengan cara menjalankan perintah:

    ```
    echo $PATH
    ```
{% endtab %}

{% tab title="Linux" %}


Anda dapat memperbarui variabel PATH, hanya untuk sesi _command-line_ saat ini (sementara). Anda mungkin ingin memperbarui variabel secara permanen, sehingga dapat menjalankan perintah flutter di sesi terminal apa pun.

Langkah-langkah untuk memodifikasi variabel PATH secara permanen untuk semua sesi terminal akan tergantung perangkat yang digunakan. Umumnya, Anda dapat menambahkan variabel PATH seperti ini:

1. Tentukan direktori tempat Anda meletakkan Flutter SDK. Anda akan membutuhkannya di tahap ke-3 contoh ini.
2. Buka (atau buat) **$HOME/.bash\_profile**. Direktori dan nama file mungkin berbeda pada perangkat Anda (bisa .profile, .bash\_profile, .zshrc, .bashrc, atau yang lainnya).
3.  Tambahkan baris berikut dan ubah \[FLUTTER\_DIRECTORY] menjadi direktori dimana Anda menaruh Flutter SDK pada bagian sebelumnya:

    ```
    export PATH="$PATH:[FLUTTER_DIRECTORY]/flutter/bin"
    ```
4. Jalankan source $HOME/.bash\_profile untuk memuat ulang jendela saat ini.
5.  Pastikan direktori flutter/bin sekarang ada di PATH Anda dengan cara menjalankan perintah:

    ```
    echo $PATH
    ```
{% endtab %}
{% endtabs %}

### Flutter Doctor

Flutter doctor adalah perintah untuk mengecek kelengkapan framework flutter yang Anda gunakan, seperti versi flutter yang digunakan, Android SDK yang digunakan, iOS SDK yang digunakan (hanya pada MacOS), perangkat yang sudah terhubung, dan semacamnya.  Periksa kembali dan pastikan dependensi untuk pengaturan sudah lengkap. Jalankan perintah berikut untuk membuka flutter doctor:

```
flutter doctor
```

Perintah ini memeriksa environment Anda dan menampilkan laporan ke jendela terminal. Pada Flutter SDK sudah terdapat Dart SDK, jadi Anda tidak perlu menginstal Dart secara terpisah. Periksa output dengan cermat untuk perangkat lunak lain yang mungkin perlu Anda instal atau melakukan sesuatu lebih lanjut (ditunjukkan dalam teks tebal).

Contoh :

| <p>[-] Android toolchain - develop for Android devices</p><p>• Android SDK at D:\Android\sdk</p><p>**✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ**</p><p>• Try re-installing or updating your Android SDK,</p><p>    visit https://flutter.io/setup/#android-setup for detailed instructions.</p> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Bagian tersebut menjelaskan cara menyelesaikan proses instalasi Flutter SDK. Setelah memasang dependensi yang hilang, jalankan perintah flutter doctor lagi untuk memverifikasi bahwa Anda telah mengatur semuanya dengan benar.
