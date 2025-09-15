# ☕ Coffee Shop Inventory - Menu Based

## 1. Product Requirement Document (PRD)
### Latar Belakang
Coffee shop sering mengalami kesulitan dalam mengontrol stok bahan baku karena perhitungan manual dan tidak terintegrasi dengan penjualan menu. Sistem ini hadir untuk menghubungkan menu yang terjual dengan stok bahan secara otomatis.

### Tujuan Produk
- Mengurangi human error dalam pencatatan stok.
- Memberikan laporan bahan baku yang akurat.
- Membantu rekomendasi restock berdasarkan penggunaan bahan.

### Target Pengguna
- **Admin/Owner Coffee Shop**: mengelola resep, bahan baku, dan laporan.
- **Kasir**: melakukan input transaksi penjualan menu.

### Fitur Utama
1. Input resep menu (contoh: Cappuccino = 18gr kopi + 120ml susu).
2. Transaksi penjualan → stok otomatis berkurang sesuai resep.
3. Laporan bahan paling banyak dipakai & rekomendasi restock.

---

## 2. Software Requirement Specification (SRS)
### Functional Requirements
- FR1: Sistem dapat menyimpan data bahan baku (nama, satuan, stok).
- FR2: Sistem dapat menyimpan data menu beserta resep bahan bakunya.
- FR3: Sistem dapat mencatat transaksi penjualan menu.
- FR4: Sistem mengurangi stok bahan baku secara otomatis berdasarkan menu yang dijual.
- FR5: Sistem dapat menampilkan laporan stok bahan baku.
- FR6: Sistem dapat memberikan rekomendasi bahan yang perlu direstock.

### Non-Functional Requirements
- NFR1: Sistem berbasis web/mobile dengan UI sederhana.
- NFR2: Database harus konsisten (ACID compliant).
- NFR3: Respon sistem untuk transaksi ≤ 2 detik.

---

## 3. Entity Relationship Diagram (ERD)
### Tabel Utama
- **BahanBaku**(id_bahan, nama_bahan, satuan, stok)
- **Menu**(id_menu, nama_menu, harga)
- **Resep**(id_resep, id_menu, id_bahan, jumlah_pakai)
- **Transaksi**(id_transaksi, tanggal, total_harga)
- **DetailTransaksi**(id_detail, id_transaksi, id_menu, jumlah_menu)

Relasi:
- 1 Menu ↔ banyak Resep.
- 1 Bahan ↔ banyak Resep.
- 1 Transaksi ↔ banyak DetailTransaksi.
- 1 Menu ↔ banyak DetailTransaksi.

---

## 4. Software Design Document (SDD)
### Arsitektur Sistem
- **Frontend**: Flutter (Android/iOS & Web).
- **Backend**: Node.js / Express.
- **Database**: MySQL atau PostgreSQL.

### Desain Modul
1. **Modul Manajemen Bahan Baku**
   - Tambah, edit, hapus bahan baku.
2. **Modul Manajemen Menu & Resep**
   - Input menu + bahan baku yang dibutuhkan.
3. **Modul Transaksi**
   - Input penjualan menu.
   - Update stok otomatis.
4. **Modul Laporan**
   - Laporan stok bahan baku.
   - Rekomendasi restock (bahan dengan stok < minimum).

---

## 5. Checklist Timeline Sprint MVP
### Sprint 1 (Minggu 1-2)
- [ ] Setup project (Flutter + Backend + Database).
- [ ] Modul Login Admin/Kasir.
- [ ] CRUD Bahan Baku.

### Sprint 2 (Minggu 3-4)
- [ ] CRUD Menu & Resep.
- [ ] Integrasi stok dengan penjualan.

### Sprint 3 (Minggu 5-6)
- [ ] Modul Transaksi Penjualan.
- [ ] Update stok otomatis.

### Sprint 4 (Minggu 7-8)
- [ ] Modul Laporan Stok & Restock Suggestion.
- [ ] UAT (User Acceptance Testing) & Deployment.

---

📌 **MVP Goal**: Sistem bisa otomatis mengurangi stok bahan setiap kali ada penjualan menu dan menampilkan laporan stok dengan rekomendasi restock.
