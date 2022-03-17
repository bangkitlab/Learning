# 📖 Input Widget

Salah satu bentuk interaksi dengan pengguna adalah dengan menerima input. Ada beberapa input widget yang bisa digunakan supaya pengguna bisa berinteraksi dengan aplikasi. Perhatikan bahwa input pengguna ini berkaitan dengan state yang dapat sering berubah. Karena itu umumnya input widget akan ditempatkan di dalam StatefulWidget.

### TextField

TextField merupakan sebuah widget yang digunakan untuk menerima input berupa teks yang berasal dari _keyboard_. Terdapat beberapa cara yang bisa Anda gunakan untuk mendapatkan nilai dari TextField. Salah satunya adalah melalui parameter onChanged.

```
String _name = '';
 
TextField(
  onChanged: (String value) {
    setState(() {
      _name = value;
    });
  },
)
```

Parameter _onChanged_ berisi sebuah fungsi yang akan dipanggil setiap terjadi perubahan inputan pada TextField. Pada fungsi ini, kita dapat mengubah nilai variabel state dengan memanggil fungsi setState().

Jika Anda tidak ingin mengambil nilai setiap perubahan, tetapi hanya ketika seluruh input sudah selesai di-_submit_, Anda dapat menggunakan parameter <mark style="color:yellow;">`onSubmitted`</mark> seperti berikut:

```
String _name = '';
 
TextField(
  onSubmitted: (String value) {
    setState(() {
      _name = value;
    });
  },
)
```

Cara lain yang bisa kita gunakan adalah dengan <mark style="color:yellow;">`TextEditingController`</mark>. Dengan controller, kita cukup membuat variabel TextEditingController lalu menambahkannya ke widget TextField.

```
TextEditingController _controller = TextEditingController();
 
TextField(
  controller: _controller,
),
```

Ketika menggunakan controller, pastikan untuk menghapus controller ketika halaman atau widget sudah tidak digunakan. Ini bertujuan supaya tidak menimbulkan kebocoran memori (_memory leak_).

```
@override
void dispose() {
  _controller.dispose();
  super.dispose();
}
```

Berikut ini adalah contoh penerapan widget TextField:

[![20210425140302c2dc9c745ca80003e131220c8cef3fa3.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425140302c2dc9c745ca80003e131220c8cef3fa3.gif)](https://www.dicoding.com/academies/159/tutorials/8606?from=6504#)

Untuk membuat TextField seperti di atas, Anda bisa menggunakan kode seperti berikut:

{% tabs %}
{% tab title="onChanged" %}


1. class \_FirstScreenState extends State\<FirstScreen> {
2. &#x20; String \_name = '';
3. &#x20;
4. &#x20; @override
5. &#x20; Widget build(BuildContext context) {
6. &#x20;   return Scaffold(
7. &#x20;     appBar: AppBar(
8. &#x20;       title: Text('First Screen'),
9. &#x20;     ),
10. &#x20;     body: Padding(
11. &#x20;       padding: const EdgeInsets.all(16.0),
12. &#x20;       child: Column(
13. &#x20;         children: \[
14. &#x20;           TextField(
15. &#x20;             decoration: InputDecoration(
16. &#x20;               hintText: 'Write your name here...',
17. &#x20;               labelText: 'Your Name',
18. &#x20;             ),
19. &#x20;             onChanged: (String value) {
20. &#x20;               setState(() {
21. &#x20;                 \_name = value;
22. &#x20;               });
23. &#x20;             },
24. &#x20;           ),
25. &#x20;           SizedBox(height: 20),
26. &#x20;           ElevatedButton(
27. &#x20;             onPressed: () {
28. &#x20;               showDialog(
29. &#x20;                   context: context,
30. &#x20;                   builder: (context) {
31. &#x20;                     return AlertDialog(
32. &#x20;                       content: Text('Hello, $\_name'),
33. &#x20;                     );
34. &#x20;                   });
35. &#x20;             },
36. &#x20;             child: Text('Submit'),
37. &#x20;           )
38. &#x20;         ],
39. &#x20;       ),
40. &#x20;     ),
41. &#x20;   );
42. &#x20; }
43. }
{% endtab %}

{% tab title="controller" %}


1. class \_FirstScreenState extends State\<FirstScreen> {
2. &#x20; TextEditingController \_controller = TextEditingController();
3. &#x20;
4. &#x20; @override
5. &#x20; Widget build(BuildContext context) {
6. &#x20;   return Scaffold(
7. &#x20;     appBar: AppBar(
8. &#x20;       title: Text('First Screen'),
9. &#x20;     ),
10. &#x20;     body: Padding(
11. &#x20;       padding: const EdgeInsets.all(16.0),
12. &#x20;       child: Column(
13. &#x20;         children: \[
14. &#x20;           TextField(
15. &#x20;             controller: \_controller,
16. &#x20;             decoration: InputDecoration(
17. &#x20;               hintText: 'Write your name here...',
18. &#x20;               labelText: 'Your Name',
19. &#x20;             ),
20. &#x20;           ),
21. &#x20;           SizedBox(height: 20),
22. &#x20;           ElevatedButton(
23. &#x20;             onPressed: () {
24. &#x20;               showDialog(
25. &#x20;                   context: context,
26. &#x20;                   builder: (context) {
27. &#x20;                     return AlertDialog(
28. &#x20;                       content: Text('Hello, ${\_controller.text}'),
29. &#x20;                     );
30. &#x20;                   });
31. &#x20;             },
32. &#x20;             child: Text('Submit'),
33. &#x20;           )
34. &#x20;         ],
35. &#x20;       ),
36. &#x20;     ),
37. &#x20;   );
38. &#x20; }
39. &#x20;
40. &#x20; @override
41. &#x20; void dispose() {
42. &#x20;   \_controller.dispose();
43. &#x20;   super.dispose();
44. &#x20; }
45. }
{% endtab %}
{% endtabs %}

### Switch

Switch merupakan inputan yang mengembalikan nilai boolean true atau false. Perhatikan contoh berikut:

```
class _FirstScreenState extends State<FirstScreen> {
  bool lightOn = false;
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Switch(
        value: lightOn,
        onChanged: (bool value) {
          setState(() {
            lightOn = value;
          });
 
          ScaffoldMessenger.of(context).showSnackBar(
            SnackBar(
              content: Text(lightOn ? 'Light On' : 'Light Off'),
              duration: Duration(seconds: 1),
            ),
          );
        },
      ),
    );
  }
}
```

Pada contoh tersebut value dari Switch berupa boolean di mana ketika boolean tersebut false maka Switch akan berada pada posisi nonaktif. Switch umumnya digunakan sebagai konfigurasi on/off pada halaman setting.

[![2021042514091145028d504a528995ac261f5f22ad9460.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042514091145028d504a528995ac261f5f22ad9460.gif)](https://www.dicoding.com/academies/159/tutorials/8606?from=6504#)

#### Radio

Radio merupakan inputan yang digunakan untuk memilih salah satu dari beberapa pilihan dalam suatu kelompok. Berikut contohnya:

```
class _FirstScreenState extends State<FirstScreen> {
  String language;
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Column(
        mainAxisSize: MainAxisSize.min,
        children: <Widget>[
          ListTile(
            leading: Radio<String>(
              value: 'Dart',
              groupValue: language,
              onChanged: (String value) {
                setState(() {
                  language = value;
                  showSnackbar();
                });
              },
            ),
            title: Text('Dart'),
          ),
          ListTile(
            leading: Radio<String>(
              value: 'Kotlin',
              groupValue: language,
              onChanged: (String value) {
                setState(() {
                  language = value;
                  showSnackbar();
                });
              },
            ),
            title: Text('Kotlin'),
          ),
          ListTile(
            leading: Radio<String>(
              value: 'Swift',
              groupValue: language,
              onChanged: (String value) {
                setState(() {
                  language = value;
                  showSnackbar();
                });
              },
            ),
            title: Text('Swift'),
          ),
        ],
      ),
    );
  }
 
  void showSnackbar() {
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        content: Text('$language selected'),
        duration: Duration(seconds: 1),
      ),
    );
  }
}
```

Pada contoh tersebut terdapat variable <mark style="color:yellow;">`language`</mark> yang digunakan pada <mark style="color:yellow;">`groupValue`</mark> tiap Radio. Language inilah yang menyimpan nilai Radio yang dipilih. Nilainya akan berubah ketika fungsi <mark style="color:yellow;">`onChanged`</mark> terpanggil.

[![2021042514122809a3cc862b236b861e8d6b2572e0963d.gif](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2021042514122809a3cc862b236b861e8d6b2572e0963d.gif)](https://www.dicoding.com/academies/159/tutorials/8606?from=6504#)

### Checkbox

Checkbox merupakan inputan benar atau salah. Checkbox akan berisi centang jika nilainya adalah benar dan kosong jika salah. Seperti pada contoh berikut:

```
class _FirstScreenState extends State<FirstScreen> {
  bool agree = false;
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: ListTile(
        leading: Checkbox(
          value: agree,
          onChanged: (bool value) {
            setState(() {
              agree = value;
            });
          },
        ),
        title: Text('Agree / Disagree'),
      ),
    );
  }
}
```

Kode di atas jika dijalankan akan tampil seperti berikut:

[![20210425141306d2c24a9c0f4f1f6cda3ebd8f7fd9b871.png](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20210425141306d2c24a9c0f4f1f6cda3ebd8f7fd9b871.png)](https://www.dicoding.com/academies/159/tutorials/8606?from=6504#)

Ada beberapa tautan yang dapat Anda baca untuk memahami tentang widget-widget input yang ada pada Flutter, antara lain:

* [Input and selections widgets](https://flutter.dev/docs/development/ui/widgets/material#Input%20and%20selections)
* [TextField Class](https://api.flutter.dev/flutter/material/TextField-class.html)
* [Switch Class](https://api.flutter.dev/flutter/material/Switch-class.html)
* [Radio Class](https://api.flutter.dev/flutter/material/Radio-class.html)
* [Checkbox Class](https://api.flutter.dev/flutter/material/Checkbox-class.html)
