# 🏗️ Panduan Modul Manajemen Proyek (Master Project)

Modul **Manajemen Proyek** adalah jantung dari struktur data di AMS. Modul ini digunakan oleh **Super Admin** atau level pimpinan untuk mendaftarkan dan mengelola seluruh proyek perumahan yang berjalan di bawah naungan perusahaan.

## 1. Konsep "Project Scope" (Sekat Data)

AMS didesain untuk menangani banyak proyek secara sekaligus (*Multi-Project*). Modul ini berperan penting sebagai pemisah (sekat) data agar operasional antar proyek tidak saling bercampur.

### Bagaimana Scope Bekerja?
1.  **Session-Based Filtering:** Saat user login, mereka sudah ditugaskan pada satu proyek aktif. ID proyek tersebut disimpan dalam session AMS.
2.  **Otomatisasi Filter:** Hampir seluruh modul lain (Kavling, Prospek, Booking, Biaya, dll) akan secara otomatis hanya menampilkan data yang sesuai dengan proyek yang sedang aktif di session user tersebut.
3.  **Keamanan Data:** Tim sales atau admin di Proyek A tidak akan bisa melihat data konsumen di Proyek B, kecuali mereka memiliki izin khusus (Scope: `all_projects`).

---

## 2. Fitur Utama

### Pengelolaan Data Proyek
*   **Nama Proyek:** Identitas resmi perumahan.
*   **Lokasi:** Alamat atau area pemasaran proyek.
*   **Deskripsi:** Informasi tambahan mengenai keunggulan atau detail proyek.
*   **Logo Proyek:** Digunakan sebagai identitas visual pada header laporan (PDF/Excel) yang dicetak melalui AMS.

### Pengelolaan Site Plan & Arsip
Anda dapat mengunggah file gambar Site Plan (JPG/PNG) di setiap proyek.
*   **Site Plan Digital:** Berperan sebagai referensi visual utama.
*   **Pembaruan File:** AMS mendukung penggantian (update) file site plan. Namun, perlu diperhatikan bahwa **dimensi (lebar & tinggi) serta aspek rasio file baru harus identik dengan file lama**.
    *   *Risiko Teknis:* Jika dimensi berubah, titik koordinat unit yang sudah di-plotting pada modul Site Plan Interaktif akan bergeser dan tidak lagi presisi. Perubahan dimensi mengharuskan Anda melakukan plotting ulang seluruh unit kavling.
*   **Penyimpanan Aman:** Seluruh file tersimpan secara terorganisir di sub-folder `uploads/site_plans/` dan `uploads/project_logos/`.

---

## 3. Alur Teknis (Workflow)

### Menambah Proyek Baru
1.  Buka menu **Admin > Proyek**.
2.  Klik **Tambah Proyek Baru**.
3.  Isi data identitas dan unggah Logo serta Site Plan (Jika sudah ada).
    *   *Tips: Gunakan Logo dengan format PNG transparan agar tampilan di laporan PDF terlihat lebih profesional.*
4.  Klik **Simpan**.

### Mengubah (Edit) Proyek
1.  Klik ikon **Pensil (Kuning)** pada baris proyek.
2.  Ubah informasi yang diperlukan.
3.  Jika ingin mengganti file, cukup unggah file baru. AMS akan otomatis menghapus file lama dari server untuk menghemat ruang penyimpanan.
4.  Gunakan fitur **Switch (Hapus File)** jika ingin mengosongkan file tanpa menggantinya.

### Menghapus Proyek
AMS menyertakan **Fitur Keamanan Penghapusan**. Jika sebuah proyek sudah memiliki data terkait (seperti unit kavling, daftar prospek, user atau data booking), maka tombol hapus akan ditolak oleh AMS dengan pesan peringatan. Hal ini untuk menjaga integritas data agar tidak ada transaksi yang menjadi "yatim" atau hilang secara tidak sengaja.

---

## FAQ

**Q: Apakah menghapus proyek akan menghapus data kavling/booking di dalamnya?**
> **TIDAK BISA.** AMS akan memblokir proses penghapusan jika proyek tersebut sudah memiliki data aktif (User, Kavling, Prospek, atau Booking). Anda harus menghapus data-data terkait tersebut terlebih dahulu jika benar-benar ingin menghapus master proyeknya. Hal ini adalah prosedur keamanan untuk mencegah kehilangan data massal secara tidak sengaja.

**Q: Mengapa logo tidak muncul di cetakan laporan PDF?**
> Pastikan Anda telah mengunggah Logo di modul ini. AMS mengambil logo secara dinamis berdasarkan `project_id` yang sedang aktif saat laporan dicetak. Jika logo belum diunggah, header laporan akan tampil standar tanpa logo.

**Q: Mengapa saya harus menggunakan dimensi gambar yang sama saat update Site Plan?**
> Karena modul Site Plan Interaktif AMS menyimpan data lokasi unit dalam koordinat piksel (atau persentase relatif). Jika gambar baru lebih lebar, lebih tinggi, atau memiliki perbandingan (rasio) yang berbeda, maka titik-titik unit yang sudah dibuat sebelumnya akan "melenceng" dari gambar bangunan di peta. Pastikan tim desain memberikan file revisi dengan resolusi yang sama persis.

**Q: Saya sudah menambah proyek, tapi sales tidak bisa melihatnya?**
> Pastikan user Sales tersebut sudah diberikan akses melalui modul **User Management** atau akun mereka sudah disetting untuk memiliki akses ke proyek baru tersebut.
