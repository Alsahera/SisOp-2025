# Fork: Parent - Child Process

Dalam sistem operasi mirip Unix seperti Linux Ubuntu, `fork()` adalah sebuah *system call* yang digunakan untuk menciptakan sebuah proses baru, yang disebut sebagai *child process*, yang merupakan salinan dari proses yang memanggilnya, yang disebut sebagai *parent process*. Setelah pemanggilan `fork()` berhasil, kernel akan membuat duplikat dari ruang alamat *parent process* untuk *child process*. Ini berarti *child process* akan memiliki salinan dari kode, data, dan *stack parent process* pada saat `fork()` dipanggil.

Setelah proses duplikasi selesai, baik *parent process* maupun *child process* akan melanjutkan eksekusi dari instruksi setelah pemanggilan `fork()`. Perbedaan utama antara keduanya adalah nilai kembalian dari fungsi `fork()`. Pada *parent process*, `fork()` akan mengembalikan *process ID* (PID) dari *child process* yang baru dibuat. Sedangkan pada *child process*, `fork()` akan mengembalikan nilai 0. Jika terjadi kesalahan saat pembuatan proses, `fork()` akan mengembalikan -1 pada *parent process* dan tidak ada *child process* yang dibuat. Mekanisme ini memungkinkan programmer untuk membedakan antara *parent* dan *child process* dan mengeksekusi kode yang berbeda pada masing-masing proses.

### $ ./fork01  
![fork1](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork01.png)  
```
int main() {
                           pid: 27655, ppid: 26948
                            [Main Process]
                                  |
         ------------------------------------------------
        |              |               |
    Iterasi 1       Iterasi 2       Iterasi 3
      |                |                |
   Print info      Print info       Print info
   sleep(3)         sleep(3)         sleep(3)
}
```
Karena kode fork01.cpp tidak menggunakan fork(), tiga iterasi for menjalankan perintah cout yang sama, bukan proses ganda, sehingga output tampak seperti diulang.

### $ ./fork02
![fork2](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork02.png)  
```
int main() { 
                          pid: 28027, ppid: 26948
                            [Main process]
                                 |
fork();                 > Child process created <
                                 +
                               /   \
                             /       \
      pid: 28027, ppid: 26948       pid: 28028, ppid: 28027
         [Parent Process]             [Child Process]

while(1) {               // Kedua proses mencetak:
   cout << pid, x;       // PID masing-masing dan x++
   sleep(2);             // setiap 2 detik
}
}
```
Kode fork02.cpp memiliki loop while (1), yang berarti bahwa itu akan berjalan tanpa henti setiap dua detik, dengan nilai x yang terus meningkat.  Oleh karena itu, selama penggunaan kode ini, hasil akan muncul di layar sampai kita menghentikannya secara mandiri `ctrl c`.

### $ ./fork03
![fork3](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork03.png)  
```
int main() { 
                          pid: 28338, ppid: 26948
                            [Main process]
                                 |
fork();                 > Child process created <
                                 +
                               /   \
                             /       \
      pid: 28338, ppid: 26948       pid: 28339, ppid: 28338
         [Parent Process]             [Child Process]

for (i = 0; i < 5; i++) {
   cout << "This is process <pid>";
   sleep(2);
}
}
```
Fork() digunakan oleh program fork03 untuk membuat satu proses anak.  Setelah itu, proses induk dan anak menjalankan loop lima kali, masing-masing mencetak identitas proses setiap dua detik.  Output akan muncul selang-seling antara proses induk dan anak karena keduanya menjalankan kode yang sama secara paralel.


### $ ./fork04
![fork4](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork04.png)  
```
int main() {
                          pid: 28389, ppid: 26948
                            [Main Process]
                                 |
fork();                 > Child process created <
                                 +
                               /   \
                             /       \
  pid: 28389, ppid: 26948        pid: 28390, ppid: 28389
 [Parent Process]               [Child Process]
      |                               |
  print info                     print info
      |                               |
 wait(child) <------------------ child exits
      |
print "I am quitting."
}
```
Program fork04 menggunakan fork untuk membuat satu proses anak.  Proses anak mencetak PID-nya dan memberi tahu bahwa ia akan berhenti. Proses induk mencetak PID-nya sendiri dan menggunakan wait untuk menunggu anak selesai.  Proses induk mencetak pesan terakhir dan kemudian keluar setelah anak keluar.  Program ini menunjukkan cara proses induk dapat menunggu proses anak untuk dilanjutkan.


### $ ./fork05
![fork5](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork05.png)  
```
int main() { 
                          pid: 28485, ppid: 26948
                            [Main Process]
                                 |
fork();                 > Child process created <
                                 +
                               /   \
                             /       \
  pid: 28485, ppid: 26948        pid: 28486, ppid: 28485
 [Parent Process]               [Child Process]
      |                               |
  print info                     execl("/bin/ls", ...)
      |                               |
 wait(child) <------------------ output of `ls -l /home`
      |
print "I am quitting."
}
```
fork05 dan fork04 sama, tetapi proses anak menggunakan execl() untuk menjalankan perintah sistem ls -l /home. Ini karena execl() menggantikan program ls untuk proses anak, sehingga sisa kode setelah execl() tidak dijalankan pada proses anak.  Seperti biasa, proses induk menunggu sampai LS selesai dan kemudian keluar.  Ini menunjukkan penggunaan execl() untuk menjalankan program luar proses anak.


### $ ./fork06
![fork6](https://github.com/Alsahera/SisOp-2025/blob/main/fork/fork06.png)  
```
int main() {
                            pid: 28584, ppid: ?
                             [Main Process]
                                  |
   fork();                > Child process created <
                                  +
                                /   \
                              /       \
     pid: 28584, ppid: ?         pid: 28585, ppid: 28584
     [Parent Process]           [Child Process]
          |                          |
   print info                   print info
   wait(child)                 execl("fork03")
       |                          |
   wait → done              fork03 starts running:
       |                   +-----------------------+
       |                   | "This is process 28585" (x10)
   print "quitting"        | with 2 sec sleep each |
                           +-----------------------+
}
```
fork06 juga mirip, tetapi proses anak menjalankan program lokal bernama fork03 dengan execl(). Setelah berhasil, proses anak menjadi program fork03 dan menjalankan isi dari program itu. Proses induk hanya mencetak informasi, menunggu proses anak selesai, lalu keluar.  Dalam program ini, proses dapat menjalankan program buatan sendiri sebagai ganti perintah sistem.
