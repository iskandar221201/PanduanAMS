# 🌐 Overview: Ekosistem Arthamulya Management System (AMS)

**Arthamulya Management System (AMS)** adalah solusi ERP (Enterprise Resource Planning) terintegrasi yang dirancang untuk mendigitalkan seluruh siklus bisnis properti, mulai dari akuisisi lahan, konstruksi, pemasaran, penjualan, hingga serah terima unit dan purna jual.

Sistem ini menghubungkan berbagai departemen (Marketing, Teknik, Keuangan, Legal, Logistik) dalam satu platform data yang *real-time* dan transparan.

---

## 🏗️ 1. Manajemen Proyek & Aset (Project Management)
Fondasi data untuk seluruh operasional. Modul ini digunakan oleh **Admin Project** dan **Manajemen**.

*   **Manajemen Proyek:** Mengelola data induk perumahan (Lokasi, Logo, Siteplan).
*   **Aset Kavling (Inventory):** Manajemen stok unit (Nomor Unit, Luas Tanah/Bangunan) dengan status *real-time* (Available, Booked, Sold, Hold).
*   **Digital Siteplan:** Peta interaktif yang memvisualisasikan status unit secara visual di atas gambar denah proyek.
*   **Harga Kavling:** Pengaturan harga jual standar dan riwayat perubahan harga.

> 📘 **Dokumentasi Lengkap:** Lihat [Panduan Proyek & Konstruksi](project&konstuksi.md)

---

## 🤝 2. CRM & Penjualan (Sales & Marketing)
Ujung tombak bisnis untuk pengelolaan prospek dan konversi penjualan. Digunakan oleh **Sales, SPV, & Marketing Manager**.

*   **Manajemen Leads (Prospek):** Database calon konsumen dengan fitur *anti-double claim* (validasi nomor HP).
*   **Sales Pipeline:** Pelacakan status prospek (*New > Hot > Cek Lokasi > Booking*).
*   **Marketing Tools:**
    *   **WhatsApp Blast:** Kirim pesan massal ke database kontak.
    *   **Product Knowledge:** Repository digital untuk brosur, pricelist, dan materi promosi per proyek.
    *   **Ads Manager:** Integrasi laporan performa iklan digital (Meta Ads).
*   **Booking System:**
    *   **Pencatatan Booking:** Input data pemesanan unit (UTJ) yang memotong stok.
    *   **SPR Generator:** Cetak Surat Pemesanan Rumah (SPR) otomatis berdasarkan template dinamis.

> 📘 **Dokumentasi Lengkap:** Lihat [Panduan CRM & Leads](crm&leads.md)

---

## 🚜 3. Konstruksi & Teknik (Construction-Engineering)
Pemantauan progres fisik pembangunan di lapangan. Digunakan oleh **Tim Teknik & Admin Proyek**.

*   **SPK Pembangunan (Target):** Pembuatan surat perintah kerja untuk Unit, Fasum, atau Perbaikan Garansi.
*   **Template RAB/BoQ:** Standarisasi item pekerjaan (Pondasi, Dinding, Atap) untuk efisiensi input SPK.
*   **Progress Tracking:** Laporan progres mingguan dengan bobot persentase otomatis (Kurva S) dan bukti foto lapangan.
*   **Warranty System (Garansi):** Portal penanganan komplain konsumen pasca-serah terima (Masa Retensi).

> 📘 **Dokumentasi Lengkap:** Lihat [Panduan Proyek & Konstruksi](project&konstuksi.md)

---

## 📦 4. Logistik & Pengadaan (Procurement)
Manajemen rantai pasok material konstruksi. Digunakan oleh **Logistik & Purchasing**.

*   **Purchase Request (PR):** Pengajuan permintaan pembelian material dari lapangan.
*   **Purchase Order (PO):** Pembuatan pesanan pembelian ke vendor/supplier.
*   **Goods Receiving (Penerimaan):** Pencatatan barang masuk gudang (GRN) beserta bukti foto dan surat jalan.
*   **Goods Taking (Pengambilan):** Pencatatan material keluar dari gudang untuk digunakan di proyek.
*   **Stok Opname:** Monitoring saldo stok material di gudang proyek.

---

## ⚖️ 5. Legalitas & KPR (Legal & Bank)
Mengawal proses administrasi aset dan konsumen. Digunakan oleh **Admin Legal & KPR**.

*   **Legalitas Aset (Kavling):** Checklist dokuman induk per unit (Sertifikat, PBB, IMB/PBG) dengan status digital.
*   **Administrasi Konsumen:**
    *   **SLIK Checking:** Pengajuan pemeriksaan riwayat kredit.
    *   **Pemberkasan KPR:** Checklist kelengkapan dokumen persyaratan bank.
    *   **Monitoring Bank:** Status real-time (Wawancara > SP3K > Akad).
*   **Serah Terima (BAST):** Pencatatan berita acara serah terima kunci kepada konsumen.

---

## 💰 6. Keuangan & Akuntansi (Finance)
Pencatatan arus kas masuk dan keluar proyek. Digunakan oleh **Finance & Kasir**.

*   **Pencatatan Keuangan (Invoicing):** Kartu piutang digital per konsumen untuk memantau pembayaran (Booking Fee, DP, KPR/Cash) dengan fitur penyesuaian otomatis sisa plafon KPR (SP3K).
*   **Validasi Pembayaran:** Verifikasi bukti transfer dan pencatatan tanggal terima uang.
*   **Pengajuan & Realisasi Dana:**
    *   **Cash Advance (Kasbon):** Permintaan dana operasional di muka.
    *   **Reimbursement/Payment:** Pembayaran ke vendor atau penggantian biaya.
    *   **Realisasi:** Pelaporan penggunaan dana aktual dibanding pengajuan.
*   **Jurnal Pembalik (Cancellation Handler):** Pengelolaan dana dari transaksi batal (*Reject/Mundur*), dengan opsi:
    *   **Refund:** Dikembalikan ke konsumen.
    *   **Pendapatan Lain:** Hangus/menjadi hak perusahaan.
    *   **Transfer Unit:** Dialihkan sebagai deposit untuk pembelian unit lain.
*   **Laporan Arus Kas:** Rekapitulasi Cash In & Cash Out per proyek.

---

## 🛡️ 6. Administrasi Sistem (System Admin)
Pengaturan keamanan dan hak akses pengguna.

*   **User Management:** Pengelolaan akun pengguna, password, dan status aktif.
*   **Role & Permission (RBAC):** Pengaturan hak akses (Siapa boleh *Lihat/Edit/Hapus*) secara granular per modul.
*   **Log Aktivitas (Audit Trail):** Rekaman jejak digital setiap aksi user (Siapa mengubah data apa dan kapan).
*   **Notifikasi Sistem:** Pengaturan notifikasi otomatis (misal: Notifikasi Jatuh Tempo, Notifikasi Approval).

---

## 🧭 Navigasi Cepat
Untuk memulai, silakan akses halaman utama:
*   [**Dashboard Area**](dashboard.md): Ringkasan metrik kinerja & navigasi cepat.
*   [**Login Portal**](../../public/login): Halaman masuk aplikasi.


