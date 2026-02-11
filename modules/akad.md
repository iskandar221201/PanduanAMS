# 🤝 Panduan Modul Rekap Akad

Modul ini berfungsi sebagai **pusat monitoring akhir** dari seluruh rangkaian proses penjualan KPR, mulai dari Booking hingga terlaksananya Akad Kredit. Data di sini menjadi acuan final pencapaian penjualan (closing) di AMS.

## 1. Monitoring Data

Halaman utama menampilkan tabel rekapitulasi yang menggabungkan dua sumber data:

1.  **Data Otomatis (System):**
    *   Konsumen yang menjalani proses normal di AMS (Booking -> Pemberkasan -> Proses Bank -> Akad).
    *   Durasi proses (SLA) dihitung otomatis oleh mesin AMS berdasarkan riwayat inputan di modul-modul sebelumnya.
    *   Ditandai dengan label <span style="background-color:#e2e3e5; color:#383d41; padding:2px 6px; border-radius:10px; font-size:0.8em;">System</span>.

2.  **Data Manual (Legacy):**
    *   Data penjualan lama (sebelum pakai AMS) yang diinput manual untuk kepentingaan arsip/rekap.
    *   Durasi dan tanggal diinput secara manual.
    *   Ditandai dengan label <span style="background-color:#cff4fc; color:#055160; padding:2px 6px; border-radius:10px; font-size:0.8em;">Manual</span>.

### Informasi yang Ditampilkan
*   **Prospek & Unit:** Detail konsumen dan unit yang dibeli.
*   **Marketing:** Sales yang bertanggung jawab.
*   **Tanggal:** Tgl Booking vs Tgl Akad.
*   **Durasi:**
    *   **BK-AKD:** Total hari dari Booking sampai Akad.
    *   **Berkas:** Lama proses pemberkasan.
    *   **Bank:** Lama proses persetujuan bank (Analisa s/d SP3K).
*   **Dokumen:** Link download SPR dan SP3K (jika ada).

---

## 2. Input Akad Manual (Data Lama)

Fitur ini **KHUSUS** digunakan untuk merekap data penjualan masa lampau (History Data) yang tidak melalui proses realtime di AMS.

> **⚠️ PERHATIAN PENTING:**
> Jangan gunakan fitur ini untuk penjualan unit baru/sedang berjalan! Unit baru WAJIB mengikuti alur **Prospek > Booking > Pemberkasan > Proses Bank > Akad** agar perhitungan durasi proses dan performa sales tercatat akurat.

### Langkah-langkah Input Manual:
1.  Klik tombol **Tambah Akad** di pojok kanan atas.
2.  Akan muncul peringatan (Warning) bahwa ini untuk Data Lama. Klik **Lanjut**.
3.  Isi Form Lengkap:
    *   **Informasi Dasar:** Pilih Project, Input Nama Konsumen, Pilih Sales, dan Unit.
    *   **Tanggal:** Masukkan Tgl Booking dan Tgl Akad yang sebenarnya terjadi di masa lalu.
    *   **Durasi Manual:** Anda bisa mengetik durasi (misal: "30 Hari") karena AMS tidak memiliki data historisnya untuk menghitung otomatis.
    *   **Nilai SP3K:** Masukkan nominal cair.
4.  **Upload Arsip:** Upload scan SPR dan SP3K lama jika ada (untuk backup digital).
5.  Klik **Simpan Data Akad**.

*Catatan: Saat Anda menyimpan data manual, AMS akan otomatis membuatkan data dummy di modul Booking dan mengubah status Unit di Siteplan menjadi 'Sold/Akad' agar stok unit terupdate.*

---

## 3. Export Data

Anda dapat mencetak laporan rekapakad dalam berbagai format untuk keperluan meeting atau arsip fisik.

*   **Excel:** Untuk olah data lebih lanjut.
*   **PDF:** Laporan siap cetak dengan Kop Surat dan Logo Project (Landscape).
*   **Print:** Cetak langsung ke printer.

Fitur export ini akan mengikuti filter yang sedang aktif (misal: hanya Project A, atau Semua Project).

---

## FAQ

**Q: Mengapa saya tidak bisa mengedit durasi pada data berlabel "System"?**
> Data berlabel "System" adalah hasil kalkulasi otomatis dari kejadian *realtime*. Jika durasinya dirasa salah, berarti ada kesalahan input tanggal di proses sebelumnya (Booking/Pemberkasan/Bank). Silakan koreksi di modul terkait, bukan di sini.

**Q: Apakah data manual mempengaruhi laporan penjualan?**
> Ya. Sama seperti data otomatis, data manual yang diinput di sini akan tercatat sebagai penjualan sukses dan unitnya akan terkunci (tidak bisa dijual lagi).

**Q: Bagaimana jika konsumen batal setelah Akad?**
> Kasus ini sangat jarang (Buyback). Jika terjadi, hubungi Super Admin untuk membatalkan status booking secara paksa melalui database atau fitur *Rollback* (jika tersedia), karena secara default status Akad dianggap final.
