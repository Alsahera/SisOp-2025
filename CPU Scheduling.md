# CPU Scheduling
# 5.17 Consider the following set of processes, with the length of the CPU burst given in milliseconds:  

| Proses | Burst Time | Prioritas |
|--------|------------|-----------|
| P₁     | 5          | 4         |
| P₂     | 3          | 1         |
| P₃     | 1          | 2         |
| P₄     | 7          | 2         |
| P₅     | 4          | 3         |

*Catatan: Semua proses tiba pada waktu 0 dengan urutan P₁, P₂, P₃, P₄, P₅. Prioritas yang lebih tinggi memiliki angka yang lebih besar.*

## a. Gantt Chart untuk Berbagai Algoritma Penjadwalan

### 1. First-Come, First-Served (FCFS)
```
┌────────┬────────┬────────┬────────┬────────┐
│   P₁   │   P₂   │   P₃   │   P₄   │   P₅   │
└────────┴────────┴────────┴────────┴────────┘
0        5        8        9        16       20
```

### 2. Shortest Job First (SJF) non-preemptive
```
┌────────┬────────┬────────┬────────┬────────┐
│   P₃   │   P₂   │   P₅   │   P₁   │   P₄   │
└────────┴────────┴────────┴────────┴────────┘
0        1        4        8        13       20
```

### 3. Non-preemptive Priority (angka prioritas lebih besar = prioritas lebih tinggi)
```
┌────────┬────────┬────────┬────────┬────────┐
│   P₁   │   P₅   │   P₃   │   P₄   │   P₂   │
└────────┴────────┴────────┴────────┴────────┘
0        5        9        10       17       20
```

### 4. Round Robin (quantum = 2)
```
┌────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┐
│   P₁   │   P₂   │   P₃   │   P₄   │   P₅   │   P₁   │   P₂   │   P₄   │   P₅   │   P₄   │
└────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┘
0        2        4        5        7        9        11       12       14       16       20
```

## b. Waktu Turnaround untuk Setiap Proses

Waktu turnaround = waktu selesai - waktu kedatangan

### 1. FCFS
- P₁: 5 - 0 = 5
- P₂: 8 - 0 = 8
- P₃: 9 - 0 = 9
- P₄: 16 - 0 = 16
- P₅: 20 - 0 = 20
- **Rata-rata waktu turnaround: (5 + 8 + 9 + 16 + 20) / 5 = 11.6**

### 2. SJF
- P₁: 13 - 0 = 13
- P₂: 4 - 0 = 4
- P₃: 1 - 0 = 1
- P₄: 20 - 0 = 20
- P₅: 8 - 0 = 8
- **Rata-rata waktu turnaround: (13 + 4 + 1 + 20 + 8) / 5 = 9.2**

### 3. Non-preemptive Priority
- P₁: 5 - 0 = 5
- P₂: 20 - 0 = 20
- P₃: 10 - 0 = 10
- P₄: 17 - 0 = 17
- P₅: 9 - 0 = 9
- **Rata-rata waktu turnaround: (5 + 20 + 10 + 17 + 9) / 5 = 12.2**

### 4. Round Robin (RR)
- P₁: 11 - 0 = 11
- P₂: 12 - 0 = 12
- P₃: 5 - 0 = 5
- P₄: 20 - 0 = 20
- P₅: 16 - 0 = 16
- **Rata-rata waktu turnaround: (11 + 12 + 5 + 20 + 16) / 5 = 12.8**

## c. Waktu Tunggu untuk Setiap Proses

Waktu tunggu = waktu turnaround - burst time

### 1. FCFS
- P₁: 5 - 5 = 0
- P₂: 8 - 3 = 5
- P₃: 9 - 1 = 8
- P₄: 16 - 7 = 9
- P₅: 20 - 4 = 16
- **Rata-rata waktu tunggu: (0 + 5 + 8 + 9 + 16) / 5 = 7.6**

### 2. SJF
- P₁: 13 - 5 = 8
- P₂: 4 - 3 = 1
- P₃: 1 - 1 = 0
- P₄: 20 - 7 = 13
- P₅: 8 - 4 = 4
- **Rata-rata waktu tunggu: (8 + 1 + 0 + 13 + 4) / 5 = 5.2**

### 3. Non-preemptive Priority
- P₁: 5 - 5 = 0
- P₂: 20 - 3 = 17
- P₃: 10 - 1 = 9
- P₄: 17 - 7 = 10
- P₅: 9 - 4 = 5
- **Rata-rata waktu tunggu: (0 + 17 + 9 + 10 + 5) / 5 = 8.2**

### 4. Round Robin (RR)
- P₁: 11 - 5 = 6
- P₂: 12 - 3 = 9
- P₃: 5 - 1 = 4
- P₄: 20 - 7 = 13
- P₅: 16 - 4 = 12
- **Rata-rata waktu tunggu: (6 + 9 + 4 + 13 + 12) / 5 = 8.8**

## d. Algoritma dengan Waktu Tunggu Rata-rata Minimum

Dari hasil perhitungan di atas, algoritma yang menghasilkan waktu tunggu rata-rata minimum adalah:

**Shortest Job First (SJF)** dengan waktu tunggu rata-rata **5.2 ms**

Perbandingan waktu tunggu rata-rata:
1. FCFS: 7.6 ms
2. SJF: 5.2 ms
3. Non-preemptive Priority: 8.2 ms
4. Round Robin: 8.8 ms



# 5.18 The following processes are being scheduled using a preemptive, priority-based, round-robin scheduling algorithm.  

| Proses | Prioritas | Burst Time | Arrival Time |
|--------|-----------|------------|--------------|
| P₁     | 8         | 15         | 0            |
| P₂     | 3         | 20         | 0            |
| P₃     | 4         | 20         | 20           |
| P₄     | 4         | 20         | 25           |
| P₅     | 5         | 5          | 45           |
| P₆     | 5         | 15         | 55           |

## Keterangan Algoritma
- Prioritas lebih tinggi memiliki angka yang lebih tinggi
- Untuk proses dengan prioritas sama, digunakan algoritma round-robin
- Time quantum untuk round-robin adalah 10 unit waktu
- Jika proses dipreempt, ditempatkan di akhir antrian

## Solusi
### a. Urutan Penjadwalan dengan Gantt Chart

```
┌────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┬────────┐
│   P₁   │   P₁   │   P₃   │   P₃   │   P₃   │   P₅   │   P₆   │   P₆   │   P₄   │   P₄   │   P₂   │
└────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┴────────┘
0        10        20        30        40        50        60        70        80        90       100       110
```

### Penjelasan Urutan Eksekusi
1. Pada t=0, proses yang tersedia adalah P₁ (prioritas 8) dan P₂ (prioritas 3). P₁ memiliki prioritas tertinggi dan akan dieksekusi.
2. P₁ dieksekusi selama time quantum 10, burst time P₁ berkurang menjadi 5.
3. Pada t=10, proses yang tersedia: P₁ (burst=5) dan P₂ (burst=20). P₁ masih memiliki prioritas tertinggi dan melanjutkan eksekusi.
4. P₁ menyelesaikan sisa burstnya (5), dan selesai pada t=15.
5. Pada t=15, hanya ada P₂ yang tersedia, sehingga P₂ mulai dieksekusi.
6. Pada t=20, P₃ tiba dengan prioritas 4 yang lebih tinggi dari P₂ (prioritas 3). P₂ dipreempt, dan P₃ mulai dieksekusi.
7. P₃ dieksekusi selama time quantum 10, burst time P₃ berkurang menjadi 10.
8. Pada t=25, P₄ tiba dengan prioritas 4 (sama dengan P₃). P₃ melanjutkan eksekusi karena masih dalam time quantum pertamanya.
9. Pada t=30, P₃ telah menggunakan 1 time quantum. Dalam antrian ada P₃ (burst=10, prioritas 4), P₄ (burst=20, prioritas 4), dan P₂ (burst=15, prioritas 3). Karena P₃ dan P₄ memiliki prioritas tertinggi dan sama, round-robin diterapkan, dan P₃ melanjutkan eksekusi (karena sudah dalam antrian).
10. P₃ melanjutkan eksekusi selama time quantum 10 dan selesai pada t=40.
11. Pada t=40, dalam antrian ada P₄ (prioritas 4) dan P₂ (prioritas 3). P₄ memiliki prioritas lebih tinggi sehingga dieksekusi.
12. Pada t=45, P₅ tiba dengan prioritas 5 yang lebih tinggi dari P₄ (prioritas 4). P₄ dipreempt, dan P₅ mulai dieksekusi.
13. P₅ memiliki burst time 5, sehingga selesai pada t=50.
14. Pada t=50, proses yang tersedia adalah P₄ (burst=20, prioritas 4) dan P₂ (burst=15, prioritas 3). P₄ memiliki prioritas lebih tinggi.
15. Pada t=55, P₆ tiba dengan prioritas 5 yang lebih tinggi dari P₄ (prioritas 4). P₄ dipreempt, dan P₆ mulai dieksekusi.
16. P₆ dieksekusi selama time quantum 10, burst time P₆ berkurang menjadi 5.
17. Pada t=65, P₆ melanjutkan eksekusi untuk sisa burstnya (5), dan selesai pada t=70.
18. Pada t=70, tersisa P₄ (prioritas 4) dan P₂ (prioritas 3). P₄ memiliki prioritas lebih tinggi dan dieksekusi.
19. P₄ dieksekusi selama time quantum 10, burst time P₄ berkurang menjadi 10.
20. Pada t=80, P₄ melanjutkan eksekusi untuk time quantum kedua dan selesai pada t=90.
21. Terakhir, P₂ dieksekusi hingga selesai pada t=110.

### b. Waktu Turnaround untuk Setiap Proses

Waktu turnaround = waktu selesai - waktu kedatangan

1. P₁: 15 - 0 = 15
2. P₂: 110 - 0 = 110
3. P₃: 40 - 20 = 20
4. P₄: 90 - 25 = 65
5. P₅: 50 - 45 = 5
6. P₆: 70 - 55 = 15

### c. Waktu Tunggu untuk Setiap Proses

Waktu tunggu = waktu turnaround - burst time

1. P₁: 15 - 15 = 0
2. P₂: 110 - 20 = 90
3. P₃: 20 - 20 = 0
4. P₄: 65 - 20 = 45
5. P₅: 5 - 5 = 0
6. P₆: 15 - 15 = 0
