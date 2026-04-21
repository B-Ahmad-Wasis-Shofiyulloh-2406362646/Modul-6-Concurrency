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

<details>
<summary>Modul 6 - Reflection 3</summary>

![Commit 3 Screen Capture](/assets/images/Commit3.png)

Di Milestone 3, saya mulai memvalidasi request dengan membaca request line dan membedakan respons berdasarkan path yang diminta. Jika browser meminta `/`, server mengirim `hello.html`, sedangkan request lain diarahkan ke `404.html` agar pengguna mendapat halaman not found yang jelas. Saya juga memahami kenapa refactoring diperlukan, karena pemisahan antara penentuan status/filename dan proses pembuatan response membuat kode lebih mudah dibaca dan lebih siap dikembangkan. Tahap ini menunjukkan bahwa web server tidak hanya mengirim satu halaman statis, tetapi juga bisa merespons kondisi request yang berbeda secara lebih terstruktur.

</details>

<details>
<summary>Modul 6 - Reflection 4</summary>

Di Milestone 4, saya mensimulasikan request lambat dengan menambahkan endpoint `/sleep` yang menunda respons selama 10 detik menggunakan `thread::sleep(Duration::from_secs(10))`. Dari percobaan ini terlihat jelas kelemahan server single-threaded: saat satu request lambat diproses, request lain ikut tertahan sampai proses sebelumnya selesai. Hal ini membantu saya memahami bottleneck pada desain satu thread dan kenapa milestone berikutnya perlu beralih ke server multithreaded dengan thread pool agar beberapa request dapat diproses lebih paralel.

</details>

<details>
<summary>Modul 6 - Reflection 5</summary>

Di Milestone 5, saya mengubah server menjadi multithreaded dengan `ThreadPool` sehingga setiap koneksi tidak lagi diproses langsung di thread utama, tetapi dijalankan sebagai job oleh worker thread. Dengan pendekatan ini, request cepat tetap bisa diproses walaupun ada request lambat seperti `/sleep`, sehingga bottleneck pada single-threaded server berkurang signifikan. Saya juga memahami alur koordinasi antar thread melalui channel (`mpsc`) dan `Arc<Mutex<...>>`, termasuk kenapa thread pool lebih efisien dibanding membuat thread baru untuk setiap request. Perubahan ini membuat server lebih responsif dan lebih dekat ke pola implementasi web server di dunia nyata.

</details>
