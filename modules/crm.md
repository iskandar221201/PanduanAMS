# 🎯 Panduan Lengkap: Modul CRM Official

Modul **CRM (Customer Relationship Management)** di AMS dirancang khusus untuk mengelola hubungan dengan konsumen secara lebih profesional dan terpusat. Berbeda dengan *My Leads* yang hanya dilihat oleh Sales masing-masing, CRM Official memberikan pandangan yang lebih luas bagi Supervisor, Manager, dan Admin Official dalam memantau kinerja tim dan progres follow-up.

---

## 1. Dashboard CRM
Halaman utama CRM adalah pusat komando Anda. Di sini Anda bisa melihat apa yang harus dikerjakan hari ini dan memantau kesehatan *pipeline* penjualan.

### A. Navigasi & Filter
*   **Pilih Proyek:** Di pojok kanan atas, Anda bisa memfilter data berdasarkan proyek tertentu.
    *   Jika Anda sales/marketing, Anda hanya akan melihat proyek tempat Anda ditugaskan.
    *   Jika Anda Manager Marketing atau yang memiliki izin, Anda bisa melihat semua proyek (*All Projects*).
*   **Total Official Leads:** Menampilkan jumlah total prospek yang masuk melalui jalur Official (non-kanvas/pribadi sales).

### B. Panel Aktivitas (To-Do List)
Sistem otomatis mengelompokkan tugas Anda menjadi dua bagian penting:
1.  **🚨 Overdue Activities (Terlewat):**
    *   Daftar tugas yang *seharusnya* sudah dikerjakan kemarin atau hari-hari sebelumnya tapi belum ditandai selesai.
    *   **Prioritas:** TINGGI. Segera selesaikan tugas di daftar ini agar konsumen merasa diperhatikan.
2.  **📅 Today's Activities (Hari Ini):**
    *   Daftar tugas yang dijadwalkan untuk hari ini.
    *   Fokus Anda hari ini adalah menuntaskan daftar ini sampai bersih (kosong).

---

## 2. Detail CRM & Interaksi Konsumen
Klik tombol **Detail** (ikon mata) pada salah satu nama prospek untuk masuk ke halaman kerja.

### A. Informasi Prospek
Menampilkan data lengkap konsumen:
*   Nama, No Telepon (klik untuk langsung WA), Alamat.
*   Status Terkini (Hot, Cold, Booking, dll).
*   Sales/Marketing yang menangani (PIC).

### B. Tab Riwayat Catatan (Notes)
Gunakan tab ini untuk mencatat **informasi statis** atau fakta penting tentang konsumen yang perlu diingat oleh tim.
*   *Contoh:* "Ibu ini suka unit hadap utara", "Suami kerja di pertambangan, hanya bisa dihubungi weekend", "Budget max 500jt".
*   **Cara Pakai:** Ketik catatan di kolom teks > Klik **Simpan Catatan**.
*   Catatan ini tidak memiliki tanggal jatuh tempo (bukan reminder).

### C. Tab Aktivitas & Penjadwalan (Action Plan)
Ini adalah fitur inti CRM. Gunakan untuk merencanakan langkah selanjutnya (*Next Action*).

**Cara Membuat Jadwal Follow-Up:**
1.  Buka Tab **Aktivitas**.
2.  Isi Form **Tambah Aktivitas Baru**:
    *   **Jenis:** Pilih metode interaksi (Telepon, Chat WA, Kunjungan/Visit, Meeting Kantor).
    *   **Jadwal:** Tentukan Tanggal dan Jam kapan Anda akan melakukan aksi ini.
    *   **Deskripsi:** Rencana apa yang mau dibahas? (Misal: "Konfirmasi jadi booking atau tidak").
3.  Klik **Simpan**.
4.  Jadwal ini akan otomatis muncul di *Dashboard CRM* Anda pada tanggal tersebut.

**Cara Menandai Selesai (Complete):**
Setelah Anda selesai menelepon atau bertemu konsumen:
1.  Lihat daftar aktivitas di bagian bawah tab.
2.  Klik tombol **✅ Tandai Selesai** (ikon centang).
3.  Aktivitas akan pindah ke riwayat "Selesai" dan hilang dari daftar tanggungan.

---

## 3. Fitur "Assign Prospek" 
Fitur ini khusus untuk **Admin, Supervisor, atau Manager**. Berfungsi untuk mendistribusikan data prospek baru (biasanya dari iklan/pameran) kepada Sales/Marketing tertentu.

**Langkah-langkah:**
1.  Di halaman utama CRM, klik tombol hijau **+ Asign / Assign Prospek Baru**.
2.  **Pilih Marketing:** Pilih nama sales yang akan bertanggung jawab (PIC).
    *   *Tips:* Sales yang muncul hanya mereka yang bertugas di proyek yang sama dengan Anda/Proyek terpilih.
3.  **Isi Data Konsumen:**
    *   Nama, No WA, Alamat.
4.  Klik **Simpan & Assign**.

**Apa yang terjadi setelah Assign?**
*   Data prospek akan masuk ke akun Sales tersebut.
*   Sales tersebut akan menerima **Notifikasi** di sistem bahwa dia mendapatkan "tugas baru".
*   Sales wajib segera melakukan follow-up dan mengupdate statusnya.

---

## Tips Penggunaan CRM yang Efektif

1.  **Zero Inbox Mindset:** Usahakan panel *Overdue Activities* selalu kosong setiap pagi.
2.  **Selalu Buat Next Action:** Setiap kali selesai menghubungi konsumen, tanyakan pada diri sendiri: *"Kapan saya harus hubungi lagi?"*. Langsung buat jadwal aktivitas baru di sistem. Jangan biarkan prospek "menggantung" tanpa jadwal selanjutnya.
3.  **Catat Detail:** Semakin detail catatan Anda (hobi anak, pekerjaan istri, dll), semakin personal pendekatan Anda, dan semakin besar peluang closing.

---

## FAQ (Pertanyaan Umum)

**Q: Saya sales, kok tidak bisa buka menu "Assign Prospek"?**
> Fitur *Assign Leads* dibatasi hak aksesnya *Permissions: crm.assign*. Biasanya hanya Admin atau Manager yang boleh membagi-bagikan leads agar adil.

**Q: Apakah saya bisa melihat Catatan yang dibuat sales lain?**
> Tergantung *Scope* akses Anda.
*   Jika akses Anda *Own Data*, Anda hanya lihat data sendiri.
*   Jika akses Anda *Assigned Project* (Manager), Anda bisa melihat catatan semua sales di proyek Anda.

**Q: Apa bedanya "Catatan" dan "Aktivitas"?**
> *   **Catatan** = Info penting untuk dibaca (Tidak ada deadline).
> *   **Aktivitas** = Tugas yang harus dikerjakan (Ada deadline/jadwal).
