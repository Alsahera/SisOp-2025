# A.1 Migrasi Fitur

Fitur sistem operasi yang dulunya hanya ada di komputer besar seperti mainframe kini banyak yang diadopsi ke komputer kecil seperti mikrokomputer dan perangkat genggam. Konsep sistem operasi tetap relevan di berbagai kelas komputer karena adanya migrasi fitur. Contoh awal migrasi fitur dimulai dari sistem operasi MULTICS. Memahami sejarah ini penting untuk memahami sistem operasi modern.

MULTICS, sistem operasi untuk mainframe yang dikembangkan oleh MIT dan mitranya, menjadi inspirasi bagi UNIX. UNIX kemudian dikembangkan untuk minikomputer dan diadopsi lebih lanjut oleh mikrokomputer sekitar tahun 1980. Fitur-fitur UNIX menjadi dasar dari berbagai sistem operasi modern seperti Windows, macOS, dan Linux—bahkan kini bisa ditemukan di perangkat genggam seperti PDA. Ini menunjukkan bagaimana fitur dari sistem besar bermigrasi ke sistem yang lebih kecil.

# A.2 Sistem Awal

Komputer sebelum tahun 1940-an hanya dapat menjalankan tugas tetap, dan mengubah fungsinya memerlukan pekerjaan manual besar. Pada 1940-an, Alan Turing dan John von Neumann mengembangkan konsep *stored-program computer*, yang menjadi dasar komputer modern. Komputer serbaguna pertama kemungkinan adalah Manchester Mark 1 (1949), diikuti oleh komputer komersial pertama, Ferranti Mark 1 (1951). Komputer awal berukuran sangat besar, dioperasikan langsung dari konsol oleh programmer, dan menggunakan media seperti sakelar, pita kertas, atau kartu berlubang untuk input dan output.

## A.2.1 Sistem Komputer Terdedikasi

Pada era awal komputer, seiring dengan berkembangnya perangkat keras dan perangkat lunak, banyak perangkat seperti pembaca kartu, printer, dan pita magnetik menjadi umum. Untuk memudahkan pemrograman, dibuatlah assembler, loader, linker, dan pustaka fungsi yang memungkinkan penggunaan ulang kode. *Device driver* diciptakan untuk menangani operasi I/O yang kompleks sesuai karakteristik masing-masing perangkat. Dengan munculnya kompiler untuk bahasa pemrograman seperti FORTRAN dan COBOL, meskipun pemrograman menjadi lebih mudah, proses eksekusi program menjadi lebih kompleks dan memakan waktu, karena melibatkan banyak langkah manual seperti pemasangan dan pelepasan pita magnetik dan kartu. Waktu penyiapan yang lama mengakibatkan CPU sering menganggur, padahal komputer pada masa itu sangat mahal dan langka, sehingga efisiensi pemanfaatannya sangat penting.

## A.2.2 Sistem Komputer Bersama

1.  **Masalah Awal:** Programmer mengoperasikan komputer secara langsung, sehingga waktu persiapan lama dan tidak efisien.
2.  **Solusi Pertama:** Operator profesional menggantikan programmer dalam mengoperasikan komputer, sehingga waktu setup berkurang.
3.  **Solusi Kedua:** Pekerjaan sejenis dikelompokkan dalam batch agar setup tidak perlu dilakukan berulang.
4.  **Permasalahan Lanjutan:** CPU sering idle saat transisi antar pekerjaan karena operator harus bertindak manual.
5.  **Inovasi:** Diperkenalkan *automatic job sequencing* dengan program *resident monitor* yang otomatis mengelola eksekusi pekerjaan.
6.  **Control Cards:** Diperkenalkan kartu perintah seperti `$JOB`, `$FTN`, `$RUN`, `$END` untuk memberi instruksi ke monitor.
7.  **Komponen Monitor:** Interpreter kartu, loader, dan driver perangkat I/O.
8.  **Manfaat:** Mengurangi intervensi manusia, meningkatkan efisiensi.
9.  **Tantangan Baru:** Perbedaan kecepatan besar antara CPU dan perangkat I/O membuat CPU tetap sering menganggur.

# A.2.3 Overlapped I/O

1.  **Masalah Awal:** I/O lambat (kartu & printer), membuat CPU sering menganggur.
2.  **Solusi Off-line:**
    * Gunakan pita magnetik sebagai perantara input/output.
    * CPU membaca dari pita, bukan langsung dari pembaca kartu/printer.
    * Efisiensi meningkat, tapi waktu tunggu lebih panjang.
3.  **Penggantian oleh Disk:**
    * Disk bisa akses acak, tidak harus urut seperti pita.
    * Input/output langsung ke disk, bukan pita.
4.  **Spooling:**
    * Disk digunakan sebagai buffer besar.
    * Input dan output disimpan di disk, lalu dibaca/ditulis sesuai kebutuhan.
    * Bisa dilakukan bersamaan dengan eksekusi pekerjaan lain.
5.  **Keunggulan Spooling:**
    * CPU dan perangkat I/O bisa bekerja secara paralel.
    * Meningkatkan efisiensi dan performa sistem.
    * Mengarah ke konsep multiprogramming, dasar OS modern.

# A.3 Atlas

* **Lokasi & Waktu:** Universitas Manchester, Inggris (akhir 1950-an).
* **Fitur Unggulan:**
    * Batch system + spooling
    * Device drivers terintegrasi
    * System call melalui instruksi khusus (extra codes)
* **Manajemen Memori:**
    * Drum memory sebagai utama, core memory sebagai cache
    * Menggunakan demand paging
    * Memori virtual dengan pemetaan melalui memori asosiatif
* **Spesifikasi:**
    * 48-bit words
    * 24-bit decimal address
    * 98K kata di drum, 16K kata di core
    * Halaman: 512 kata; 32 frame tersedia
* **Page Replacement Algorithm:**
    * Berdasarkan riwayat akses memori
    * Prediksi berdasarkan pola looping
    * Menggunakan bit referensi dan interval waktu antar referensi
 
# A.4 XDS-940

## 1. Asal & Tujuan Sistem
- Dikembangkan di **University of California, Berkeley** pada **awal 1960-an**.
- Merupakan sistem **time-sharing** (berbagi waktu), yang memungkinkan **banyak pengguna** mengakses komputer secara **interaktif dan bersamaan**.

## 2. Manajemen Memori
- Menggunakan **paging** untuk **relokasi** memori proses.
- **Tidak** menggunakan **demand paging** (data hanya dipindahkan saat dibutuhkan).
- **Memori Virtual per Proses**: 16 KB kata.
- **Memori Fisik**: 64 KB kata.
- **Ukuran halaman**: 2 KB kata.
- **Tabel halaman disimpan di register** → akses cepat terhadap pemetaan memori.
- Karena memori fisik lebih besar, **banyak proses bisa disimpan sekaligus**.
- **Page sharing** diaktifkan untuk kode yang **read-only dan reentrant**, memungkinkan efisiensi ruang memori.

## 3. Manajemen Proses & Time-Sharing
- Proses disimpan di **drum memory** dan **swap** ke/dari memori utama sesuai kebutuhan.
- Mendukung **sistem call untuk proses**:
  - Membuat (`create`)
  - Memulai (`start`)
  - Menunda (`suspend`)
  - Menghapus (`destroy`)
- **Proses bisa membuat subprocess**, membentuk **struktur pohon** (tree):
  - Akar (root): proses utama
  - Node anak: subprocess
  - Subprocess bisa menciptakan anak lagi → hierarki proses
- Proses dapat **berbagi memori** untuk keperluan:
  - **Komunikasi antarproses**
  - **Sinkronisasi**

## 4. Keamanan & Mode Eksekusi
- Menambahkan **user-monitor mode**:
  - **Mode pengguna**: terbatas, tidak bisa menjalankan instruksi berbahaya.
  - **Mode sistem/monitor**: memiliki akses penuh ke sumber daya.
- **Instruksi privileged (istimewa)**: seperti I/O dan halt hanya bisa dijalankan di mode sistem.
- Jika instruksi privileged dijalankan di mode pengguna → terjadi **trap ke sistem operasi**.

## 5. Manajemen Berkas (File System)
- File disimpan di **drum memory** dalam **blok 256 kata**.
- **Bitmap** digunakan untuk melacak blok yang kosong/terpakai.
- Setiap file memiliki:
  - **Blok indeks**: berisi pointer ke blok data.
  - **Blok data**: tempat isi file disimpan.
- Jika satu blok indeks tidak cukup, blok tambahan akan **dirantai (chained)** untuk memperluas.

## 6. Perangkat Keras dan Modifikasi
- Dibangun dari **XDS-930** yang telah dimodifikasi:
  - Penambahan fitur untuk mendukung sistem operasi (seperti mode eksekusi, sistem call).
  - Penggunaan paging sederhana.

## Kesimpulan
Sistem operasi **XDS-940** adalah **pendahulu dari sistem time-sharing modern**, dengan beberapa fitur canggih untuk zamannya:
- Penggunaan **paging** dan **relokasi memori**
- **Manajemen proses bertingkat (berstruktur pohon)**
- **Sistem berkas dengan indeks dan manajemen blok**
- **Keamanan eksekusi** melalui mode pengguna dan sistem

# A.5 THE

Sistem operasi THE dirancang di Technische Hogeschool Eindhoven, Belanda, pada pertengahan tahun 1960-an. Sistem ini merupakan sistem batch yang dijalankan di komputer EL X8, yang memiliki memori sebesar 32 KB dengan kata-kata sepanjang 27 bit. Keunggulan utama THE terletak pada desainnya yang bersih dan terstruktur secara lapis demi lapis, serta penggunaan sekumpulan proses konkuren yang disinkronkan dengan semafor. Berbeda dengan sistem seperti XDS-940, proses dalam sistem THE bersifat statis dan dibangun sebagai satu kesatuan proses yang saling bekerja sama. Terdapat lima proses pengguna aktif yang bertugas mengompilasi, menjalankan, dan mencetak program pengguna. Setelah menyelesaikan satu pekerjaan, proses tersebut akan kembali ke antrian input untuk menangani pekerjaan berikutnya.

Untuk penjadwalan CPU, sistem ini menggunakan algoritma berbasis prioritas yang dihitung ulang setiap dua detik. Prioritas diberikan lebih tinggi kepada proses yang baru atau lebih sering melakukan input/output, karena dihitung secara terbalik berdasarkan jumlah waktu CPU yang telah digunakan dalam 8 hingga 10 detik terakhir. Dalam hal manajemen memori, keterbatasan perangkat keras membuat sistem ini hanya bisa menggunakan skema paging berbasis perangkat lunak. Karena hanya mendukung bahasa Algol, kompiler Algol otomatis memasukkan panggilan ke rutin sistem untuk memastikan data yang dibutuhkan tersedia di memori. Jika belum, maka data akan diambil dari drum penyimpanan dengan kapasitas 512 KB. Halaman memori berukuran 512 kata dan pengelolaan halamannya menggunakan strategi Least Recently Used (LRU). Untuk menghindari terjadinya deadlock, sistem ini menerapkan algoritma banker sebagai strategi pencegahan.

Sistem Venus, yang berkaitan erat dengan THE, juga dirancang dengan struktur berlapis dan penggunaan semafor sebagai alat sinkronisasi antarproses. Namun, Venus lebih unggul dalam hal performa karena bagian bawah sistem diimplementasikan dalam mikrokode, yang membuatnya bekerja jauh lebih cepat. Tidak seperti THE yang merupakan sistem batch, Venus didesain sebagai sistem time-sharing, memungkinkan banyak pengguna mengakses sistem secara bersamaan. Dalam hal manajemen memori, Venus menggabungkan metode paging dan segmentasi melalui sistem paged-segmented memory untuk efisiensi yang lebih baik.

# A.6 RC 4000

RC 4000 adalah sistem operasi yang dikembangkan di akhir 1960-an dengan pendekatan unik, berfokus pada pembangunan kernel modular yang dapat menjadi dasar untuk berbagai jenis sistem, alih-alih berperan sebagai sistem batch atau time-sharing secara langsung. Sistem ini menekankan pada pemisahan tanggung jawab melalui struktur berlapis dan mendukung proses-proses konkuren yang berkomunikasi lewat sistem pesan. Setiap proses berinteraksi melalui pengiriman pesan tetap, yang ditangani oleh kernel melalui buffer bersama, dengan penjadwalan round-robin. Tidak hanya proses, perangkat I/O pun diperlakukan sebagai proses yang berkomunikasi melalui pesan, membuat seluruh sistem bersifat seragam dalam hal komunikasi dan sinkronisasi. Pendekatan ini menjadikan RC 4000 sebagai salah satu sistem yang meletakkan dasar penting dalam pengembangan arsitektur sistem operasi modern.

# A.7 CTSS

CTSS adalah sistem operasi *time-sharing* eksperimental dari MIT yang diperkenalkan pada tahun 1961, memungkinkan hingga 32 pengguna berinteraksi secara langsung melalui terminal. Sistem ini dijalankan pada komputer IBM 7090 dan menggunakan strategi penjadwalan *multilevel feedback queue*, yang menyesuaikan waktu eksekusi program berdasarkan performa sebelumnya. Meskipun sederhana dan terbatas, CTSS membuktikan bahwa konsep *time-sharing* layak digunakan, dan menjadi cikal bakal bagi pengembangan sistem-sistem lanjutan seperti MULTICS.

# A.8 MULTICS

MULTICS merupakan lanjutan dari sistem CTSS yang dirancang untuk memberikan layanan komputasi seperti halnya layanan utilitas umum, seperti listrik. Sistem ini memperkenalkan konsep inovatif seperti *paged segmentation*, integrasi alamat virtual ke dalam sistem berkas, dan arsitektur berlapis yang mendukung keamanan proses. Ditulis sebagian besar dalam PL/1 dan dikembangkan untuk mendukung multiprosesor, MULTICS menjadi tonggak penting dalam sejarah sistem operasi modern, yang kemudian menginspirasi lahirnya UNIX dan banyak fitur keamanan serta struktur direktori yang kita kenal saat ini.

# A.9 IBM OS/360

Perkembangan sistem operasi IBM menunjukkan evolusi dari sistem batch sederhana ke sistem *time-sharing* yang kompleks. IBM/360 dengan OS/360 mencoba menyatukan platform IBM yang beragam, namun kompleksitas dan keterbatasan arsitektur membatasi performa dan fleksibilitasnya. Meski *virtual memory* dan fitur-fitur lanjutan ditambahkan di versi-versi berikutnya seperti MVS, IBM tetap menghadapi tantangan dalam mewujudkan visi *time-sharing* seperti pada TSS/360. Kegagalan TSS/360 dan MULTICS mencerminkan bahwa solusi komputasi besar tidak selalu praktis, terutama ketika teknologi komputasi mulai bergeser ke arah sistem yang lebih kecil dan terdistribusi seperti minikomputer dan PC.

# A.10 TOPS-20

TOPS-20, sistem operasi warisan dari TENEX, menjadi puncak inovasi *time-sharing* yang dikembangkan dari komputer PDP-10 oleh BBN dan kemudian diadopsi oleh DEC. Dengan fitur *virtual memory* dan antarmuka baris perintah yang interaktif, TOPS-20 menjelma menjadi sistem *time-sharing* paling populer saat itu. Namun, seiring berjalannya waktu dan pergeseran teknologi, DEC menghentikan pengembangan sistem 36-bit ini dan beralih ke arsitektur 32-bit VAX dan sistem operasi VMS yang lebih modern dan *business-oriented*.

# A.11 CP/M and MS/DOS

Perkembangan komputer pribadi dimulai dari mesin sederhana yang menjalankan satu program pada satu waktu. CP/M menjadi standar awal bagi komputer berbasis Intel 8080, menyediakan antarmuka teks dan fungsionalitas dasar. Namun, kehadiran IBM PC membawa perubahan besar. MS-DOS, hasil kerja sama IBM dengan Microsoft, menjadi penerus CP/M untuk prosesor 16-bit Intel 8086. Dengan fitur yang lebih kaya namun tetap sederhana, MS-DOS mendominasi era awal komputer pribadi meski tanpa dukungan fitur modern seperti proteksi memori.

