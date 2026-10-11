# Homework 6 — My First Compose App

## Task 3: Colour and Spacing
Colour used: Color.Magenta
Padding kept: 48.dp
What changed / what stayed the same: Ketika padding diubah dari 8 dp ke 48 dp, teks dan gambar bergeser lebih jauh dari tepi layar, jadi isinya terlihat lebih menjorok ke dalam. Warna latar (magenta), urutan isi (dua teks lalu gambar), serta ukuran teks dan gambar tidak berubah. Padding hanya mengatur jarak antara tepi layar dan isi Column, bukan isi itu sendiri. Ini sama seperti margin bergaris kuning di Module M06, Figure 13.

## Task 4: Build Error
First error message:
'M' is not a valid file-based resource name character: File-based resource names must contain only lowercase a-z, 0-9, or underscore
Cause: Nama file gambar saya ubah menjadi My-Picture.png. Nama file resource di Android hanya boleh berisi huruf kecil, angka, dan underscore, sedangkan "My-Picture" memakai huruf besar M dan P serta tanda hubung. Karena itu build gagal.

Why other errors appear: Karena file dengan nama tidak valid gagal diproses, ID R.drawable.my_picture tidak terbentuk. Kode di MainActivity.kt yang memanggil R.drawable.my_picture jadi ikut error (unresolved reference).
Fix: Nama file saya kembalikan menjadi my_picture.png, lalu project saya build ulang sampai berhasil.

## Task 5: Explore the Project
(a) MainActivity: path app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt — file ini adalah titik masuk aplikasi; di dalamnya setContent memanggil MyFirstScreen().
(b) Gradle file: path app/build.gradle.kts — file ini mengatur konfigurasi modul app, seperti versi SDK dan dependensi Compose.
(c) Launcher image line: painter = painterResource(id = R.drawable.ic_launcher_foreground) di MainActivity.kt — baris ini memuat gambar ikon launcher dari folder res/drawable untuk ditampilkan oleh Image.

## Task 6: Preview vs Run
Saya mengubah satu teks lalu hanya me-refresh Preview tanpa menekan Run. Preview langsung berubah, tetapi aplikasi di emulator masih menampilkan teks lama. Hal ini terjadi karena Preview hanya menggambar ulang composable di dalam Android Studio, sedangkan aplikasi di perangkat adalah APK yang sudah terpasang. Agar perubahan muncul di perangkat, kode harus di-build dan di-install lagi dengan menekan Run.

## Task 7: Views vs Compose
1. Pada Views (imperatif), saya harus mengambil sebuah view lalu memerintahkan perubahannya langkah demi langkah, misalnya mencari TextView dan memanggil setText. Pada Compose (deklaratif), saya cukup mendeskripsikan tampilan layar. Di MyFirstScreen, saya menulis Column berisi dua Text dan satu Image, dan Compose yang menggambar serta memperbarui tampilannya.
2.
| Composable | Package                       | Library layer |
|---|-------------------------------|--|
| Column | androidx.compose.foundation.layout | Foundation |
| Text | androidx.compose.material3       | Material |
| Image | androidx.compose.foundation      | Foundation |