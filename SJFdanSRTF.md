# SJF dan SRTF Scheduling Algorithm

## 1. SJF without arrival time (non-preemptive)
Kode program : [SJF Scheduling Algorithm Without Arrival Time](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm%20Without%20Arrival%20Time.c)  

![SJF whitout](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SJF%20without%20arrival%20time.png)  

### Bagan Gantt Penjadwalan SJF (Shortest Job First)

### Informasi Proses
| Proses | Waktu Burst | Waktu Selesai | Waktu Tunggu Total | Waktu Tunggu |
|--------|-------------|---------------|-------------------|--------------|
| P3     | 2           | 2             | 2                 | 0            |
| P4     | 3           | 5             | 5                 | 2            |
| P1     | 5           | 10            | 10                | 5            |
| P2     | 7           | 17            | 17                | 10           |

### Perhitungan Detail

### Urutan eksekusi berdasarkan waktu burst terpendek:
- P3 (2) → P4 (3) → P1 (5) → P2 (7)

### Perhitungan Waktu Selesai (Completion Time/CT):
- CT(P3) = 0 + 2 = 2
- CT(P4) = CT(P3) + Burst(P4) = 2 + 3 = 5
- CT(P1) = CT(P4) + Burst(P1) = 5 + 5 = 10
- CT(P2) = CT(P1) + Burst(P2) = 10 + 7 = 17

### Perhitungan Waktu Tunggu Total (Turnaround Time/TAT):
- TAT(P3) = CT(P3) = 2
- TAT(P4) = CT(P4) = 5
- TAT(P1) = CT(P1) = 10
- TAT(P2) = CT(P2) = 17

### Perhitungan Waktu Tunggu (Waiting Time/WT):
- WT(P3) = TAT(P3) - Burst(P3) = 2 - 2 = 0
- WT(P4) = TAT(P4) - Burst(P4) = 5 - 3 = 2
- WT(P1) = TAT(P1) - Burst(P1) = 10 - 5 = 5
- WT(P2) = TAT(P2) - Burst(P2) = 17 - 7 = 10

### Perhitungan Rata-rata:
- Rata-rata Waktu Tunggu Total = (2 + 5 + 10 + 17) / 4 = 34 / 4 = 8,5
- Rata-rata Waktu Tunggu = (0 + 2 + 5 + 10) / 4 = 17 / 4 = 4,25

### Bagan Gantt
```
 0       2       5       10      17
 |---P3--|---P4--|---P1--|---P2--|
```

### Urutan Eksekusi
1. Proses P3 (Waktu Burst: 2) - Dieksekusi dari waktu 0 hingga 2
2. Proses P4 (Waktu Burst: 3) - Dieksekusi dari waktu 2 hingga 5
3. Proses P1 (Waktu Burst: 5) - Dieksekusi dari waktu 5 hingga 10
4. Proses P2 (Waktu Burst: 7) - Dieksekusi dari waktu 10 hingga 17

### Implementasi Algoritma SJF (Shortest Job First)
1. Urutkan semua proses berdasarkan waktu burst (dari terkecil ke terbesar)
2. Proses dengan waktu burst terkecil akan dieksekusi terlebih dahulu
3. Jika terdapat proses dengan waktu burst yang sama, gunakan urutan kedatangan (FCFS)
4. Setiap proses akan dieksekusi hingga selesai tanpa interupsi (non-preemptive)

### Analisis
- Algoritma SJF memilih proses berdasarkan urutan waktu burst (terpendek lebih dulu)
- Proses P3 memiliki waktu burst terpendek (2), sehingga dieksekusi pertama
- Proses P4 memiliki waktu burst terpendek berikutnya (3), sehingga dieksekusi kedua
- Proses P1 memiliki waktu burst terpanjang kedua (5), sehingga dieksekusi ketiga
- Proses P2 memiliki waktu burst terpanjang (7), sehingga dieksekusi terakhir
- Total waktu eksekusi adalah 17 unit waktu
- Implementasi SJF non-preemptive ini meminimalkan rata-rata waktu tunggu dibandingkan dengan FCFS

## 2. SJF with arrival time (non-prremptive)
Kode program : [SJF Scheduling Algorithm](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm.c)  

![SJF with arrival time (non-prremptive)](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SJF%20with%20arrival%20time.png)  
### Bagan Gantt Penjadwalan SJF (Shortest Job First) dengan Waktu Kedatangan

### Informasi Proses
| Proses | Waktu Kedatangan | Waktu Burst | Waktu Selesai | Waktu Tunggu Total | Waktu Tunggu |
|--------|------------------|-------------|---------------|-------------------|--------------|
| P1     | 0                | 5           | 5             | 5                 | 0            |
| P2     | 1                | 7           | 17            | 16                | 9            |
| P3     | 2                | 2           | 7             | 5                 | 3            |
| P4     | 3                | 3           | 10            | 7                 | 4            |

### Perhitungan Detail

### Urutan proses berdasarkan waktu kedatangan dan waktu burst:
1. T=0: Hanya P1 tersedia, maka P1 dieksekusi.
2. T=5: P2 dan P3 telah tiba. P3 memiliki waktu burst lebih pendek (2 vs 7), maka P3 dieksekusi.
3. T=7: P2 dan P4 telah tiba. P4 memiliki waktu burst lebih pendek (3 vs 7), maka P4 dieksekusi.
4. T=10: Hanya P2 tersisa, maka P2 dieksekusi.

### Perhitungan Waktu Selesai (Completion Time/CT):
- CT(P1) = 0 + 5 = 5
- CT(P3) = 5 + 2 = 7
- CT(P4) = 7 + 3 = 10
- CT(P2) = 10 + 7 = 17

### Perhitungan Waktu Tunggu Total (Turnaround Time/TAT):
- TAT(P1) = CT(P1) - AT(P1) = 5 - 0 = 5
- TAT(P3) = CT(P3) - AT(P3) = 7 - 2 = 5
- TAT(P4) = CT(P4) - AT(P4) = 10 - 3 = 7
- TAT(P2) = CT(P2) - AT(P2) = 17 - 1 = 16

### Perhitungan Waktu Tunggu (Waiting Time/WT):
- WT(P1) = TAT(P1) - BT(P1) = 5 - 5 = 0
- WT(P3) = TAT(P3) - BT(P3) = 5 - 2 = 3
- WT(P4) = TAT(P4) - BT(P4) = 7 - 3 = 4
- WT(P2) = TAT(P2) - BT(P2) = 16 - 7 = 9

### Perhitungan Response Time (RT):
- RT(P1) = 0 (langsung dieksekusi pada kedatangan)
- RT(P3) = 5 - 2 = 3 (mulai dieksekusi pada T=5, tiba pada T=2)
- RT(P4) = 7 - 3 = 4 (mulai dieksekusi pada T=7, tiba pada T=3)
- RT(P2) = 10 - 1 = 9 (mulai dieksekusi pada T=10, tiba pada T=1)

### Perhitungan Rata-rata:
- Rata-rata Waktu Tunggu Total = (5 + 16 + 5 + 7) / 4 = 33 / 4 = 8,25
- Rata-rata Waktu Tunggu = (0 + 9 + 3 + 4) / 4 = 16 / 4 = 4

### Bagan Gantt
```
 0       5       7       10              17
 |---P1--|---P3--|---P4--|------P2------|
```

### Urutan Eksekusi
1. Proses P1 (Waktu Kedatangan: 0, Waktu Burst: 5) - Dieksekusi dari waktu 0 hingga 5
2. Proses P3 (Waktu Kedatangan: 2, Waktu Burst: 2) - Dieksekusi dari waktu 5 hingga 7
3. Proses P4 (Waktu Kedatangan: 3, Waktu Burst: 3) - Dieksekusi dari waktu 7 hingga 10
4. Proses P2 (Waktu Kedatangan: 1, Waktu Burst: 7) - Dieksekusi dari waktu 10 hingga 17

### Implementasi Algoritma SJF (Shortest Job First) dengan Waktu Kedatangan
1. Pada waktu t = 0, eksekusi proses yang sudah tiba dengan waktu burst terkecil
2. Setelah proses selesai dieksekusi, pilih di antara proses yang sudah tiba (pada waktu itu) dengan waktu burst terkecil
3. Jika tidak ada proses yang tersedia, tunggu hingga proses berikutnya tiba
4. Jika terdapat proses dengan waktu burst yang sama, prioritaskan yang memiliki waktu kedatangan lebih awal
5. Setiap proses akan dieksekusi hingga selesai tanpa interupsi (non-preemptive)

### Analisis
- Pada waktu 0, hanya P1 yang tersedia, sehingga P1 dieksekusi terlebih dahulu
- Setelah P1 selesai pada waktu 5, P2 dan P3 sudah tiba (P2 tiba pada t=1, P3 tiba pada t=2)
- Di antara P2 dan P3, P3 memiliki waktu burst lebih kecil (2 < 7), sehingga P3 dieksekusi setelah P1
- Setelah P3 selesai pada waktu 7, P2 dan P4 sudah tiba (P4 tiba pada t=3)
- Di antara P2 dan P4, P4 memiliki waktu burst lebih kecil (3 < 7), sehingga P4 dieksekusi setelah P3
- Setelah P4 selesai pada waktu 10, hanya tersisa P2, sehingga P2 dieksekusi terakhir
- Total waktu eksekusi adalah 17 unit waktu
- Algoritma SJF non-preemptive dengan waktu kedatangan ini menghasilkan rata-rata waktu tunggu total 8,25 dan rata-rata waktu tunggu 4

## 3. SRTF (preemptive)
Kode program : [SRTF Scheduling Algorithm](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SRTF%20Scheduling%20Algorithm.c)  

![SRTF](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SRTF.png)

### Bagan Gantt Penjadwalan SRTF (Shortest Remaining Time First) dengan Waktu Kedatangan

### Informasi Proses
| Proses | Waktu Kedatangan | Waktu Burst | Waktu Selesai | Waktu Tunggu Total | Waktu Tunggu |
|--------|------------------|-------------|---------------|-------------------|--------------|
| P1     | 0                | 5           | 7             | 7                 | 2            |
| P2     | 1                | 7           | 17            | 16                | 9            |
| P3     | 2                | 2           | 4             | 2                 | 0            |
| P4     | 3                | 3           | 10            | 7                 | 4            |

### Perhitungan Detail

### Urutan eksekusi berdasarkan waktu sisa terkecil:
1. T=0: Hanya P1 tersedia, P1 dieksekusi.
2. T=1: P1 dan P2 tersedia. P1 memiliki sisa waktu 4, P2 memiliki waktu burst 7. P1 tetap dieksekusi.
3. T=2: P1, P2, dan P3 tersedia. P1 memiliki sisa waktu 3, P2 memiliki waktu burst 7, P3 memiliki waktu burst 2. P3 memiliki sisa waktu terkecil, sehingga P1 di-preempt dan P3 dieksekusi.
4. T=4: P3 selesai. P1 memiliki sisa waktu 3, P2 memiliki waktu burst 7, P4 memiliki waktu burst 3. P1 dan P4 memiliki sisa waktu yang sama, tetapi P1 datang lebih dulu, sehingga P1 dieksekusi.
5. T=7: P1 selesai. P2 memiliki sisa waktu 7, P4 memiliki sisa waktu 3. P4 dieksekusi.
6. T=10: P4 selesai. Hanya P2 tersisa dengan sisa waktu 7, sehingga P2 dieksekusi.
7. T=17: P2 selesai. Semua proses telah selesai dieksekusi.

### Perhitungan Waktu Selesai (Completion Time/CT):
- CT(P3) = 4 (selesai pada t=4)
- CT(P1) = 7 (selesai pada t=7)
- CT(P4) = 10 (selesai pada t=10)
- CT(P2) = 17 (selesai pada t=17)

### Perhitungan Waktu Tunggu Total (Turnaround Time/TAT):
- TAT(P3) = CT(P3) - AT(P3) = 4 - 2 = 2
- TAT(P1) = CT(P1) - AT(P1) = 7 - 0 = 7
- TAT(P4) = CT(P4) - AT(P4) = 10 - 3 = 7
- TAT(P2) = CT(P2) - AT(P2) = 17 - 1 = 16

### Perhitungan Waktu Tunggu (Waiting Time/WT):
- WT(P3) = TAT(P3) - BT(P3) = 2 - 2 = 0
- WT(P1) = TAT(P1) - BT(P1) = 7 - 5 = 2
- WT(P4) = TAT(P4) - BT(P4) = 7 - 3 = 4
- WT(P2) = TAT(P2) - BT(P2) = 16 - 7 = 9

### Perhitungan Rata-rata:
- Rata-rata Waktu Tunggu Total = (7 + 16 + 2 + 7) / 4 = 32 / 4 = 8
- Rata-rata Waktu Tunggu = (2 + 9 + 0 + 4) / 4 = 15 / 4 = 3,75

### Bagan Gantt
```
 0    1    2    3    4    5    6    7    8    9    10                  17
 |--P1--|-P1-|--P3--|-P1-|-P1-|-P1-|-P4-|-P4-|-P4-|--------P2---------|
```

### Bagan Gantt Terperinci
```
Waktu:  | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |10 |11 |12 |13 |14 |15 |16 |17 |
Proses: | P1  | P1  | P3  | P3  | P1  | P1  | P1  | P4  | P4  | P4  | P2  | P2  | P2  | P2  | P2  | P2  | P2  |
```

### Urutan Eksekusi (Dengan Preemption)
1. Proses P1 (Waktu Kedatangan: 0, Waktu Burst: 5) - Dieksekusi dari waktu 0 hingga 2 (2 unit)
2. Proses P3 (Waktu Kedatangan: 2, Waktu Burst: 2) - Dieksekusi dari waktu 2 hingga 4 (2 unit)
3. Proses P1 (Waktu Kedatangan: 0, Waktu Burst: 5) - Melanjutkan eksekusi dari waktu 4 hingga 7 (3 unit)
4. Proses P4 (Waktu Kedatangan: 3, Waktu Burst: 3) - Dieksekusi dari waktu 7 hingga 10 (3 unit)
5. Proses P2 (Waktu Kedatangan: 1, Waktu Burst: 7) - Dieksekusi dari waktu 10 hingga 17 (7 unit)

### Implementasi Algoritma SRTF (Shortest Remaining Time First)
1. Setiap kali ada proses baru tiba atau proses saat ini selesai, algoritma memeriksa semua proses yang tersedia
2. Proses dengan waktu sisa terkecil akan dipilih untuk dieksekusi selanjutnya
3. Jika ada proses baru yang tiba dengan waktu burst lebih pendek dari sisa waktu proses yang sedang dieksekusi, proses yang sedang berjalan akan di-preempt (dihentikan sementara)
4. Jika terdapat beberapa proses dengan waktu sisa yang sama, gunakan waktu kedatangan untuk menentukan prioritas (yang datang lebih awal akan dieksekusi terlebih dahulu)

### Analisis
- SRTF adalah versi preemptive dari algoritma SJF
- Proses P1 mulai dieksekusi pada waktu 0 karena hanya itu yang tersedia
- Ketika P3 tiba pada waktu 2, P1 di-preempt karena P3 memiliki waktu burst lebih kecil dari sisa waktu P1 (2 vs 3)
- Setelah P3 selesai pada waktu 4, P1 dilanjutkan karena memiliki sisa waktu terkecil dibandingkan dengan proses lain yang tersedia
- Ketika P1 selesai pada waktu 7, P4 dieksekusi karena memiliki waktu burst lebih kecil dari P2 (3 vs 7)
- Terakhir, P2 dieksekusi karena hanya itu proses yang tersisa
- Algoritma SRTF menghasilkan rata-rata waktu tunggu total 8 dan rata-rata waktu tunggu 3,75, yang lebih baik dibandingkan dengan algoritma non-preemptive
- Meskipun SRTF optimal dalam hal rata-rata waktu tunggu, algoritma ini menghasilkan overhead karena pergantian konteks yang lebih sering
