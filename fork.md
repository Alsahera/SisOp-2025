# Fork: Parent - Child Process

Dalam sistem operasi mirip Unix seperti Linux Ubuntu, `fork()` adalah sebuah *system call* yang digunakan untuk menciptakan sebuah proses baru, yang disebut sebagai *child process*, yang merupakan salinan dari proses yang memanggilnya, yang disebut sebagai *parent process*. Setelah pemanggilan `fork()` berhasil, kernel akan membuat duplikat dari ruang alamat *parent process* untuk *child process*. Ini berarti *child process* akan memiliki salinan dari kode, data, dan *stack parent process* pada saat `fork()` dipanggil.

Setelah proses duplikasi selesai, baik *parent process* maupun *child process* akan melanjutkan eksekusi dari instruksi setelah pemanggilan `fork()`. Perbedaan utama antara keduanya adalah nilai kembalian dari fungsi `fork()`. Pada *parent process*, `fork()` akan mengembalikan *process ID* (PID) dari *child process* yang baru dibuat. Sedangkan pada *child process*, `fork()` akan mengembalikan nilai 0. Jika terjadi kesalahan saat pembuatan proses, `fork()` akan mengembalikan -1 pada *parent process* dan tidak ada *child process* yang dibuat. Mekanisme ini memungkinkan programmer untuk membedakan antara *parent* dan *child process* dan mengeksekusi kode yang berbeda pada masing-masing proses.

### $ ./fork01  
![fork1](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork01.png)  
Karena kode fork01.cpp tidak menggunakan fork(), pohon prosesnya sederhana dan hanya memiliki satu proses yang berjalan (proses utama yang menjalankan kode), itu hanya mencetak informasi tentang proses yang sedang berjalan.

### $ ./fork02
![fork2](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork02.png)  
Kode fork02.cpp memiliki loop while (1), yang berarti bahwa itu akan berjalan tanpa henti setiap dua detik, dengan nilai x yang terus meningkat.  Oleh karena itu, selama penggunaan kode ini, hasil akan muncul di layar sampai kita menghentikannya secara mandiri `ctrl c`.

### $ ./fork03
![fork3](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork03.png)  
Outputnya akan bercabang dan diulang karena fork() dan loop for. Dengan demikian, outputnya akan terdiri dari sepuluh baris, lima baris dari induk, dan lima baris dari anak, dengan jeda dua detik di antara baris.

### $ ./fork04
![fork4](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork04.png)  
Proses induk mencetak pesan dan menggunakan wait() untuk menunggu proses anak selesai. Proses anak mencetak pesan dan kemudian keluar.

### $ ./fork05
![fork5](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork05.png)  
Dengan menggunakan execl(), proses anak menjalankan perintah ls -l /home. Hasil dari perintah ini, yaitu daftar file dan direktori yang ada di dalam direktori /home, ditampilkan.  Proses induk keluar (wait()) setelah proses anak selesai.

### $ ./fork06
![fork6](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork06.png)  
Fungsi wait() membuat proses induk menunggu hingga proses anak selesai, dan fungsi execl() mengganti kode yang sedang berjalan dengan kode dari program lain (fork03).
