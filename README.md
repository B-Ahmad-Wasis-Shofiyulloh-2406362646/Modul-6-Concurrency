### Reflection Notes

<details>
<summary>Modul 6 - Reflection 1</summary>

Di Milestone 1, saya belajar membangun *single-threaded web server* sederhana di Rust dengan `TcpListener` yang mendengarkan koneksi lokal pada `127.0.0.1:7878`. Setiap koneksi diproses lewat `handle_connection` menggunakan `TcpStream` dan `BufReader` agar permintaan HTTP bisa dibaca baris demi baris melalui `.lines()`. Dari sini, saya memahami bahwa request dari browser memiliki struktur yang jelas, seperti baris `GET`, header pendukung, dan baris kosong sebagai penanda akhir request. Meskipun server belum mengirim respons, tahap ini sudah memperlihatkan alur dasar komunikasi *client-server* dan menjadi fondasi untuk milestone berikutnya.

</details>
