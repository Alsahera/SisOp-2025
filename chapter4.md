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

## 4. Practice Exercises

### 4.1
**Contoh program yang mendapat keuntungan dari multithreading:**
1. Web server: Menggunakan satu thread untuk tiap permintaan klien memungkinkan server menangani banyak permintaan secara bersamaan.  
2. Aplikasi pemrosesan gambar: Membuat thumbnail dari banyak gambar bisa dilakukan paralel, satu thread per gambar.  
3. Editor teks seperti word processor: Thread terpisah untuk menangani input keyboard, spell-checking, dan auto-save, agar responsif dan efisien.  

### 4.2 Amdahl’s Law Calculation

**Gunakan Amdahl’s Law untuk menghitung speedup dengan 60% kode yang bisa diparalelkan.**

Rumus Amdahl’s Law:
```math
\text{Speedup} = \frac{1}{(1 - P) + \frac{P}{N}}
```

Dengan:
- \( P = 0.6 \) (60% bagian paralel)
- \( N \) = jumlah core

#### a. Untuk 2 core:
```math
\text{Speedup} = \frac{1}{0.4 + \frac{0.6}{2}} = \frac{1}{0.4 + 0.3} = \frac{1}{0.7} \approx 1.43
```

#### b. Untuk 4 core:
```math
\text{Speedup} = \frac{1}{0.4 + \frac{0.6}{4}} = \frac{1}{0.4 + 0.15} = \frac{1}{0.55} \approx 1.82
```



### 4.3
**Web server:** menggunakan *task parallelism* karena tiap thread menangani tugas berbeda.

### 4.4
**User-level threads vs Kernel-level threads:**
- User-level: efisien, cepat dibuat.
- Kernel-level: bisa paralel, cocok untuk blocking operations.

### 4.5
**Context-switch antar kernel threads:**
1. Simpan state lama (register, PC).
2. Muat state baru.
3. Update struktur kernel.

### 4.6
**Resource dibuat:**
- Thread: stack, register.
- Proses: memori, PCB lengkap.

### 4.7
**Thread real-time harus terikat ke LWP** agar dijadwalkan tepat waktu.

## Exercises

### 4.8
Multithreading tidak efektif pada:
- Program sederhana.
- Akses data bersama intensif.

### 4.9
Multithreading berguna untuk I/O blocking: thread lain bisa tetap berjalan.

### 4.10
- a. ❌
- b. ✅
- c. ✅
- d. ❌

### 4.11
Bisa lebih baik jika menggunakan model one-to-one atau many-to-many.

### 4.12
Chrome gunakan proses untuk keamanan dan stabilitas.

### 4.13
Concurrency tanpa paralelisme: sistem single-core dengan interleaving.

### 4.14
Menggunakan Amdahl's Law:
- Hasil dipecah sesuai soal.

### 4.15
- a. Task
- b. Data
- c. Task
- d. Data
- e. Campuran

### 4.16
Gunakan 4 thread CPU + 2 thread I/O.

### 4.17
Total proses dan thread tergantung posisi `fork()` dan `thread_create()`.

### 4.18
Linux: semua task
Windows: proses & thread berbeda struktur.

### 4.19
Output:
- Child: 5
- Parent: 0

### 4.20
Model threading:
- a. Underutilized
- b. Ideal
- c. Lebih baik dari a, masih bisa antri

## Programming Problems

### 4.22
**Statistik multithreaded:**
- Thread 1: average
- Thread 2: min
- Thread 3: max

### 4.23
**Bilangan Prima:**
- Thread cari dan cetak bilangan prima <= input.

### 4.24
**Monte Carlo Estimator:**
- Gunakan banyak thread untuk generate titik dan hitung π.

### 4.25
**Monte Carlo dengan OpenMP:**
- Gunakan `#pragma omp parallel for`.

### 4.26
**Multithreaded Date Server:**
- Tiap koneksi → thread baru.

### 4.27
**Fibonacci:**
- Thread isi array global, parent cetak hasil.

### 4.28
**PID Manager Test:**
- Buat 100 thread, masing-masing allocate & release PID.

### 4.29
**Java Echo Server:**
- Setiap client → `new Thread(new EchoHandler()).start()`

