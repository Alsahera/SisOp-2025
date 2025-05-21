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

Analisa:  
Program ini menggunakan algoritma preemptive Shortest Remaining Time First (SRTF) untuk menghitung waktu eksekusi proses.  Program memilih proses yang sudah datang dan memiliki sisa waktu terpendek setiap satuan waktu. Proses ini dijalankan satu unit waktu, dan jika ada proses baru dengan waktu lebih pendek, proses ini dipilih ulang.

 Untuk mengukur efisiensi penjadwalan, program mencatat waktu selesai (completion time), menghitung turnaround time (CT − AT), dan waktu menunggu (TAT − BT).
