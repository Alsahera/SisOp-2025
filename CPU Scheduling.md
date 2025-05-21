## b. Waktu Turnaround untuk Setiap Proses

Waktu turnaround adalah waktu total yang dibutuhkan proses dari kedatangan hingga selesai eksekusi.
Waktu turnaround = Waktu selesai - Waktu kedatangan

### 1. FCFS (First Come First Served)

| Proses | Waktu Kedatangan | Waktu Selesai | Waktu Turnaround |
|--------|-----------------|---------------|------------------|
| P₁     | 0               | 5             | 5                |
| P₂     | 0               | 8             | 8                |
| P₃     | 0               | 9             | 9                |
| P₄     | 0               | 16            | 16               |
| P₅     | 0               | 20            | 20               |

Rata-rata waktu turnaround FCFS = (5 + 8 + 9 + 16 + 20) / 5 = 58 / 5 = **11,6 ms**

### 2. SJF (Shortest Job First)

| Proses | Waktu Kedatangan | Waktu Selesai | Waktu Turnaround |
|--------|-----------------|---------------|------------------|
| P₁     | 0               | 13            | 13               |
| P₂     | 0               | 4             | 4                |
| P₃     | 0               | 1             | 1                |
| P₄     | 0               | 20            | 20               |
| P₅     | 0               | 8             | 8                |

Rata-rata waktu turnaround SJF = (13 + 4 + 1 + 20 + 8) / 5 = 46 / 5 = **9,2 ms**

### 3. Non-preemptive Priority

| Proses | Waktu Kedatangan | Waktu Selesai | Waktu Turnaround |
|--------|-----------------|---------------|------------------|
| P₁     | 0               | 20            | 20               |
| P₂     | 0               | 3             | 3                |
| P₃     | 0               | 4             | 4                |
| P₄     | 0               | 11            | 11               |
| P₅     | 0               | 15            | 15               |

Rata-rata waktu turnaround Priority = (20 + 3 + 4 + 11 + 15) / 5 = 53 / 5 = **10,6 ms**

### 4. Round Robin (quantum = 2)

| Proses | Waktu Kedatangan | Waktu Selesai | Waktu Turnaround |
|--------|-----------------|---------------|------------------|
| P₁     | 0               | 17            | 17               |
| P₂     | 0               | 12            | 12               |
| P₃     | 0               | 5             | 5                |
| P₄     | 0               | 20            | 20               |
| P₅     | 0               | 16            | 16               |

Rata-rata waktu turnaround RR = (17 + 12 + 5 + 20 + 16) / 5 = 70 / 5 = **14 ms**

## c. Waktu Tunggu untuk Setiap Proses

Waktu tunggu adalah total waktu proses menunggu di ready queue.
Waktu tunggu = Waktu turnaround - Waktu CPU burst

### 1. FCFS (First Come First Served)

| Proses | Waktu Turnaround | Waktu Burst | Waktu Tunggu |
|--------|-----------------|-------------|--------------|
| P₁     | 5               | 5           | 0            |
| P₂     | 8               | 3           | 5            |
| P₃     | 9               | 1           | 8            |
| P₄     | 16              | 7           | 9            |
| P₅     | 20              | 4           | 16           |

Rata-rata waktu tunggu FCFS = (0 + 5 + 8 + 9 + 16) / 5 = 38 / 5 = **7,6 ms**

### 2. SJF (Shortest Job First)

| Proses | Waktu Turnaround | Waktu Burst | Waktu Tunggu |
|--------|-----------------|-------------|--------------|
| P₁     | 13              | 5           | 8            |
| P₂     | 4               | 3           | 1            |
| P₃     | 1               | 1           | 0            |
| P₄     | 20              | 7           | 13           |
| P₅     | 8               | 4           | 4            |

Rata-rata waktu tunggu SJF = (8 + 1 + 0 + 13 + 4) / 5 = 26 / 5 = **5,2 ms**

### 3. Non-preemptive Priority

| Proses | Waktu Turnaround | Waktu Burst | Waktu Tunggu |
|--------|-----------------|-------------|--------------|
| P₁     | 20              | 5           | 15           |
| P₂     | 3               | 3           | 0            |
| P₃     | 4               | 1           | 3            |
| P₄     | 11              | 7           | 4            |
| P₅     | 15              | 4           | 11           |

Rata-rata waktu tunggu Priority = (15 + 0 + 3 + 4 + 11) / 5 = 33 / 5 = **6,6 ms**

### 4. Round Robin (quantum = 2)

| Proses | Waktu Turnaround | Waktu Burst | Waktu Tunggu |
|--------|-----------------|-------------|--------------|
| P₁     | 17              | 5           | 12           |
| P₂     | 12              | 3           | 9            |
| P₃     | 5               | 1           | 4            |
| P₄     | 20              | 7           | 13           |
| P₅     | 16              | 4           | 12           |

Rata-rata waktu tunggu RR = (12 + 9 + 4 + 13 + 12) / 5 = 50 / 5 = **10 ms**

## d. Algoritma dengan Waktu Tunggu Rata-rata Minimum

Berdasarkan perhitungan di atas, algoritma dengan waktu tunggu rata-rata minimum adalah:

**SJF (Shortest Job First)** dengan waktu tunggu rata-rata **5,2 ms**

Perbandingan semua algoritma (dari terbaik ke terburuk berdasarkan waktu tunggu rata-rata):
1. SJF: 5,2 ms
2. Non-preemptive Priority: 6,6 ms
3. FCFS: 7,6 ms
4. Round Robin: 10 ms
