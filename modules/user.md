# 👤 Panduan Modul Manajemen Pengguna (User Management)

Modul ini digunakan oleh **Administrator** untuk mengelola seluruh akun pengguna yang memiliki akses ke AMS. Di sinilah identitas, peran (role), penugasan proyek, dan status aktivasi setiap user dikonfigurasi.

## 1. Konsep Peran (Role) dan Keterkaitan dengan AMS

Setiap pengguna di AMS **wajib** memiliki satu **Role (Peran)**. Role inilah yang menentukan:
*   **Menu apa saja** yang bisa diakses oleh user.
*   **Data proyek mana** yang bisa dilihat (tergantung penugasan proyek).
*   **Aksi apa** yang diizinkan (Create, Read, Update, Delete) di setiap modul.

### Mekanisme Otorisasi
AMS menggunakan sistem **Permission berbasis Role**. Setiap role memiliki konfigurasi hak akses yang sudah ditentukan di database (tabel `roles` dan `role_permissions`). Ketika user login, AMS membaca `role_id` miliknya dan menerapkan filter data serta akses menu secara otomatis.

### Penugasan Proyek (Project Scope)
*   **User dengan Proyek Spesifik:** Jika `project_id` diisi (misal: Proyek A), maka user tersebut **hanya** bisa melihat dan mengelola data milik Proyek A. Contoh: Sales yang hanya bertugas di satu perumahan tertentu.
*   **User Global / HO:** Jika `project_id` dikosongkan, user dianggap sebagai **Head Office (HO)** atau **Global**. User ini berpotensi mengakses data dari semua proyek, tergantung role-nya. Contoh: Administrator, General Manager, Direktur.

### Pembatasan Role Khusus (Single-User)
Untuk menjaga keamanan dan integritas struktur organisasi, AMS menerapkan aturan bahwa role tertentu **hanya boleh dimiliki oleh 1 user aktif** pada satu waktu:

| Role ID | Nama Role | Batasan |
|---|---|---|
| 13 | General Manager | Maks 1 user aktif |
| 15 | Direktur | Maks 1 user aktif |
| 16 | Owner | Maks 1 user aktif |

Jika Anda mencoba mengaktifkan user baru dengan salah satu role di atas sementara sudah ada user aktif lain dengan role yang sama, AMS akan **menolak** dan menampilkan pesan peringatan. Anda harus menonaktifkan user lama terlebih dahulu.

---

## 2. Fitur Utama

### Menambah Pengguna Baru
1.  Klik **Tambah Pengguna** di pojok kanan atas.
2.  Isi data pada modal form:
    *   **Username:** Harus unik, minimal 3 karakter. Digunakan untuk login.
    *   **Nama Lengkap:** Nama asli user (ditampilkan di berbagai laporan AMS).
    *   **Peran (Role):** Pilih dari daftar role yang tersedia.
    *   **Penugasan Proyek:** Pilih proyek spesifik atau kosongkan untuk Global/HO.
    *   **Password:** Minimal 6 karakter.
    *   **Status Aktif:** Centang untuk mengizinkan user login.
3.  Klik **Simpan Pengguna**.

### Mengubah (Edit) Pengguna
1.  Klik ikon **Pensil (Kuning)** pada baris user yang ingin diedit.
2.  Modal form akan terbuka dengan data yang sudah terisi.
3.  Ubah data yang diperlukan:
    *   Password boleh dikosongkan jika tidak ingin mengubahnya.
    *   Anda bisa memindahkan user ke proyek lain atau mengubah role-nya.
4.  Klik **Simpan Pengguna**.

*Catatan: Setiap perubahan data user akan tercatat di Log Aktivitas AMS beserta detail field yang berubah (misal: "Role ID diubah dari 3 menjadi 5").*

### Menghapus Pengguna
AMS memiliki **Fitur Keamanan Penghapusan** untuk user. Sebelum menghapus, AMS akan mengecek apakah user tersebut memiliki keterikatan data transaksi di:
*   **Tabel Prospek** — Sebagai `created_by_user_id` (yang menginput prospek).
*   **Tabel Booking** — Sebagai `sales_id` (sales yang menghandle booking).

Jika ditemukan keterikatan, AMS akan **menolak penghapusan** dan menampilkan detail jumlah data yang terikat. Hal ini untuk mencegah data transaksi kehilangan referensi ke user yang bertanggung jawab.

> **💡 Tips:** Jika user sudah resign tapi masih memiliki data transaksi, gunakan fitur **Nonaktifkan** (matikan centang "Aktifkan Pengguna") alih-alih menghapus akunnya. Dengan cara ini, akun tidak bisa login tapi data historis tetap terjaga.

---

## 3. Status Aktif / Non-aktif

| Status | Efek |
|---|---|
| **Aktif** ✅ | User dapat login dan menggunakan AMS sesuai role-nya. |
| **Non-aktif** ❌ | User **tidak bisa login** sama sekali. Data historisnya tetap tersimpan dan tetap muncul di laporan/rekap yang relevan. |

---

## FAQ

**Q: Saya ingin mengganti sales yang handle konsumen tertentu. Bagaimana caranya?**
> Perubahan penanggungjawab sales tidak dilakukan di modul User, melainkan di modul **Booking** (edit data booking untuk mengganti `sales_id`). Modul User hanya mengatur identitas dan akses login, bukan assignment transaksi.

**Q: User sudah dinonaktifkan, tapi namanya masih muncul di laporan. Apakah ini bug?**
> Bukan bug. Ini adalah desain AMS yang disengaja (*by design*). Data historis seperti "Sales: Budi" pada rekap booking akan tetap menampilkan nama Budi meskipun akunnya sudah non-aktif. Ini penting untuk audit trail dan akurasi laporan masa lalu.

**Q: Mengapa saya tidak bisa menghapus user tertentu?**
> Karena user tersebut masih memiliki data transaksi aktif (Prospek atau Booking). AMS akan menampilkan detail keterikatan, misalnya: *"Prospek (5 data), Booking (3 data)"*. Anda perlu memindahkan data-data tersebut ke user lain terlebih dahulu, atau cukup nonaktifkan akunnya saja.

**Q: Apa yang terjadi jika saya mengubah role user yang sedang login?**
> Perubahan role akan berlaku pada **sesi login berikutnya**. User tersebut perlu logout dan login kembali agar hak akses barunya diterapkan oleh AMS.
