# 💰 Panduan Modul Harga Kavling (Price List Management)

Modul ini berfungsi sebagai **Master Data Harga** di AMS. Berbeda dengan input harga manual, modul ini mewajibkan Anda merinci komponen harga (Booking, DP, KPR/SP3K, dll) sehingga **Harga Jual Total** dihitung secara otomatis dan transparan.

## 1. Konsep Dasar Penetapan Harga

Di AMS, harga unit **BUKAN** sekadar satu angka gelondongan. Harga disusun dari beberapa komponen biaya:

| Komponen | Penjelasan |
|---|---|
| **Booking Fee** | Tanda jadi pemesanan unit. |
| **DP (Uang Muka)** | Down Payment yang harus dibayar konsumen. |
| **SP3K Full** | plafon KPR maksimal (jika pembelian KPR). |
| **Biaya Hook** | Tambahan harga untuk unit pojok/sudut. |
| **Kelebihan Tanah** | Biaya tambahan jika luas tanah realisasi > standar. |
| **SBUM** | Subsidi Bantuan Uang Muka (jika ada). |
| **Lainnya** | Biaya administrasi atau tambahan lain. |

> **Rumus Otomatis:**
> `Harga Jual Total = Booking + DP + SP3K + Hook + Kelebihan Tanah + SBUM + Lainnya`

---

## 2. Fitur Utama

### Menetapkan Harga Baru
1.  Buka menu **Harga Kavling**.
2.  Pilih Proyek (jika Anda memiliki akses lebih dari satu proyek).
3.  Cari unit yang belum memiliki harga (baris berwarna kuning/kosong), klik tombol **Set**.
4.  Isi rincian komponen biaya (Booking, DP, dll).
5.  Kolom **Harga Jual** akan terisi otomatis dan terkunci (readonly).
6.  Klik **Simpan Harga**.

### Mengupdate Harga
1.  Klik tombol **Edit** (ikon pensil) pada unit yang sudah ada harganya.
2.  Ubah komponen biaya yang diinginkan.
3.  Harga Jual Total akan otomatis dikalkulasi ulang.
4.  **PENTING:** Perubahan ini akan berdampak pada laporan keuangan (baca bagian Integrasi di bawah).

*Catatan:* Aksi ini tercatat di Log Aktivitas.

---

## 3. Integrasi dengan Modul Lain

Modul Harga Kavling sangat krusial karena terhubung langsung dengan modul-modul berikut:

### a. Integrasi ke Modul Kavling (Stok)
Setiap kali Anda menyimpan harga di sini, sistem otomatis mengupdate kolom `harga` di tabel **Master Kavling**. Jadi, harga yang muncul saat sales melihat stok unit adalah harga terbaru dari modul ini.

### b. Integrasi ke Pencatatan Keuangan (Financial Records) ⚠️
Ini adalah fitur cerdas AMS. Jika unit yang harganya Anda ubah **sudah memiliki catatan keuangan** (sudah terjual/sedang dicicil):
1.  Sistem mendeteksi adanya perubahan harga.
2.  Sistem menghitung selisih harga (Baru - Lama).
3.  Sistem **secara otomatis mengupdate** nilai total piutang konsumen tersebut di modul `Pencatatan Keuangan`.
    *   *Contoh:* Konsumen A sudah beli unit seharga 500jt. Manajemen menaikkan harga unit tersebut jadi 550jt karena ada penambahan bangunan. Saat Anda update di sini, tagihan konsumen A otomatis naik 50jt.

> **Tips:** Hati-hati mengubah harga untuk unit yang sudah terjual (Sold). Pastikan perubahan tersebut memang disepakati dengan konsumen (misal: addendum).

---

## FAQ

**Q: Mengapa saya tidak bisa mengetik langsung di kolom Harga Jual?**
> **Sengaja dikunci.** AMS memaksa Anda merinci komponennya agar laporan keuangan nanti rapi. Anda tidak bisa bikin harga "asal tembak" tanpa jelas alokasinya (berapa untuk DP, berapa untuk KPR, dll).

**Q: Bagaimana kalau penjualannya Cash Keras (Tanpa KPR)?**
> Cukup isi komponen **Booking Fee** dan **DP** (atau **Biaya Lainnya**) hingga totalnya senilai harga unit. Kosongkan kolom SP3K.

**Q: Saya salah input harga untuk unit yang sudah lunas. Apakah data keuangannya akan rusak?**
> **Iya.** Jika Anda mengubah harga unit yang sudah `Lunas`, sistem akan menambah/mengurang piutang, sehingga statusnya bisa berubah jadi `Belum Lunas` (minus/kurang bayar). **Selalu konfirmasi dengan Tim Keuangan sebelum mengubah harga unit Sold.**

**Q: Siapa yang berhak mengubah harga?**
> Secara default, hanya **Project Manager** dan **Administrator** yang memiliki akses edit harga. Marketing/Sales hanya memiliki akses *View Only* (Melihat daftar harga).
