# 🔐 Dokumentasi Modul Auth Delete (Authorization Manager)

Modul **Auth Delete** adalah sistem tambahan di AMS yang berfungsi sebagai "Kunci Ganda" untuk penghapusan data krusial. Modul ini dirancang agar data yang memiliki dampak finansial atau operasional besar tidak dihapus secara sepihak oleh staf, melainkan harus melalui persetujuan digital dari pimpinan.

Modul ini digunakan secara eksklusif oleh **Direktur** dan **General Manager**.

---

## 🚀 Fitur Unggulan 

### 1. Secure Access (PIN 2FA)
Akses ke modul ini dilindungi oleh PIN rahasia yang terpisah dari *password* login akun. Ini memberikan lapisan keamanan tambahan jika akun pimpinan disalahgunakan oleh pihak lain.
*   **Encrypted PIN:** PIN disimpan menggunakan algoritma enkripsi modern.
*   **Auto-Timeout:** Sesi Secure Access akan otomatis berakhir jika tidak ada aktivitas selama 15 menit.

> Administrator tidak dapat mengubah PIN

### 2. Guarded Modules (Modul yang Dilindungi)
Saat ini, AMS melindungi 5 entitas data utama yang tidak bisa dihapus tanpa izin pimpinan:
*   **Pencatatan Keuangan (Pembayaran):** Mencegah penghapusan riwayat uang masuk secara ilegal.
*   **Unit Kavling:** Mencegah penghapusan stok properti secara sembarangan.
*   **Target Konstruksi:** Menjaga integritas riwayat progres pembangunan.
*   **Berita Acara Serah Terima (BAST):** Melindungi bukti legalitas serah terima unit.
*   **Booking Unit:** Mencegah manipulasi data antrian konsumen.

### 3. Anti-Brute Force Protection
Sistem dilengkapi dengan pembatas percobaan (*throttling*). Jika terjadi kesalahan input PIN sebanyak 3 kali berturut-turut, akses akan diblokir selama 5 menit untuk mencegah upaya pembobolan.

### 4. Audit Trail Lengkap
Setiap pemberian izin (*grant*) dan pencabutan izin (*revoke*) otomatis dicatat dalam **Log Aktivitas AMS** lengkap dengan stempel waktu, nama pimpinan, dan ID data yang diizinkan untuk dihapus.

---

## 🛠️ Langkah Penggunaan (Step-by-Step)

### Tahap 1: Setup PIN (Hanya untuk Pertama Kali)
Jika Anda baru pertama kali mengakses menu ini:
1.  Klik menu **Auth Delete** di panel Admin.
2.  AMS akan mendeteksi bahwa PIN belum dibuat.
3.  Masukkan 4-6 digit angka PIN baru Anda.
4.  Masukkan kembali untuk konfirmasi, lalu klik **Simpan & Aktivasi**.

### Tahap 2: Login Secure Access
Setiap kali Anda ingin masuk ke halaman otorisasi:
1.  Buka menu **Auth Delete**.
2.  Masukkan PIN Secure Access Anda.
3.  Klik **Buka Akses**.

### Tahap 3: Memberikan Izin Hapus (Grant Permission)
Jika ada staf yang mengajukan penghapusan data (misal: "Salah input pembayaran sebesar Rp 1.000.000"):
1.  Minta **ID Data** dan **Modul** yang bersangkutan dari staf tersebut.
2.  Di halaman Auth Delete, klik tombol **+ Berikan Izin Baru**.
3.  Pilih **Module** (Contoh: *Pencatatan Keuangan*).
4.  Masukkan **Reference ID** (ID yang diberikan staf).
5.  Masukkan kembali **PIN** Anda sebagai konfirmasi akhir.
6.  Klik **Grant Permission**.
7.  Beritahu staf bahwa izin sudah diberikan. Staf kini bisa mengklik tombol "Hapus" pada data tersebut di menu asalnya.

### Tahap 4: Mencabut Izin (Revoke)
Jika izin sudah diberikan namun ternyata batal dihapus atau pimpinan berubah pikiran:
1.  Lihat daftar **Active Authorizations** di tabel utama.
2.  Klik tombol **Revoke** (warna merah) pada baris yang diinginkan.
3.  Izin akan hangus seketika dan data kembali terkunci dari penghapusan.

---

## 🛡️ Validasi & Aturan AMS

1.  **Strict Role Access:** Hanya pengguna dengan Level Direktur (Role 13) dan General Manager (Role 15) yang dapat melihat dan login ke menu ini.
2.  **ID Validation:** AMS otomatis mengecek apakah ID yang Anda masukkan benar-benar ada di modul tersebut. Anda tidak bisa memberikan izin untuk ID gaib/palsu.
3.  **One-Time Use (Ideal):** Izin didesain untuk satu kali pakai. Setelah staf melakukan penghapusan, status izin akan berubah menjadi *Used* atau otomatis tidak berlaku lagi.
4.  **IP Tracking:** Sistem mencatat alamat IP setiap kali ada upaya verifikasi PIN untuk pemantauan keamanan.

---

## ❓ FAQ (Troubleshooting)

**Q: Saya lupa PIN Secure Access saya. Bagaimana cara reset?**
> Untuk alasan keamanan, PIN tidak bisa direset sendiri melalui menu "Lupa Password". Hubungi Admin Database/Developer untuk melakukan reset manual melalui backend.

**Q: Staf saya menginfokan sudah klik hapus, tapi muncul pesan "Unauthorized". Apa penyebabnya?**
> Pastikan ID yang Anda beri izin PAS dan SAMA dengan yang staf tersebut ingin hapus. Cek kembali kolom Module dan Reference ID-nya. Pastikan juga izin tersebut statusnya masih *Active* (belum di-revoke).

**Q: Apakah PIN Secure Access sama dengan password login?**
> **TIDAK.** Sangat disarankan untuk membuat PIN yang berbeda dengan password login akun Anda demi keamanan maksimal.

**Q: Berapa lama izin ini berlaku?**
> Izin akan terus aktif sampai staf melakukan eksekusi penghapusan atau Anda mencabutnya secara manual (*Revoke*).
