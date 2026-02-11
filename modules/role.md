# 🔑 Panduan Modul Role & Permission (RBAC)

Modul ini adalah **pusat kendali otorisasi** di AMS. Hanya **Administrator (Role ID: 1)** yang memiliki akses ke halaman ini. Di sinilah Anda mengatur siapa boleh mengakses apa, dan sejauh mana cakupan datanya.

## 1. Konsep RBAC (Role-Based Access Control)

AMS menggunakan sistem RBAC yang terdiri dari 3 komponen utama:

| Komponen | Penjelasan |
|---|---|
| **Role** | Identitas jabatan user (misal: Sales, Admin KPR, Koordinator). Didefinisikan di tabel _roles_. |
| **Permission** | Kombinasi **Modul + Aksi** yang diizinkan untuk role tersebut. Contoh: Role "Sales" memiliki permission _prospek > create_. |
| **Scope** | Cakupan data yang bisa diakses. Menentukan apakah user bisa melihat data semua proyek atau hanya proyek yang di-assign kepadanya. |

### Alur Kerja Otorisasi
1.  User login → AMS membaca `role_id` dari session.
2.  Setiap kali user mengakses suatu fitur, AMS memanggil `Permission::can('nama-modul', 'aksi')`.
3.  Jika **Role ID = 1 (Administrator)**, langsung diizinkan tanpa pengecekan (Super Admin).
4.  Untuk role lain, AMS mengecek apakah kombinasi `role_id + module + action` ada di tabel `role_permissions`.
5.  Jika tidak ditemukan → **Akses Ditolak**.

---

## 2. Daftar Modul & Aksi yang Tersedia

AMS memiliki **30+ modul** yang bisa dikonfigurasi. Berikut adalah daftar aksi (operasi) yang tersedia:

| Aksi | Keterangan |
|---|---|
| **Access** | Hak untuk melihat/membuka halaman modul. |
| **Create** | Hak untuk menambah data baru. |
| **Update** | Hak untuk mengubah data yang sudah ada. |
| **Delete** | Hak untuk menghapus data. |
| **Approve** | Hak untuk menyetujui/menolak permintaan (Booking, Pengajuan Dana, dll). |
| **Confirm** | Hak untuk mengkonfirmasi penerimaan/penyelesaian. |
| **Report** | Hak untuk melihat atau mencetak laporan. |
| **Receive** | Hak untuk menerima barang (khusus modul Purchase/Logistik). |
| **Take** | Hak untuk mengambil/take-over data (CRM, Purchase). |
| **Monitor** | Hak untuk memonitor progress (khusus modul Garansi). |

> **Catatan:** Tidak semua modul memiliki semua aksi. Misalnya, modul `funnel` dan `log-aktivitas` hanya memiliki aksi **Access** (Read-Only).

### Contoh Modul Utama

| Modul | Aksi yang Tersedia |
|---|---|
| *prospek* | Access, Create, Update, Delete |
| *booking* | Access, Create, Update, Delete, Approve |
| *pengajuan-dana* | Access, Create, Confirm, Approve, Report |
| *purchase* | Access, Create, Update, Delete, Approve, Receive, Take |
| *garansi* | Access, Create, Confirm, Monitor, Approve |
| *siteplan* | Access, Update |
| *funnel* | Access |

---

## 3. Cakupan Data (Scope)

Scope menentukan **batas jangkauan data** yang bisa dilihat oleh user. Setiap modul bisa dikonfigurasi scope-nya secara independen per role.

| Scope | Keterangan | Contoh Penggunaan |
|---|---|---|
| **Assigned Project Only** | User hanya bisa melihat data dari proyek yang di-assign ke akunnya (berdasarkan *project_id* di tabel *user*). | Sales Proyek A hanya melihat prospek Proyek A. |
| **All Projects (HQ)** | User bisa melihat data dari **semua proyek** tanpa batasan. | General Manager, Direktur, Administrator. |
| **Own Data (Marketing)** | User hanya bisa melihat data yang **dia sendiri** buat/input. | Sales junior yang hanya boleh lihat prospek buatannya sendiri. |

> **⚠️ Penting:** Scope berlaku **per modul**. Artinya, seorang Koordinator bisa memiliki scope `All Projects` untuk modul `monitor-prospek` tapi `Assigned Project` untuk modul `booking`. Ini memberikan fleksibilitas tinggi dalam konfigurasi.

---

## 4. Cara Mengonfigurasi Permission

### Langkah-langkah:
1.  Buka menu **Admin > Hak Akses (RBAC)**.
2.  Anda akan melihat daftar semua Role yang terdaftar di AMS.
3.  Klik **Kelola Izin** pada role yang ingin dikonfigurasi.
4.  Di halaman konfigurasi, Anda akan melihat tabel matriks:
    *   **Baris:** Nama Modul/Fitur.
    *   **Kolom:** Aksi (Access, Create, Update, dst).
    *   **Centang (✓):** Tandai aksi yang diizinkan untuk role ini.
    *   **Dropdown Scope (kolom terakhir):** Pilih cakupan data per modul.
5.  Klik **Simpan Hak Akses**.

### Kapan Perubahan Berlaku?
Perubahan permission berlaku **segera**. User yang sedang login akan langsung terdampak saat mereka memuat ulang halaman atau berpindah menu. Tidak perlu logout-login ulang.

---

## FAQ

**Q: Apakah Administrator perlu dikonfigurasi permission-nya?**
> **Tidak perlu.** Role Administrator (ID: 1) memiliki hak akses penuh (*bypass*) ke semua modul dan semua proyek secara otomatis oleh AMS. Konfigurasi permission di halaman ini tidak akan berpengaruh terhadap role Administrator.

**Q: Saya sudah mengaktifkan permission tapi user masih tidak bisa akses. Kenapa?**
> Periksa 3 hal berikut secara berurutan:
> 1. Pastikan aksi **Access** sudah dicentang (ini adalah syarat minimum untuk membuka halaman modul).
> 2. Pastikan **Scope** sudah benar (jika user di Proyek A tapi scope-nya `Own Data`, dia mungkin tidak melihat data siapapun selain miliknya).
> 3. Pastikan user tersebut sudah di-assign ke proyek yang benar di modul **User Management**.

**Q: Bagaimana jika saya ingin membuat role baru?**
> Saat ini, penambahan role baru dilakukan langsung oleh Administrator melalui database (tabel `roles`). Setelah role baru dibuat, Anda bisa langsung mengonfigurasi permission-nya dari halaman ini.

**Q: Apakah perubahan permission dicatat di log?**
> **Ya.** Setiap kali Administrator menyimpan perubahan konfigurasi RBAC, AMS mencatat aktivitasnya di Log Aktivitas dengan tipe `CONFIG`, termasuk nama role yang diubah.
