# Manajemen Proses

- **Proses** adalah program yang sedang dieksekusi. Ini merupakan unit kerja dalam sistem. Program adalah entitas pasif, sedangkan proses adalah entitas aktif.
- Proses membutuhkan sumber daya untuk menyelesaikan tugasnya:
  - CPU, memori, I/O, file
  - Data inisialisasi
- Terminasi proses memerlukan pelepasan sumber daya yang dapat digunakan kembali.
- **Proses single-threaded** memiliki satu program counter yang menentukan lokasi instruksi berikutnya yang akan dieksekusi.
  - Proses mengeksekusi instruksi secara berurutan, satu per satu, hingga selesai.
- **Proses multi-threaded** memiliki satu program counter per thread.
- Biasanya sistem memiliki banyak proses, baik dari pengguna maupun sistem operasi, yang berjalan secara bersamaan di satu atau lebih CPU.
  - Konkuren dengan cara melakukan multiplexing CPU di antara proses/thread.

## Aktivitas Manajemen Proses

- Membuat dan menghapus proses pengguna maupun sistem.
- Menangguhkan dan melanjutkan proses.
- Menyediakan mekanisme untuk sinkronisasi proses.
- Menyediakan mekanisme untuk komunikasi proses.
- Menyediakan mekanisme untuk penanganan deadlock.

---

# Manajemen Memori

- Untuk mengeksekusi program, semua (atau sebagian) instruksi harus berada di memori.
- Semua (atau sebagian) data yang dibutuhkan oleh program harus berada di memori.
- **Manajemen memori** menentukan apa yang ada di memori dan kapan:
  - Mengoptimalkan penggunaan CPU dan respons komputer terhadap pengguna.
- **Aktivitas manajemen memori**:
  - Melacak bagian memori yang sedang digunakan dan oleh siapa.
  - Menentukan proses (atau bagian dari proses) serta data yang dipindahkan masuk dan keluar dari memori.
  - Mengalokasikan dan membebaskan ruang memori sesuai kebutuhan.

---

# Manajemen Sistem Berkas

- **OS** menyediakan tampilan logis yang seragam untuk penyimpanan informasi.
  - Mengabstraksi properti fisik ke dalam unit penyimpanan logis - file.
  - Setiap media dikendalikan oleh perangkat (misalnya, disk drive, tape drive).
  - Properti yang bervariasi meliputi kecepatan akses, kapasitas, kecepatan transfer data, metode akses (sekuensial atau acak).
- **Manajemen sistem berkas**:
  - File biasanya diorganisir dalam direktori.
  - Kontrol akses pada sebagian besar sistem menentukan siapa yang dapat mengakses apa.
  - **Aktivitas OS** meliputi:
    - Membuat dan menghapus file serta direktori.
    - Menyediakan primitive untuk memanipulasi file dan direktori.
    - Memetakan file ke penyimpanan sekunder.
    - Mencadangkan file ke media penyimpanan stabil (non-volatile).

---

# Manajemen Penyimpanan Massal

- Biasanya disk digunakan untuk menyimpan data yang tidak dapat dimuat dalam memori utama atau data yang harus disimpan untuk jangka waktu lama.
- Pengelolaan yang tepat sangat penting.
- Kecepatan keseluruhan operasi komputer bergantung pada subsistem disk dan algoritmanya.
- **Aktivitas OS**:
  - Mounting dan unmounting.
  - Manajemen ruang kosong.
  - Alokasi penyimpanan.
  - Penjadwalan disk.
  - Partisi.
  - Perlindungan.
- **Beberapa penyimpanan tidak perlu cepat**:
  - Penyimpanan tersier mencakup penyimpanan optik, pita magnetik.
  - Tetap harus dikelola – oleh OS atau aplikasi.

---

# Caching

- Prinsip penting yang dilakukan pada banyak level dalam komputer (di perangkat keras, sistem operasi, perangkat lunak).
- Informasi yang digunakan disalin dari penyimpanan yang lebih lambat ke penyimpanan yang lebih cepat untuk sementara.
- **Penyimpanan yang lebih cepat (cache) diperiksa terlebih dahulu** untuk menentukan apakah informasi tersedia:
  - Jika ada, informasi digunakan langsung dari cache (lebih cepat).
  - Jika tidak, data disalin ke cache dan digunakan dari sana.
- **Cache lebih kecil dibandingkan penyimpanan yang di-cache**:
  - Manajemen cache adalah masalah desain yang penting.
  - Ukuran cache dan kebijakan penggantian cache menjadi pertimbangan utama.
