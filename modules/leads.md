# 🎯 Panduan Penggunaan Modul Prospek (Leads Management)

Modul **Prospek** adalah pusat pengelolaan data calon konsumen (Leads) dalam Arthamulya Management System (AMS). Modul ini digunakan oleh tim Marketing untuk mencatat, melacak, dan merawat potensi penjualan dari tahap awal hingga penutupan (Closing).

---

## 1. Menambahkan Prospek Baru
Setiap kali Anda mendapatkan kontak calon konsumen baru, segera catat ke dalam AMS agar tidak hilang dan bisa ditindaklanjuti.

**Langkah-langkah:**
1.  Buka menu **Prospek** di sidebar.
2.  Klik tombol **+ Tambah Prospek**.
3.  Isi formulir data diri konsumen:
    *   **Nama Prospek:** Nama lengkap calon konsumen.
    *   **Kode Negara & Telepon:** Pastikan nomor WhatsApp aktif. AMS otomatis mendeteksi kode negara.
    *   **Sumber Leads:** Dari mana konsumen ini didapat? (Pameran, Iklan IG, Walk-in, dll).
    *   **Alamat & Keterangan:** Alamat calon konsumen.
4.  Klik **Simpan**.

> #### **Gunakan Data yang valid:**
> Jika sudah mendapatkan informasi lengkap yang valid, segera ubah data calon konsumen dengan data yang benar sesuai kartu identitas (KTP), karena akan berpengaruh terhadap data booking dan pembuatan SPR.

> #### **Validasi Sistem:**
> AMS akan menolak jika Nomor Telepon sudah terdaftar sebelumnya. Ini untuk mencegah *double claim* antar marketing.

---

## 2. Mengelola & Update Status Prospek
Perjalanan seorang konsumen dari "Sekedar Tanya" hingga "Beli Rumah" dilacak melalui **Status Prospek**. Anda wajib mengupdate status ini secara berkala sesuai perkembangan interaksi.

**Alur Status (Sales Pipeline):**
1.  **New:** Prospek baru masuk, belum dihubungi.
2.  **Follow Up:** Sedang dalam komunikasi intens (chat/telepon).
3.  **Hot:** Konsumen sangat berminat, minta simulasi harga/brosur detail.
4.  **Cek Lokasi:** Konsumen menjadwalkan atau sudah survei ke lokasi proyek.
5.  **SLIK:** Konsumen setuju lanjut dan sedang dalam proses pengecekan BI Checking (SLIK OJK).
6.  **Booking:** Konsumen membayar Booking Fee (Unit dipesan).
7.  **Cold:** Konsumen tidak berminat/batal/tidak bisa dihubungi (Arsip).

**Cara Update Status:**
1.  Di daftar prospek, klik tombol **Edit** (ikon pensil) pada nama konsumen.
2.  Ubah kolom **Status** ke tahap selanjutnya.
3.  Klik **Simpan Perubahan**.

> #### **Aturan Transisi:**
> Anda tidak bisa melompat status sembarangan. Misalnya dari *New* langsung ke *Booking*. Ikuti alur yang wajar. 
---

## 3. Mencatat Aktivitas & Jadwal (Follow Up)
Untuk menjaga komunikasi yang efektif, gunakan modul **CRM Official** untuk mencatat semua interaksi dan merencanakan jadwal follow-up.

**Dashboard CRM:**
Halaman utama CRM (`crm/index`) menampilkan dua panel penting:
*   **Aktivitas Hari Ini:** Daftar tugas follow-up yang harus dikerjakan hari ini.
*   **Overdue Activities:** Tugas yang terlewat dari jadwal (segera selesaikan!).

**Cara Menambah Catatan & Aktivitas:**
1.  Buka menu **CRM Official** > Klik **Detail** pada nama prospek.
2.  **Tambah Catatan (Notes):**
    *   Gunakan tab **Catatan** untuk menyimpan info penting (misal: preferensi konsumen, kendala budget). Catatan bersifat informatif dan tidak memiliki jadwal.
3.  **Jadwalkan Aktivitas (Activity):**
    *   Gunakan tab **Aktivitas** untuk membuat rencana aksi.
    *   Isi **Jenis** (Telepon/Visit/Meeting), **Deskripsi**, dan **Tanggal Jadwal**.
    *   Klik **Simpan**. Aktivitas ini akan muncul di Dashboard pada tanggal tersebut sebagai pengingat.

**Menyelesaikan Aktivitas:**
Setelah melakukan follow-up, jangan lupa menandai aktivitas sebagai selesai:
1.  Di daftar aktivitas (Dashboard atau Detail Prospek), klik tombol **Tandai Selesai** (Checklist).
2.  Sistem akan mencatat waktu penyelesaian dan *user* yang mengerjakannya.

---

## 4. Validasi Khusus (SLIK & Booking)
Ada dua status spesial yang memiliki aturan ketat:

### A. Status "SLIK" (Cek BI Checking)
Untuk mengubah status ke **SLIK**, Anda **WAJIB** mengisi **Nomor KTP (NIK)** konsumen.
*   Sistem akan memvalidasi format NIK (harus 16 digit angka).
*   Perubahan ke status ini akan otomatis mengirim notifikasi ke **Admin Legal/KPR** untuk segera melakukan pengecekan SLIK.

### B. Status "Booking"
Digunakan jika konsumen yang akan melakukan booking, jika data konsumen tersebut tidak ada di modul SLIK (Indikator bahwa konsumen tersebut belum melakukan SLIK), maka Anda tidak bisa melakukan update status ke 'Booking'.


---

## FAQ (Tanya Jawab)

**Q: Saya tidak bisa ubah status ke "Booking", kenapa?**

> Cek apakah status sebelumnya adalah SLIK? AMS tidak mengizinkan booking tanpa melewati proses SLIK.

**Q: Nomor HP konsumen ganti, bagaimana cara ubahnya?**
> Nomor HP adalah kunci unik identitas konsumen. Untuk menjaga integritas data, nomor HP **tidak bisa diubah** sembarangan. Hubungi Admin IT jika memang terjadi kesalahan input fatal.

**Q: Apakah Prospek saya bisa dilihat Sales lain?**
> Tidak. Secara default, Anda hanya bisa melihat prospek milik sendiri (*Private Scope*). Supervisor dan Manager bisa melihat prospek tim mereka.

**Q: Apakah saya bisa hapus data prospek?**
> Demi menjaga integritas data dan riwayat audit (audit trail) perusahaan, AMS tidak mengizinkan penghapusan data secara permanen dari basis data.