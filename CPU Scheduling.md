# CPU Scheduling
# 5.17  

## Tabel Proses

| Proses | Burst Time (ms) | Prioritas |
|--------|----------------|-----------|
| P₁     | 5              | 4         |
| P₂     | 3              | 1         |
| P₃     | 1              | 2         |
| P₄     | 7              | 2         |
| P₅     | 4              | 3         |

Semua proses diasumsikan tiba pada waktu 0 dengan urutan P₁, P₂, P₃, P₄, P₅.

## a. Diagram Gantt untuk Berbagai Algoritma Penjadwalan

### 1. FCFS (First Come First Serve)

```
 P₁      P₂     P₃    P₄        P₅    
+------+-----+----+---------+------+
|      |     |    |         |      |
+------+-----+----+---------+------+
0      5     8    9         16     20
```

Dengan FCFS, proses dieksekusi sesuai urutan kedatangan tanpa preemption.

### 2. SJF (Shortest Job First)

```
 P₃   P₂     P₅      P₁      P₄       
+----+-----+------+------+---------+
|    |     |      |      |         |
+----+-----+------+------+---------+
0    1     4      8      13        20
```

Dengan SJF, proses dengan burst time terpendek dieksekusi terlebih dahulu.

### 3. Non-preemptive Priority

Catatan: Nilai prioritas yang lebih besar berarti prioritas lebih tinggi.

```
 P₁      P₅      P₃,P₄        P₂    
+------+------+------------+-----+
|      |      |            |     |
+------+------+------------+-----+
0      5      9            17    20
```

Dengan prioritas non-preemptive, proses dengan nilai prioritas tertinggi dieksekusi terlebih dahulu. P₃ dan P₄ memiliki prioritas yang sama (2), tetapi P₃ dieksekusi lebih dulu karena tiba lebih awal.

### 4. RR (Round Robin) dengan quantum = 2

```
 P₁    P₂    P₃    P₄    P₅    P₁    P₂    P₄    P₅    P₄    P₄   
+-----+-----+-----+-----+-----+-----+-----+-----+-----+-----+----+
|     |     |     |     |     |     |     |     |     |     |    |
+-----+-----+-----+-----+-----+-----+-----+-----+-----+-----+----+
0     2     4     5     7     9     11    12    14    16    18   20
```

Dengan Round Robin (quantum = 2), setiap proses mendapatkan jatah waktu CPU maksimal 2 ms secara bergiliran.

## b. Waktu Turnaround untuk Setiap Proses

Waktu turnaround = Waktu selesai - Waktu kedatangan

### FCFS
- P₁: 5 - 0 = 5 ms
- P₂: 8 - 0 = 8 ms
- P₃: 9 - 0 = 9 ms
- P₄: 16 - 0 = 16 ms
- P₅: 20 - 0 = 20 ms

### SJF
- P₁: 13 - 0 = 13 ms
- P₂: 4 - 0 = 4 ms
- P₃: 1 - 0 = 1 ms
- P₄: 20 - 0 = 20 ms
- P₅: 8 - 0 = 8 ms

### Non-preemptive Priority
- P₁: 5 - 0 = 5 ms
- P₂: 20 - 0 = 20 ms
- P₃: 10 - 0 = 10 ms
- P₄: 17 - 0 = 17 ms
- P₅: 9 - 0 = 9 ms

### Round Robin (quantum = 2)
- P₁: 11 - 0 = 11 ms
- P₂: 12 - 0 = 12 ms
- P₃: 5 - 0 = 5 ms
- P₄: 20 - 0 = 20 ms
- P₅: 16 - 0 = 16 ms

## c. Waktu Tunggu untuk Setiap Proses

Waktu tunggu = Waktu turnaround - Burst time

### FCFS
- P₁: 5 - 5 = 0 ms
- P₂: 8 - 3 = 5 ms
- P₃: 9 - 1 = 8 ms
- P₄: 16 - 7 = 9 ms
- P₅: 20 - 4 = 16 ms

### SJF
- P₁: 13 - 5 = 8 ms
- P₂: 4 - 3 = 1 ms
- P₃: 1 - 1 = 0 ms
- P₄: 20 - 7 = 13 ms
- P₅: 8 - 4 = 4 ms

### Non-preemptive Priority
- P₁: 5 - 5 = 0 ms
- P₂: 20 - 3 = 17 ms
- P₃: 10 - 1 = 9 ms
- P₄: 17 - 7 = 10 ms
- P₅: 9 - 4 = 5 ms

### Round Robin (quantum = 2)
- P₁: 11 - 5 = 6 ms
- P₂: 12 - 3 = 9 ms
- P₃: 5 - 1 = 4 ms
- P₄: 20 - 7 = 13 ms
- P₅: 16 - 4 = 12 ms

## d. Algoritma dengan Rata-rata Waktu Tunggu Minimum

Rata-rata waktu tunggu untuk setiap algoritma:

### FCFS
(0 + 5 + 8 + 9 + 16) / 5 = 38 / 5 = 7,6 ms

### SJF
(8 + 1 + 0 + 13 + 4) / 5 = 26 / 5 = 5,2 ms

### Non-preemptive Priority
(0 + 17 + 9 + 10 + 5) / 5 = 41 / 5 = 8,2 ms

### Round Robin (quantum = 2)
(6 + 9 + 4 + 13 + 12) / 5 = 44 / 5 = 8,8 ms

Berdasarkan perhitungan di atas, algoritma **SJF (Shortest Job First)** menghasilkan rata-rata waktu tunggu minimum sebesar 5,2 ms.



# 5.18  

## Tabel Proses

| Proses | Prioritas | Burst Time | Arrival Time |
|--------|-----------|------------|-------------|
| P₁     | 8         | 15         | 0           |
| P₂     | 3         | 20         | 0           |
| P₃     | 4         | 20         | 20          |
| P₄     | 4         | 20         | 25          |
| P₅     | 5         | 5          | 45          |
| P₆     | 5         | 15         | 55          |

Catatan:
- Nilai prioritas lebih tinggi berarti prioritas lebih tinggi
- Quantum = 10 unit waktu
- Untuk proses dengan prioritas sama, digunakan algoritma Round Robin
- Jika proses dipreempt, proses tersebut diletakkan di akhir antrian

## a. Diagram Gantt untuk Algoritma Penjadwalan Preemptive Priority Round-Robin

Berikut adalah eksekusi berdasarkan waktu:

- t=0: P₁ (prioritas 8) dan P₂ (prioritas 3) tiba. P₁ dieksekusi karena memiliki prioritas tertinggi.
- t=10: P₁ telah berjalan selama 10 unit (quantum). Sisa burst time P₁ = 5. Tidak ada proses lain dengan prioritas lebih tinggi, jadi P₁ melanjutkan eksekusi.
- t=15: P₁ selesai. P₂ (prioritas 3) dieksekusi.
- t=20: P₃ (prioritas 4) tiba. Karena P₃ memiliki prioritas lebih tinggi dari P₂, P₂ dipreempt dan P₃ dieksekusi. Sisa burst time P₂ = 15.
- t=25: P₄ (prioritas 4) tiba. P₃ sudah berjalan selama 5 unit. Karena P₃ dan P₄ memiliki prioritas sama (4), mereka akan dijadwalkan secara Round Robin.
- t=30: P₃ telah berjalan selama 10 unit (quantum). P₄ mulai dieksekusi. Sisa burst time P₃ = 10.
- t=40: P₄ telah berjalan selama 10 unit (quantum). P₃ melanjutkan eksekusi. Sisa burst time P₄ = 10.
- t=45: P₅ (prioritas 5) tiba. Karena P₅ memiliki prioritas lebih tinggi dari P₃, P₃ dipreempt dan P₅ dieksekusi. Sisa burst time P₃ = 5.
- t=50: P₅ selesai. P₃ melanjutkan eksekusi.
- t=55: P₆ (prioritas 5) tiba. P₃ telah berjalan selama 5 unit sejak dipreempt terakhir kali. Karena P₆ memiliki prioritas lebih tinggi dari P₃, P₃ dipreempt dan P₆ dieksekusi. Sisa burst time P₃ = 0.
- t=65: P₆ telah berjalan selama 10 unit (quantum). Sisa burst time P₆ = 5.
- t=70: P₆ selesai. P₄ melanjutkan eksekusi. Sisa burst time P₄ = 0.
- t=80: P₄ selesai. P₂ melanjutkan eksekusi.
- t=95: P₂ selesai.

Berikut diagram Gantt yang menggambarkan penjadwalan:

```
      P₁           P₂      P₃     P₄     P₃  P₅  P₃    P₆     P₄      P₂     
+-------------+------+----------+------+----+---+----+------+------+--------+
|             |      |          |      |    |   |    |      |      |        |
+-------------+------+----------+------+----+---+----+------+------+--------+
0            15     20         30     40   45  50   55     70     80       95
```

## b. Waktu Turnaround untuk Setiap Proses

Waktu turnaround = Waktu selesai - Waktu kedatangan

- P₁: 15 - 0 = 15
- P₂: 95 - 0 = 95
- P₃: 55 - 20 = 35
- P₄: 80 - 25 = 55
- P₅: 50 - 45 = 5
- P₆: 70 - 55 = 15

## c. Waktu Tunggu untuk Setiap Proses

Waktu tunggu = Waktu turnaround - Burst time

- P₁: 15 - 15 = 0
- P₂: 95 - 20 = 75
- P₃: 35 - 20 = 15
- P₄: 55 - 20 = 35
- P₅: 5 - 5 = 0
- P₆: 15 - 15 = 0

## Ringkasan

| Proses | Turnaround Time | Waiting Time |
|--------|----------------|-------------|
| P₁     | 15             | 0           |
| P₂     | 95             | 75          |
| P₃     | 35             | 15          |
| P₄     | 55             | 35          |
| P₅     | 5              | 0           |
| P₆     | 15             | 0           |

Rata-rata Turnaround Time = (15 + 95 + 35 + 55 + 5 + 15) / 6 = 220 / 6 = 36,67

Rata-rata Waiting Time = (0 + 75 + 15 + 35 + 0 + 0) / 6 = 125 / 6 = 20,83
