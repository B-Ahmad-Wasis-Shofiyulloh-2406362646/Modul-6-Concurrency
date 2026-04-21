### Reflection Notes

<details>
<summary>Modul 6 - Reflection 1</summary>

Di Milestone 1, saya belajar membangun *single-threaded web server* sederhana di Rust dengan `TcpListener` yang mendengarkan koneksi lokal pada `127.0.0.1:7878`. Setiap koneksi diproses lewat `handle_connection` menggunakan `TcpStream` dan `BufReader` agar permintaan HTTP bisa dibaca baris demi baris melalui `.lines()`. Dari sini, saya memahami bahwa request dari browser memiliki struktur yang jelas, seperti baris `GET`, header pendukung, dan baris kosong sebagai penanda akhir request. Meskipun server belum mengirim respons, tahap ini sudah memperlihatkan alur dasar komunikasi *client-server* dan menjadi fondasi untuk milestone berikutnya.

</details>

<details>
<summary>Modul 6 - Reflection 2</summary>

![Commit 2 Screen Capture](/assets/images/Commit2.png)

Di Milestone 2, saya menambahkan kemampuan server untuk mengirim respons HTTP yang berisi halaman HTML. File `hello.html` dibaca dengan `fs::read_to_string`, lalu isi file digabung dengan status line dan header `Content-Length` sebelum dikirim kembali ke browser melalui `write_all`. Dari tahap ini, saya memahami bahwa server tidak hanya menerima request, tetapi juga harus menyusun response yang valid agar browser dapat menampilkan halaman dengan benar. Perubahan ini membuat alur kerja web server menjadi lebih lengkap, dari menerima koneksi sampai mengembalikan konten HTML.

</details>
