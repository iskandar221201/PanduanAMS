# 📣 Dokumentasi Modul Blast WhatsApp (AMS)

Modul **WhatsApp Blast** di AMS adalah fitur power-user yang memungkinkan tim marketing mengirim pesan personalisasi secara massal ke ratusan prospek secara lebih efisien. 

Tidak seperti broadcast biasa, modul ini terintegrasi penuh dengan database Prospek, memungkinkan filter target yang presisi dan penyisipan variabel otomatis (seperti menyapa nama masing-masing prospek).

---

## 🚀 Fitur Unggulan (Powerful Features)

### 1. Smart Spintax & Personalization
Hindari pemblokiran WA karena pesan "spammy" yang sama persis. Modul ini mendukung **Spintax** dan **Variabel Dinamis**:
*   **Contoh Template:** `{Halo|Hai|Selamat Pagi} kak {nama}, ada promo baru di {project} nih!`
*   **Hasil Pesan 1:** "Halo kak Budi, ada promo baru di Grand Sharon nih!"
*   **Hasil Pesan 2:** "Selamat Pagi kak Susi, ada promo baru di Grand Sharon nih!"
*   **Keuntungan:** Setiap pesan unik, terlihat personal, dan lebih aman dari deteksi spam.

### 2. Laser-Targeted Audience
Anda tidak perlu copy-paste nomor dari Excel. Gunakan fitur **Monitoring Prospek** untuk memfilter target spesifik:
*   "Kirim promo hanya ke prospek yang statusnya *Hot* bulan lalu."
*   "Follow-up prospek yang *Belum Dihubungi* dari sumber *Facebook Ads*."
*   "Sapa ulang prospek *Booking* tahun 2024 untuk tawaran referral."

### 3. Real-Time Runner dengan Kontrol Penuh
Proses pengiriman dilakukan satu per satu dengan jeda (delay) untuk keamanan.
*   **Interactive Runner:** Anda melihat progres pengiriman secara live (0% -> 100%).
*   **Skip/Retry:** Ada nomor yang salah? Bisa di-*Skip*. Ada gangguan internet? Bisa *Retry*.
*   **Mark Inactive:** Jika menemukan nomor mati saat pengiriman, langsung tandai sebagai *Inactive* agar tidak dikirimi pesan lagi di masa depan.

---

## 🛠️ Langkah Penggunaan (Step-by-Step)

### Cara 1: Kirim dari Menu Monitoring (Recommended)
Cara paling efisien untuk memilih target audiens.

1.  **Buka Menu Monitoring:**
    Masuk ke `Prospek > Monitor Prospek`.
2.  **Filter Data:**
    Gunakan panel *Filter & Pencarian*. Contoh: Pilih Status "Hot" dan Tanggal Input bulan lalu.
3.  **Pilih Prospek:**
    *   Centang kotak di sebelah kiri nama prospek yang ingin dikirimi pesan.
    *   Klik checkbox di judul tabel untuk memilih semua yang tampil di halaman tersebut.
4.  **Eksekusi Blast:**
    Klik tombol **<i class="fas fa-bullhorn"></i> Blast Terpilih** di pojok kanan atas tabel.
5.  **Tulis Pesan:**
    Anda akan diarahkan ke halaman pembuatan kampanye dengan daftar penerima yang sudah terisi otomatis.

### Cara 2: Buat Kampanye Manual
Jika Anda ingin mengetik nomor manual atau merencanakan kampanye "campur".

1.  Masuk ke menu **WhatsApp Blast > Buat Kampanye**.
2.  Isi **Nama Kampanye** (misal: "Promo Kemerdekaan 2025").
3.  **Pilih Target:** Cari dan pilih prospek dari database.
4.  **Tulis Pesan Template:** Gunakan spintax `{...|...}` dan variabel `{nama}`.
5.  Klik **Simpan & Preview**.

### Cara 3: Menjalankan Pengiriman (The Runner)
Setelah kampanye dibuat, statusnya *Pending*. Anda harus menjalankannya.

1.  Di daftar Blast, klik tombol **<i class="fas fa-play"></i> Mulai**.
2.  Halaman **Runner** akan terbuka.
3.  Klik **Start Sending**. Sistem akan membuka WhatsApp Web/API untuk setiap nomor secara berurutan.
4.  **Penting:** Jangan tutup tab browser sampai proses selesai 100%.

---

## 🛡️ Validasi & Logika Keamanan

### A. Validasi Nomor Telepon (_cleanPhone_)
Sistem otomatis membersihkan dan menstandarisasi nomor HP:
*   Mengubah `0812...` menjadi `62812...`.
*   Menghapus karakter aneh seperti `-` atau `( )`.
*   Mendeteksi format internasional `+65` , `+355` dan lainnya.
*   Jika nomor tidak valid (kurang dari 10 digit), otomatis di-skip.

### B. Proteksi Ganda (Double Protection)
*   **Owner Only:** Sales hanya bisa melihat dan mem-blast data prospek miliknya sendiri. Manager bisa mem-blast seluruh data tim.
*   **Anti-Spam Delay:** Sistem tidak mengirim 1000 pesan sekaligus, tapi antrian (queue) satu per satu untuk menjaga reputasi nomor WA kantor.

### C. Status Inactive
Jika saat proses blast ditemukan nomor yang tidak valid/tidak terdaftar di WA:
1.  Klik tombol **Mark Inactive** di layar Runner.
2.  Sistem mengupdate status nomor tersebut di database Prospek menjadi "Tidak Aktif".
3.  Di masa depan, nomor ini otomatis dikecualikan dari blast.

---

## ❓ FAQ Blast

**Q: Apakah saya bisa kirim gambar/brosur?**
> Saat ini modul hanya mendukung pesan teks dengan emoji. Untuk gambar, Anda bisa menyisipkan *link* Google Drive atau website di dalam pesan teks.

**Q: Apa itu Spintax?**
> Spintax adalah format teks `{opsi1|opsi2}` di mana sistem memilih satu kata secara acak. Contoh: `{Halo|Hai|Pagi}`. Gunakan ini sesering mungkin agar setiap pesan terlihat unik dan manusiawi.

**Q: Bagaimana kalau internet putus di tengah jalan?**
> Tidak masalah. Progres tersimpan otomatis. Cukup refresh halaman Runner dan klik *Resume*, sistem akan melanjutkan dari nomor terakhir yang sukses.

**Q: Bisakah saya membatalkan blast yang sudah dijadwalkan?**
> Bisa, selama belum dikirim. Buka detail kampanye dan hapus antrian atau hapus kampanye tersebut sepenuhnya.
