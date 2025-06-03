# Analisis Algoritma Penjadwalan CPU

## Informasi Proses

| Proses | Waktu Burst (ms) | Prioritas | Waktu Kedatangan |
|--------|------------------|-----------|------------------|
| P₁     | 2                | 2         | 0                |
| P₂     | 1                | 1         | 0                |
| P₃     | 8                | 4         | 0                |
| P₄     | 4                | 2         | 0                |
| P₅     | 5                | 3         | 0                |

## 1. First Come First Serve (FCFS)

**Urutan Eksekusi:** P₁ → P₂ → P₃ → P₄ → P₅

### Diagram Gantt:
```
P₁  | P₂ | P₃       | P₄   | P₅    |
0   2   3         11     15      20
```

### Hasil:
| Proses | Waktu Selesai | Waktu Turnaround | Waktu Tunggu |
|--------|---------------|------------------|--------------|
| P₁     | 2             | 2                | 0            |
| P₂     | 3             | 3                | 2            |
| P₃     | 11            | 11               | 3            |
| P₄     | 15            | 15               | 11           |
| P₅     | 20            | 20               | 15           |
| **Rata-rata** | **10.2** | **10.2**      | **6.2**      |

## 2. Shortest Job First (SJF)

**Urutan Eksekusi:** P₂ → P₁ → P₄ → P₅ → P₃

### Diagram Gantt:
```
P₂ | P₁  | P₄   | P₅    | P₃       |
0  1    3     7      12         20
```

### Hasil:
| Proses | Waktu Selesai | Waktu Turnaround | Waktu Tunggu |
|--------|---------------|------------------|--------------|
| P₁     | 3             | 3                | 1            |
| P₂     | 1             | 1                | 0            |
| P₃     | 20            | 20               | 12           |
| P₄     | 7             | 7                | 3            |
| P₅     | 12            | 12               | 7            |
| **Rata-rata** | **8.6** | **8.6**        | **4.6**      |

## 3. Prioritas Non-Preemptive (Angka lebih besar = Prioritas lebih tinggi)

**Urutan Eksekusi:** P₃ → P₅ → P₁ → P₄ → P₂

### Diagram Gantt:
```
P₃       | P₅    | P₁  | P₄   | P₂ |
0        8      13   15     19   20
```

### Hasil:
| Proses | Waktu Selesai | Waktu Turnaround | Waktu Tunggu |
|--------|---------------|------------------|--------------|
| P₁     | 15            | 15               | 13           |
| P₂     | 20            | 20               | 19           |
| P₃     | 8             | 8                | 0            |
| P₄     | 19            | 19               | 15           |
| P₅     | 13            | 13               | 8            |
| **Rata-rata** | **15.0** | **15.0**      | **11.0**     |

## 4. Round Robin (Kuantum = 2)

**Eksekusi mengikuti kuantum waktu 2ms per proses**

### Diagram Gantt:
```
P₁ |P₂|P₃ |P₄ |P₅ |P₃ |P₄ |P₅ |P₃ |P₅|P₃ |
0  2 3  5  7  9 11 13 15 17 1820
```

### Eksekusi Detail:
- **Putaran 1:** P₁(2ms), P₂(1ms), P₃(2ms), P₄(2ms), P₅(2ms)
- **Putaran 2:** P₃(2ms), P₄(2ms), P₅(2ms)  
- **Putaran 3:** P₃(2ms), P₅(1ms)
- **Putaran 4:** P₃(2ms) - selesai

### Hasil:
| Proses | Waktu Selesai | Waktu Turnaround | Waktu Tunggu |
|--------|---------------|------------------|--------------|
| P₁     | 2             | 2                | 0            |
| P₂     | 3             | 3                | 2            |
| P₃     | 20            | 20               | 12           |
| P₄     | 13            | 13               | 9            |
| P₅     | 18            | 18               | 13           |
| **Rata-rata** | **11.2** | **11.2**      | **7.2**      |

## Perbandingan Ringkasan

| Algoritma | Rata-rata Waktu Turnaround | Rata-rata Waktu Tunggu |
|-----------|----------------------------|------------------------|
| FCFS      | 10.2                       | 6.2                    |
| **SJF**   | **8.6**                    | **4.6**                |
| Prioritas | 15.0                       | 11.0                   |
| Round Robin | 11.2                     | 7.2                    |

## Jawaban

### a. Diagram Gantt
Keempat diagram Gantt ditampilkan di atas untuk algoritma penjadwalan FCFS, SJF, Prioritas Non-preemptive, dan Round Robin.

### b. Waktu Turnaround setiap proses
- **FCFS:** P₁=2, P₂=3, P₃=11, P₄=15, P₅=20
- **SJF:** P₁=3, P₂=1, P₃=20, P₄=7, P₅=12  
- **Prioritas:** P₁=15, P₂=20, P₃=8, P₄=19, P₅=13
- **Round Robin:** P₁=2, P₂=3, P₃=20, P₄=13, P₅=18

### c. Waktu Tunggu setiap proses
- **FCFS:** P₁=0, P₂=2, P₃=3, P₄=11, P₅=15
- **SJF:** P₁=1, P₂=0, P₃=12, P₄=3, P₅=7
- **Prioritas:** P₁=13, P₂=19, P₃=0, P₄=15, P₅=8  
- **Round Robin:** P₁=0, P₂=2, P₃=12, P₄=9, P₅=13

### d. Algoritma dengan rata-rata waktu tunggu minimum
**SJF (Shortest Job First)** menghasilkan rata-rata waktu tunggu minimum sebesar **4.6 ms** untuk semua proses.

## Rumus yang Digunakan
- **Waktu Turnaround** = Waktu Selesai - Waktu Kedatangan
- **Waktu Tunggu** = Waktu Turnaround - Waktu Burst
- Karena semua proses datang pada waktu 0: Waktu Turnaround = Waktu Selesai

## Catatan
- Penjadwalan prioritas menggunakan angka yang lebih besar untuk prioritas yang lebih tinggi
- Round Robin menggunakan kuantum 2ms
- Semua proses diasumsikan datang pada waktu 0
- SJF memberikan performa terbaik dalam hal rata-rata waktu tunggu untuk kumpulan proses ini

## Penjelasan Algoritma

### FCFS (First Come First Serve)
Proses dieksekusi berdasarkan urutan kedatangan. Algoritma ini sederhana tetapi dapat menyebabkan convoy effect.

### SJF (Shortest Job First)
Proses dengan waktu burst terpendek dieksekusi terlebih dahulu. Algoritma ini optimal untuk meminimalkan rata-rata waktu tunggu.

### Prioritas Non-Preemptive
Proses dengan prioritas tertinggi dieksekusi terlebih dahulu. Setelah proses dimulai, tidak dapat diinterupsi.

### Round Robin
Setiap proses mendapat jatah waktu yang sama (kuantum). Jika proses belum selesai dalam satu kuantum, akan dilanjutkan pada giliran berikutnya.
