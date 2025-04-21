# Programming Exercise

## a. Penerapan thread pada contoh SumTask.java
![Penerapan thread pada contoh SumTask.java](https://github.com/Alsahera/SisOp-2025/blob/main/chapter%204/Screenshot%20from%202025-04-21%2016-34-18.png)  
Bagian pertama dari latihan ini menggunakan file bernama SumTask.java. File ini dikompilasi menggunakan perintah javac, kemudian dijalankan dengan java. Dari hasil eksekusinya, program menampilkan output berupa "The sum is 45389". Ini menunjukkan bahwa program berhasil menjalankan proses penjumlahan melalui beberapa thread.

Dalam konteks Java, multithreading biasanya dilakukan dengan menggunakan class Thread atau Runnable, yang memungkinkan beberapa proses berjalan secara bersamaan. Hasil yang muncul menunjukkan bahwa thread-thread tersebut berhasil melakukan tugasnya dan mengembalikan hasil perhitungan yang benar. Dengan kata lain, threading di Java telah berhasil diterapkan dengan baik.

## b. Penerapan Thread di Linux (thrd-posix.c)
![penerapan Thread di Linux (thrd-posix.c)](https://github.com/Alsahera/SisOp-2025/blob/main/chapter%204/Screenshot%20from%202025-04-21%2016-58-12.png)  
Implementasi multithreading juga dilakukan menggunakan bahasa C di lingkungan Linux, dengan file thrd-posix.c. Proses kompilasi menggunakan GCC dilakukan dengan menambahkan flag -lpthread, yang menunjukkan bahwa program menggunakan POSIX Threads.

Setelah dikompilasi, program dijalankan dengan perintah ./thrd 100000. Angka 100000 kemungkinan besar adalah parameter yang menunjukkan jumlah iterasi atau data yang akan diproses secara paralel oleh thread. Output yang ditampilkan adalah "sum = 705082704", menandakan bahwa proses penjumlahan berhasil dilakukan oleh thread-thread yang dibuat.

Penggunaan pthread dalam C memungkinkan pembuatan dan pengelolaan thread secara manual, sehingga lebih fleksibel namun juga membutuhkan pemahaman yang lebih dalam terhadap sinkronisasi dan manajemen memori.
