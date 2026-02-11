# 🔔 Sistem Notifikasi Real-Time (AMS)

AMS dilengkapi dengan **Sistem Notifikasi Terpadu** yang memastikan setiap tim mendapatkan informasi penting secara instan. Sistem ini dirancang agar setiap alur kerja (seperti persetujuan booking atau pengaduan unit) dapat diproses dengan cepat tanpa harus mengecek database secara manual.

---

## 🚀 Fitur Unggulan 

### 1. Real-Time Smart Polling
AMS melakukan sinkronisasi data ke server setiap 15 detik untuk memeriksa adanya aktivitas baru.
*   **Dynamic Badge:** Ikon lonceng pada Navbar akan otomatis menampilkan angka merah (kontras tinggi) jika ada pesan baru yang belum dibaca.
*   **Instant Dropdown:** Klik ikon lonceng untuk melihat ringkasan singkat (10 pesan terakhir) tanpa harus meninggalkan halaman yang sedang Anda buka.

### 2. Segmentasi Notifikasi (Cerdas & Relevan)
AMS cukup cerdas untuk memilah siapa yang berhak menerima informasi. Notifikasi dikirimkan berdasarkan:
*   **Project Geofencing:** Manajer di Proyek A tidak akan terganggu oleh notifikasi booking dari Proyek B.
*   **Role Based:** Notifikasi teknis (seperti keluhan garansi) hanya dikirim ke tim Konstruksi, sementara notifikasi finansial (seperti pembayaran booking) dikirim ke Admin Pusat dan Direksi.

### 3. Integrated Action Link
Notifikasi AMS bukan sekadar teks. Setiap pesan dilengkapi dengan link aktif yang jika diklik akan langsung mengarahkan Anda ke **halaman detail data** yang bersangkutan. 
*   *Contoh:* Klik notifikasi "Booking Baru dari Budi" akan langsung membawa Anda ke formulir persetujuan (ACC/Reject) konsumen tersebut.

### 4. Human-Friendly Time
AMS menggunakan format waktu relatif (seperti *"2 menit yang lalu"* atau *"Baru saja"*) sehingga pimpinan dapat segera mengetahui seberapa mendesak informasi tersebut.

---

## 🛠️ Langkah Penggunaan (User Guide)

### A. Melihat Notifikasi Baru
1.  Perhatikan ikon **Lonceng** di pojok kanan atas layar.
2.  Jika muncul angka merah, berarti ada informasi baru.
3.  Klik ikon tersebut untuk membuka **Dropdown Notifikasi**.

### B. Memproses Informasi
1.  Baca ringkasan judul dan isi pesan di dropdown.
2.  Klik pada pesan tersebut untuk masuk ke modul terkait.
3.  AMS akan otomatis menandai pesan tersebut sebagai **"Sudah Dibaca"**.

### C. Manajemen Daftar Notifikasi
1.  Untuk melihat riwayat notifikasi secara lengkap, klik tombol **"Lihat Semua Notifikasi"** di bagian bawah dropdown.
2.  Gunakan tombol **"Tandai Baca Semua"** jika Anda ingin membersihkan angka badge merah secara instan.

---

## 🛡️ Aturan & Mekanisme AMS

1.  **Auto-Pruning:** AMS hanya menyimpan riwayat notifikasi terbaru untuk menjaga performa sistem tetap ringan.
2.  **Strict Privacy:** User hanya dapat melihat notifikasi yang memang ditujukan untuk akun atau level jabatan mereka (sesuai Role ID).
3.  **CORS & Socket Security:** Saat pengiriman notifikasi, AMS melakukan pemeriksaan keamanan server (`DarkReader safe-fetch`) untuk memastikan konektivitas tidak terganggu oleh pengaturan browser.

---

## ⌨️ Tips & Shortcut

| Kebutuhan | Cara |
| :--- | :--- |
| **Cek Notifikasi Tanpa Mouse** | Lihat angka badge lonceng. Jika bertambah, tekan **F5** atau tunggu 15 detik untuk update otomatis. |
| **Bersihkan Lonceng** | Klik dropdown notifikasi lalu pilih "Tandai Baca Semua". |
| **Kembali ke Detail** | Alih-alih mencari manual di tabel monitor, selalu gunakan link di notifikasi untuk akses tercepat. |

---

## ❓ FAQ

**Q: Mengapa saya mendapatkan notifikasi tapi saat diklik datanya tidak ada?**
> A: Hal ini bisa terjadi jika data tersebut sudah dihapus oleh Admin atau pimpinan lain sebelum Anda sempat membukanya.

**Q: Apakah notifikasi ini masuk ke WhatsApp saya?**
> A: Tidak. Notifikasi ini hanya muncul di dalam aplikasi AMS. 

**Q: Berapa lama notifikasi akan muncul setelah kejadian?**
> A: AMS mengecek data setiap 15 detik. Jadi, maksimal dalam 15 detik sejak data di-input, notifikasi akan muncul di layar Anda.
