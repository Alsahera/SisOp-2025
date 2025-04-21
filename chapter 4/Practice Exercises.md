# 4. Practice Exercises
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
**Web server:** menggunakan *task parallelism* karena setiap thread menangani permintaan yang berbeda, bukan melakukan operasi yang sama pada data berbeda.


### 4.4
**User-level threads vs Kernel-level threads:**
- User-level threads: dikelola oleh pustaka pengguna, tanpa interaksi langsung dengan kernel.
- Kernel-level: bisa paralel, cocok untuk blocking operations.

**Kapan lebih baik?**
- User-level lebih efisien pada sistem dengan banyak thread ringan tanpa sering blocking.
- Kernel-level lebih baik saat thread sering menunggu I/O, karena kernel bisa menjadwalkan thread lain.

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
**Ya, thread real-time perlu diikat ke LWP (Lightweight Process).** Karena hanya LWP yang dijadwalkan oleh kernel, pengikatan memastikan thread real-time mendapatkan jaminan eksekusi yang tepat waktu.

### 4.8
Multithreading tidak efektif pada:
- Program sederhana yang hanya membaca satu file kecil dan mencetak isi ke layar.
- Aplikasi dengan banyak akses ke resource bersama (misalnya counter global), yang menyebabkan banyak thread saling menunggu (contention).

### 4.9
Multithreaded dengan multiple kernel threads bisa lebih baik jika satu thread melakukan I/O blocking, karena thread lain masih bisa dijadwalkan dan berjalan oleh OS.

### 4.10
**Komponen yang shared antar thread:**
- a. Register values: ❌ Tidak dibagi
- b. Heap memory: ✅ Dibagi
- c. Global variables: ✅ Dibagi
- d. Stack memory: ❌ Masing-masing thread punya stack sendiri

### 4.11
Ya. Di multiprocessor, banyak user-level threads bisa mendapat performa lebih baik karena bisa dijadwalkan secara paralel oleh kernel (tergantung model thread digunakan). Tapi pada sistem one-to-one atau many-to-many, biasanya butuh kernel threads agar paralel.

### 4.12
Membuka tiap tab Chrome sebagai proses memberi isolasi lebih baik (keamanan, crash handling). Jika pakai thread, satu thread crash bisa hancurkan seluruh aplikasi. Jadi proses > thread untuk keamanan dan stabilitas.


### 4.13
Concurrency tanpa parallelism bisa terjadi, contohnya pada sistem dengan satu core: thread tampak berjalan bersamaan tapi sebenarnya bergantian (via context-switching).

### 4.14
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

### 4.15
**Task vs Data Parallelism:**
- a. Thumbnail generator: Task parallelism
- b. Matrix transpose: Data parallelism
- c. Network I/O (read/write): Task
- d. Fork-join array summation: Data
- e. Grand Central Dispatch (GCD): Task, kadang hybrid

### 4.16
**I/O hanya dilakukan di awal dan akhir (sequential), jadi:**
- Input/output: 1 thread cukup untuk masing-masing.
- CPU-intensive: 4 threads (jumlah core tersedia) untuk memaksimalkan paralelisme di sistem 4-core.  

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

