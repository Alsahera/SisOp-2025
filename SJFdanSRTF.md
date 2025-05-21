# SJF dan SRTF Scheduling Algorithm

## 1. SJF without arrival time (non-preemptive)
Kode program : [SJF Scheduling Algorithm Without Arrival Time](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm%20Without%20Arrival%20Time.c)  

![SJF whitout](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SJF%20without%20arrival%20time.png)

Analisa:  
Program ini dapat mensimulasikan algoritma SJF Non-Preemptive tanpa waktu kedatangan.  Setiap proses memiliki burst time yang berbeda, dan program mengurutkan proses berdasarkan burst time terkecil.  Selain itu, program menghitung waktu penyelesaian (CT), waktu balik (TAT), dan waktu menunggu (WT) untuk setiap proses.  TAT = CT dan WT = TAT - BT karena semua proses dianggap datang bersamaan. Hasilnya ditampilkan dalam tabel bersama dengan rata-rata TAT dan WT untuk mengukur efisiensi penjadwalan.

## 2. SJF with arrival time (non-prremptive)
Kode program : [SJF Scheduling Algorithm](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm.c)  

![SJF with arrival time (non-prremptive)](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SJF%20with%20arrival%20time.png)

Analisa:  
Program ini menggunakan waktu kedatangan untuk mensimulasikan algoritma SJF Non-Preemptive. Setelah pengguna memasukkan waktu kedatangan dan burst time, program mengurutkan proses berdasarkan waktu kedatangan. Proses yang sudah datang dan memiliki burst time terkecil akan dipilih untuk dijalankan tanpa preemption. Program menghitung waktu mulai, selesai, turnaround, dan tunggu untuk setiap proses, dan kemudian menampilkan hasilnya bersama dengan turnaround time rata-rata dan wai.

## 3. SRTF (preemptive)
Kode program : [SRTF Scheduling Algorithm](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SRTF%20Scheduling%20Algorithm.c)  

![SRTF](https://github.com/Alsahera/SisOp-2025/blob/main/gambar/SRTF.png)

Analisa:  
Program ini menggunakan algoritma preemptive Shortest Remaining Time First (SRTF) untuk menghitung waktu eksekusi proses.  Program memilih proses yang sudah datang dan memiliki sisa waktu terpendek setiap satuan waktu. Proses ini dijalankan satu unit waktu, dan jika ada proses baru dengan waktu lebih pendek, proses ini dipilih ulang.

 Untuk mengukur efisiensi penjadwalan, program mencatat waktu selesai (completion time), menghitung turnaround time (CT − AT), dan waktu menunggu (TAT − BT).
