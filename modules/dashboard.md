# 📊 Panduan & Dokumentasi Dashboard Sistem

Dashboard ini dirancang dinamis menyesuaikan dengan **Role (Peran)** pengguna yang login. Data yang ditampilkan diambil secara *real-time* dari berbagai modul seperti Penjualan, Konstruksi, dan Keuangan.

Berikut adalah penjelasan rinci mengenai nilai (values) dan metrik yang ditampilkan untuk setiap divisi.

---

## 1. Dashboard Manajemen & Eksekutif
**Role:** Project Manager, Direktur, Owner, General Manager, Admin Project, Construction Manager.

Dashboard ini memberikan wawasan "Helicopter View" terhadap kesehatan proyek secara keseluruhan.

### 📐 Statistik Unit (Kavling)
Angka ini **bukan sekadar status fisik** kavling, melainkan status gabungan antara **Status Fisik + Status Transaksi**. 
Logika penentuan status adalah prioritas sebagai berikut:
1.  **Status Transaksi (Prioritas Utama):** Jika ada data booking aktif (tidak *Reject*/*Mundur*), status transaksi yang diambil (misal: *SP3K Turun*, *Akad Kredit*, dll).
2.  **Validasi Pengajuan:** Jika ada pengajuan booking yang sedang diproses (*Pending/ACC*), maka status fisik kavling (*Booked/Hold*) dianggap valid dan ditampilkan.


### 💰 Ringkasan Keuangan (Financial Overview)
Menampilkan kesehatan arus kas proyek berdasarkan data **Pencatatan Keuangan** (tidak termasuk unit status *Reject* atau *Mundur*).
*   **Total Piutang:** Akumulasi total Harga Jual (Netto) dari semua unit yang terjual. Ini adalah *potensi omzet*.
*   **Total Dibayarkan:** Total uang tunai yang sudah diterima perusahaan (Cash In).
*   **Total Saldo Piutang:** Sisa tagihan konsumen yang belum dibayar (*Outstanding*).

### 🏗️ Progres Konstruksi & Garansi
*   **Stats Pembangunan:** Jumlah unit dikelompokkan berdasarkan status target konstruksi (dari modul *Construction Targets*).
*   **Klaim Garansi:** Memantau jumlah komplain konsumen purna-jual (*Submitted, Processed, Completed*).

### 📈 Tren Penjualan (Sales Trend)
Grafik batang yang menunjukkan jumlah unit terjual (booking) per bulan pada tahun berjalan.

### 🌪️ Statistik Konversi & Funnel (Analisis Pipeline)
Bagian ini menjelaskan bagaimana sistem menghitung efektivitas tim marketing dari awal (Leads) hingga akhir (Closing).
Konsep utamanya adalah memisahkan antara **"Kegiatan"** (seberapa sibuk tim) dengan **"Hasil Nyata"** (berapa unit terjual).

#### Logika Perhitungan:
1.  **Total Leads (Prospek):** Menghitung jumlah total data orang yang masuk ke database prospek.
    *   *Rumus: 1 Nama Orang = 1 Lead.*
2.  **SLIK Diajukan:** Menghitung jumlah pengajuan BI Checking sebagai indikator minat serius awal.
3.  **Booking (Orang Unik):** Berapa banyak **orang berbeda** yang pernah melakukan booking, terlepas ujungnya lanjut atau batal.
    *   *Logika:* Jika Pak Budi booking -> Reject -> Booking Ulang, tetap dihitung **1 Booking**. Ini untuk mengukur jumlah *peminat unik*.
4.  **Closing (Sukses):** Jumlah orang yang transaksinya dianggap **BERHASIL**.
    *   *Kriteria Berhasil:* Status transaksi meliputi Pemberkasan, Proses Bank, SP3K, Akad, Cash, atau Cash Bertahap.
    *   *Note:* Status *Reject* dan *Mundur* tidak dihitung di sini.

> **Studi Kasus:**
> *   **Ganti Kavling:** Jika konsumen pindah dari blok A1 ke A2, sistem menghitungnya sebagai **1 Closing** (data tidak ganda).
> *   **Suami Ganti Istri:** Jika suami reject, lalu istri maju booking baru, sistem menghitungnya sebagai **2 Booking** (karena dua orang berbeda), namun tetap **1 Closing** (jika istri berhasil).


---

## 2. Dashboard Sales & Marketing
**Role:** Marketing, SPV Marketing, Marketing Manager.

Fokus pada **Target Penjualan** dan **Manajemen Prospek (Leads)**.

### 🎯 Pipeline Prospek (Lead Stats)
Untuk memudahkan prioritas, status prospek dikelompokkan ke dalam 4 kategori nilai:
*   **New Leads:** Akumulasi status `New` dan `Follow Up`. (Harus segera dihubungi).
*   **Hot Prospect:** Khusus status `Hot`. (Potensi closing tinggi).
*   **In Process:** Akumulasi status `Cek Lokasi`, `SLIK`, `Booking`, dan `Ganti Pengaju`. (Sedang dalam tahap konversi).
*   **Cold/Reject:** Khusus status `Cold`. (Prospek tidak lanjut).

> **Nilai Penting:**
> *   **Total Leads:** Jumlah total data prospek yang ditangani sales tersebut.
> *   **Bookings This Month:** Jumlah closing/booking yang dilakukan sales **bulan ini**.

### 👥 Performa Tim (Khusus SPV & Manager)
*   **Top Sales:** Menampilkan 5 sales dengan jumlah booking terbanyak.
*   **Funnel:** Sebaran status transaksi dari seluruh tim (berapa yang baru Booking, berapa yang sudah Akad, dll).

---

## 3. Dashboard Marketing Communication (Marcom)
**Role:** Marketing Communication.

Fokus pada efektivitas belanja iklan (**Ad Spend**) dan kualitas trafik.

*   **Ad Performance:** Laporan harian dari Meta Ads (mendata `ad_spend` dan metrik iklan lainnya).
*   **Total Spend:** Total biaya iklan yang dikeluarkan (akumulasi dari data report).
*   **Sumber Leads:** Grafik pie chart yang menunjukkan asal leads (misal: Facebook, Instagram, Walk-in, Website Official).
*   **Official Leads Count:** Jumlah leads yang masuk melalui jalur "Official" untuk mengukur efektivitas kampanye digital.

---

## 4. Dashboard Keuangan (Finance)
**Role:** Finance, Admin Keuangan, Finance Manager.

Dashboard ini menyajikan detail likuiditas dan pencatatan akuntansi.

### 💵 Arus Kas & Piutang
Sama seperti dashboard manajemen, namun lebih mendalam. Data diambil dari tabel `pencatatan_keuangan`.
*   **Total Nilai Kontrak:** Total nilai transaksi penjualan yang aktif.
*   **Realisasi Pembayaran:** Uang yang sudah masuk ke rekening.
*   **Outstanding:** Piutang yang harus ditagih.

### 🔄 Jurnal Pembalik & Refund
Memantau dana keluar atau pembatalan transaksi dari tabel `jurnal_pembalik`.
*   **Total Dikembalikan:** Total nominal *refund* yang disetujui.
*   **Total Pendapatan Lain:** Pemasukan administratif di luar harga unit.
*   **Total Transfer:** Total mutasi dana keluar tercatat.

---

## 5. Dashboard KPR & Administrasi
**Role:** Admin KPR.

Fokus pada kelayakan konsumen (SLIK) dan proses pemberkasan bank.

*   **Statistik SLIK:** Jumlah calon konsumen berdasarkan hasil BI Checking (misal: *Lancar, Kol 5, Tidak Ada Data*). Ini krusial untuk filter awal persetujuan booking.
*   **Status Booking:** Memantau sebaran konsumen berdasarkan tahapan KPR (Pemberkasan, Wawancara, SP3K, Akad).

---

## 🚀 Fitur Navigasi Cepat
Setiap dashboard memiliki menu **Quick Access** (kotak berwarna) yang disesuaikan dengan kebutuhan harian role tersebut, misalnya:
*   **Marketing:** Tombol cepat ke *Manajemen Prospek* dan *Cek Harga Kavling*.
*   **PM/Konstruksi:** Tombol cepat ke *Siteplan Editor* dan *Kelola Pembangunan*.
*   **Finance:** Tombol cepat ke *Validasi Pembayaran*.

Gunakan filter **"Pilih Proyek"** di pojok kanan atas (untuk level Manager/Direktur) guna menyaring data spesifik per perumahan.


