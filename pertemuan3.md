# Flowchart: Proses Menyalakan PC Sampai Siap Digunakan
![flowchart](https://github.com/Alsahera/SisOp-2025/blob/main/flowchart.png)
## Start
Proses dimulai saat pengguna menyalakan komputer.

---

## 1. Tekan Tombol Power
Pengguna menekan tombol power untuk memulai aliran listrik ke sistem.

---

## 2. Power Supply Menyala
Power Supply Unit (PSU) mengalirkan listrik ke semua komponen utama seperti motherboard, CPU, RAM, dan lainnya.

---

## 3. POST (Power-On Self-Test) oleh BIOS/UEFI
BIOS/UEFI melakukan pengecekan awal terhadap perangkat keras:
-  Jika berhasil → lanjut
-  Jika gagal → tampilkan pesan error / beep code

---

## 4. Inisialisasi Perangkat Keras
Perangkat keras utama dikenali dan disiapkan:
- RAM
- Keyboard, mouse
- Harddisk / SSD
- GPU / VGA

---

## 5. Cari dan Muat Bootloader
BIOS/UEFI mencari media boot dan memuat **bootloader** dari penyimpanan (HDD/SSD/USB).

---

## 6. Bootloader Memuat Sistem Operasi
Bootloader memuat sistem operasi (Windows, Linux, dll) ke dalam memori.

---

## 7. Sistem Operasi Melakukan Inisialisasi
OS melakukan proses inisialisasi lanjutan:
- Memuat driver perangkat
- Menjalankan layanan background
- Menyiapkan tampilan antarmuka

---

## 8. Menampilkan Layar Login / Desktop
Sistem menampilkan tampilan awal:
- Login screen (jika aktif)
- Langsung ke desktop (jika auto-login)

---

## 9. Pengguna Siap Menggunakan Komputer
Pengguna kini dapat menjalankan aplikasi, menjelajah internet, atau bekerja.

---

## End
Komputer dalam kondisi siap digunakan.

---
