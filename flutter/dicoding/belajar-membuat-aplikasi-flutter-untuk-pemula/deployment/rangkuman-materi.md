# 📖 Rangkuman Materi

Kita telah mempelajari praktik deployment Flutter untuk beberapa platform. Mari kita ulas kembali apa saja yang sudah kita pelajari.

*   Informasi terkait aplikasi Android yang ingin di-build tersedia pada berkas **android/app/src/main/AndroidManifest.xml**. Pada berkas ini kita bisa mengatur nama, ikon, perizinan aplikasi, dll. Ada dua format build Android yang bisa dibuat, yaitu .apk dan .aab. Untuk melakukan build jalankan perintah berikut:

    ```
    flutter build apk        // Untuk format apk
    flutter build appbundle  // Untuk format aab
    ```
*   Konfigurasi untuk aplikasi iOS tersedia pada berkas **ios/Runner/Info.plist**. Pada berkas ini kita bisa mengatur nama aplikasi, ikon, dan konfigurasi lainnya. Untuk melakukan build Flutter menjadi file IPA, jalankan perintah berikut:

    ```
    flutter build ios
    ```
*   Konfigurasi untuk aplikasi web tersedia pada berkas web/manifest.json. Pada berkas ini kita bisa mengatur nama aplikasi, ikon, dan konfigurasi lainnya. Untuk melakukan build Flutter web, jalankan perintah berikut:

    ```
    flutter build web
    ```

Selamat! Anda telah menyelesaikan modul terakhir pada kelas ini. Anda telah belajar banyak mulai dari proses instalasi hingga ke tahap deployment aplikasi. Untuk bisa dinyatakan lulus dari kelas ini, Anda perlu mengirimkan submission berupa aplikasi Flutter dengan tema bebas. Manfaatkan materi yang sudah Anda pelajari dan kirimkan aplikasi terbaik Anda ya! Good luck!
