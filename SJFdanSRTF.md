# SJF dan SRTF Scheduling Algorithm

## 1. SJF without arrival time (non-preemptive)
Kode program : [SJF Scheduling Algorithm Without Arrival Time](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm%20Without%20Arrival%20Time.c)  

![SJF whitout](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SJF%20without%20arrival%20time.png)  

### Informasi Proses
| Proses | Burst Time (BT) | 
|--------|-----------------|
| P3     | 2               |
| P4     | 3               | 
| P1     | 5               | 
| P2     | 7               | 

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

### Gantt Chart
```
 0       2       5       10      17
 |---P3--|---P4--|---P1--|---P2--|
```

### Perhitungan Rata-rata:
- Average TurnAroundTime = (2 + 5 + 10 + 17) / 4 = 34 / 4 = 8,5
- Average WaitingTime = (0 + 2 + 5 + 10) / 4 = 17 / 4 = 4,25

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

### Informasi Proses
| Proses | Arrival Time (AT) | Burst Time (BT) |
|--------|-------------------|-----------------|
| P1     | 0                 | 5               |
| P2     | 1                 | 7               |
| P3     | 2                 | 2               |
| P4     | 3                 | 3               |

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
- RT(P1) = 0 (langsung dieksekusi)
- RT(P3) = 5 - 2 = 3 (mulai dieksekusi pada T=5, tiba pada T=2)
- RT(P4) = 7 - 3 = 4 (mulai dieksekusi pada T=7, tiba pada T=3)
- RT(P2) = 10 - 1 = 9 (mulai dieksekusi pada T=10, tiba pada T=1)

### Gantt Chart
```
 0       5       7       10              17
 |---P1--|---P3--|---P4--|------P2------|
```

### Perhitungan Rata-rata:
- Average TurnAroundTime = (5 + 16 + 5 + 7) / 4 = 33 / 4 = 8,25
- Average WaitingTime = (0 + 9 + 3 + 4) / 4 = 16 / 4 = 4

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

### Informasi Proses
| Proses | Arrival Time (AT) | Burst Time (BT) | 
|--------|-------------------|-----------------|
| P1     | 0                 | 5               | 
| P2     | 1                 | 7               | 
| P3     | 2                 | 2               |
| P4     | 3                 | 3               |

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

### Gantt Chart
```
Waktu:  0    1    2    4    7    10                   17
       +----+----+----+----+----+----+----+----+----+----+
       | P1 | P1 | P3 | P3 | P1 | P4 | P4 | P4 | P2 | P2 |
       +----+----+----+----+----+----+----+----+----+----+
```

### Perhitungan Rata-rata:
- Average TurnAroundTime = (7 + 16 + 2 + 7) / 4 = 32 / 4 = 8
- Average WaitingTime = (2 + 9 + 0 + 4) / 4 = 15 / 4 = 3,75

### Analisis
- SRTF adalah versi preemptive dari algoritma SJF
- Proses P1 mulai dieksekusi pada waktu 0 karena hanya itu yang tersedia
- Ketika P3 tiba pada waktu 2, P1 di-preempt karena P3 memiliki waktu burst lebih kecil dari sisa waktu P1 (2 vs 3)
- Setelah P3 selesai pada waktu 4, P1 dilanjutkan karena memiliki sisa waktu terkecil dibandingkan dengan proses lain yang tersedia
- Ketika P1 selesai pada waktu 7, P4 dieksekusi karena memiliki waktu burst lebih kecil dari P2 (3 vs 7)
- Terakhir, P2 dieksekusi karena hanya itu proses yang tersisa
- Algoritma SRTF menghasilkan rata-rata waktu tunggu total 8 dan rata-rata waktu tunggu 3,75, yang lebih baik dibandingkan dengan algoritma non-preemptive
- Meskipun SRTF optimal dalam hal rata-rata waktu tunggu, algoritma ini menghasilkan overhead karena pergantian konteks yang lebih sering
