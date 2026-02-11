# 🏗️ Panduan Modul Project & Konstruksi

Dokumen ini menjelaskan cara pengelolaan data master **Proyek (Perumahan)** dan pemantauan **Progres Konstruksi** lapangan.

---

## 🏢 1. Manajemen Proyek (Admin & Project Manager)
Menu: **Manajemen Proyek** (Akses khusus Admin/PM)

Modul ini adalah hulu dari semua data. Sebelum bisa berjualan atau membangun, Anda harus mendefinisikan proyeknya terlebih dahulu.

### A. Menambah Proyek Baru
1.  Klik **Tambah Proyek**.
2.  Isi data wajib:
    *   **Nama Project:** (Misal: *Grand City Residence*)
    *   **Lokasi:** Alamat atau Kota.
    *   **Logo Proyek:** (Opsional) Format JPG/PNG, Max 5MB. Akan muncul di kop surat/laporan.
    *   **File Siteplan:** (Wajib untuk fitur Peta Digital) Gambar denah kavling bersih (JPG/PNG).
3.  Klik **Simpan**.

### B. Mengelola Aset (Kavling)
Setelah proyek dibuat, langkah selanjutnya adalah mendaftarkan unit kavling.
*   **Format Penamaan:** Sistem mewajibkan format **BLOK-NOMOR** (Huruf-Angka) dengan pemisah strip.
    *   ✅ Benar: `A-01`, `B-12A`
    *   ❌ Salah: `A01` (tanpa strip), `Blok A No 1` (terlalu panjang)
*   Aturan ini penting agar sistem **Siteplan Digital** bisa otomatis memetakan unit ke gambar.

---

## 🏗️ 2. Modul Template Konstruksi (RAB/BoQ Master)
Menu: **Konstruksi > Template Pekerjaan**

Sebelum membuat SPK Pembangunan satu per satu, sangat disarankan untuk membuat **Template Pekerjaan** terlebih dahulu. Fitur ini berfungsi sebagai "Master RAB" yang bisa digunakan berulang kali.

### A. Manfaat Template
1.  **Efisiensi Waktu:** Tidak perlu input item pekerjaan (Pondasi, Dinding, Atap) berulang-ulang untuk setiap rumah tipe yang sama.
2.  **Standarisasi:** Memastikan setiap unit dibangun dengan spesifikasi RAB yang seragam.
3.  **Fleksibilitas:** Bisa diedit per proyek atau berlaku global (untuk semua proyek).

### B. Cara Membuat Template Baru
1.  Klik **Buat Template Baru**.
2.  **Nama Template:** Berikan nama yang jelas, misal: *RAB Tipe 36 Standar* atau *Pagar Keliling Kavling*.
3.  **Pilih Proyek:**
    *   *Pilih Nama Proyek:* Template hanya muncul di proyek tersebut.
    *   *Kosongkan:* Template bersifat **Global** (bisa dipakai di semua proyek).
4.  **Input Detail Pekerjaan:**
    *   Masukkan daftar item pekerjaan, volume standar, dan satuan.
    *   Contoh:
        *   *Pekerjaan Persiapan* - *Pembersihan Lahan* - 1 ls
        *   *Pekerjaan Struktur* - *Galian Tanah* - 15 m3
5.  Klik **Simpan**.

### C. Cara Menggunakan Template (Load Template)
Saat Anda membuat Target Pembangunan (SPK) baru:
1.  Di form pembuatan target, cari tombol atau dropdown **"Load Template"**.
2.  Pilih template yang sesuai (misal: *RAB Tipe 36 Standar*).
3.  Sistem otomatis **mengisi tabel item pekerjaan** dengan data dari template.
4.  Anda tinggal menyesuaikan sedikit volume jika ada perbedaan kondisi lapangan.

---

## 🚜 3. Modul Konstruksi (Construction)
Menu: **Konstruksi / Progress Pembangunan**

Fitur ini dirancang untuk memantau Surat Perintah Kerja (SPK) pembangunan, baik untuk unit baru, fasilitas umum (Fasum), maupun perbaikan garansi.

### 📋 A. Membuat Target Pembangunan (SPK Baru)
Saat kontraktor mulai bekerja, Admin Proyek/Konstruksi membuat target baru:
1.  Klik **Buat Target Baru**.
2.  **Pilih Tipe Target:**
    *   🏠 **Unit:** Membangun rumah di kavling tertentu. (Hanya kavling yang *belum* punya target aktif yang muncul).
    *   🌳 **Fasum:** Pembangunan gerbang, jalan, taman, pos satpam (Input nama manual).
    *   🛡️ **Warranty (Garansi):** Perbaikan komplain konsumen. (Hanya muncul jika ada klaim garansi berstatus *Processed* dari modul Warranty).
3.  **Data Kontrak:**
    *   isi Nomor SPK, Nama Kontraktor, serta Tanggal Mulai & Selesai.
4.  **Detail Pekerjaan (BoQ/RAB):**
    *   Masukkan item pekerjaan (Misal: *Pondasi, Dinding, Atap*).
    *   Isi **Volume** dan **Satuan** (m3, m2, ls).
    *   **💡 Penting (Logika Bobot):** Sistem otomatis menghitung **Bobot %** setiap item berdasarkan proporsi volumenya terhadap total volume. Pastikan volume diinput dengan benar agar kurva S akurat.

### 📈 B. Update Progress Mingguan (Tracking)
Pengawas lapangan (Site Manager) mengupdate progres secara berkala:
1.  Pilih target di tabel, klik tombol **Track Progress** (Ikon Grafik).
2.  Di baris item pekerjaan, klik tombol **Update**.
3.  **Input Data Real-time:**
    *   **Realisasi %:** Masukkan persentase penyelesaian fisik di lapangan (0-100%).
    *   **Validasi:** Sistem menolak jika angka baru *lebih kecil* dari progres sebelumnya (Progress tidak bisa mundur).
    *   **Bukti Foto:** Wajib upload foto kondisi lapangan. Foto akan otomatis diberi *Watermark* nama proyek.
4.  **Kalkulasi Otomatis:**
    *   Saat Anda update 1 item, sistem akan menghitung ulang **Total Progress Proyek** berdasarkan bobot item tersebut.

### 🛠️ C. Edit Detail Pekerjaan (Addendum)
Jika di tengah jalan ada perubahan spesifikasi (Addendum):
1.  Masuk ke menu **Edit Item**.
2.  Anda bisa menambah item baru atau mengubah volume.
3.  **Resiko:** Mengubah volume akan **mereset/mengubah bobot persen** item lain secara otomatis. Harap berhati-hati.

### 🛡️ D. Integrasi Klaim Garansi
Jika ada komplain dari user (Modul Warranty) yang disetujui, maka data tersebut masuk ke antrean Konstruksi.
*   Pilih Tipe Target: **Warranty**.
*   Pilih klaim yang tersedia.
*   Setelah pekerjaan selesai (Progress 100%), Admin bisa menutup tiket komplain di modul Warranty.

### 🔐 E. Keamanan Data (Secure Delete)
Untuk mencegah kecurangan atau kesalahan hapus data progres:
*   **Hapus Target DIBATASI.** Anda tidak bisa menghapus target yang sudah memiliki progres (Progres > 0%).
*   Jika terpaksa hapus (misal salah input total), Anda memerlukan **Otorisasi Admin** (Token Delete) melalui sistem *Secure Delete Authorization*.

---

## 📊 Summary Logic (Ringkasan Logika Sistem)

| Fitur | Logika / Rumus |
| :--- | :--- |
| **Bobot Item** | _(Volume Item / Total Volume Semua Item) * 100_ |
| **Kontribusi Progres** | _(Bobot Item * % Progress Item) / 100_ |
| **Total Progres** | Sum of (Kontribusi Progres semua item) |
| **Ketersediaan Unit** | Unit hanya muncul di list "Buat Target" jika BELUM ada target konstruksi aktif padanya. |
| **Hapus Data** | Hanya bisa jika progres masih 0% **DAN** sudah dapat *Override Token* dari Admin. |
