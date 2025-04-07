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
