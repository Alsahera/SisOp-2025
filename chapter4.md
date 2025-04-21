# Chapter 4 - Threads & Concurrency: Exercises and Programming Problems

## 1. Konsep Single Thread dan Multithread  
### Single thread  
Single Thread: Sebuah proses dengan single thread berarti hanya ada satu alur eksekusi yang berjalan. Ini artinya, satu tugas dikerjakan satu per satu secara berurutan. Jika ada operasi lambat (seperti membaca file atau menunggu respon jaringan), maka keseluruhan proses akan terblokir sampai operasi itu selesai. Proses ini sederhana dalam manajemen memori dan debugging, tapi kurang efisien untuk memanfaatkan prosesor multi-core.  
### Multithread  
Multithread: Dalam model multithread, sebuah proses memiliki beberapa alur eksekusi (thread) yang bisa berjalan secara bersamaan. Setiap thread bisa mengerjakan tugas berbeda, yang meningkatkan performa terutama di sistem multi-core. Multithreading memungkinkan aplikasi merespons lebih cepat dan menyelesaikan lebih banyak pekerjaan dalam waktu singkat, tetapi manajemen thread bisa lebih kompleks.  
### Ilustrasi  
![ilustrasi](https://github.com/Alsahera/SisOp-2025/blob/main/ilustrasi.png)
## 2. Programming Exercise: Penerapan Thread
### a. Penerapan Thread pada SumTask.java  
### b. Penerapan Thread di Linux (thrd-posix.c)  
### c. Penerapan Thread di Microsoft Windows (thrd-win32.c)  
## 3. PPT

