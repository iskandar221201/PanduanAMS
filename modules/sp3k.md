# 💳 Panduan Modul Data SP3K

Modul ini digunakan oleh **Admin KPR** untuk mendata rincian persetujuan kredit (SP3K) yang telah diterbitkan oleh Bank. Data ini sangat krusial karena menjadi dasar perhitungan pencairan dana (KPR) di modul Keuangan.

## 1. Fungsi Utama

Halaman utama menampilkan daftar konsumen yang status transaksinya telah mencapai tahap **'SP3K'**.
*   **Monitoring Nominal:** Melihat berapa nilai plafon kredit yang disetujui Bank.
*   **Arsip Digital:** Menyimpan softcopy surat SP3K agar mudah diakses/didownload kapan saja.

---

## 2. Input Data SP3K

Saat surat SP3K dari Bank turun, Admin KPR wajib segera melengkapi data di sistem AMS.

### Form Input/Edit
1.  Klik tombol **Input** (atau **Edit**) pada baris konsumen yang bersangkutan.
2.  **Nominal SP3K:** Masukkan angka plafon kredit *real* yang disetujui Bank (ini bisa berbeda dengan harga jual awal).
    *   *Sistem otomatis memformat angka menjadi format Rupiah saat Anda mengetik.*
3.  **Upload File:** Unggah scan dokumen SP3K (PDF/Gambar, Max 2MB) sebagai bukti otentik.
4.  Klik **Simpan**.

### ⚠️ Hubungan dengan Pencatatan Keuangan (Suggestion System)

Nilai yang Anda input di kolom **Nominal SP3K** memiliki dampak langsung ke modul **Pencatatan Keuangan**.

*   **Logika Suggestion:**
    Saat Admin Keuangan melalukan input transaksi pencairan KPR, AMS akan memberikan **Saran Nominal (Suggest)** berdasarkan data ini.
*   **Contoh Kasus:**
    *   Harga Unit: Rp 500 Juta.
    *   Admin KPR menginput Nominal SP3K: **Rp 480 Juta** (Plafon turun).
    *   Maka di modul Keuangan, target penerimaan KPR akan otomatis di-adjust menjadi Rp 480 Juta, bukan lagi Rp 500 Juta.
    *   Selisihnya harus ditagihkan ke konsumen sebagai **Penambahan DP/Biaya Lainnya** (jika ada) atau dianggap sebagai pengurangan omset.

> **PENTING:** Pastikan input Nominal SP3K 100% akurat sesuai surat Bank, karena kesalahan input akan menyebabkan selisih perhitungan di laporan keuangan marketing dan piutang.

---

## FAQ

**Q: Apakah saya bisa menghapus data SP3K?**
> Tidak bisa dihapus, hanya bisa **diedit**. Jika terjadi kesalahan input nominal atau salah upload file, cukup gunakan tombol **Edit** untuk mengoreksinya.

**Q: Bagaimana jika konsumen Pindah Bank setelah input SP3K?**
> Silahkan ubah status transaksi kembali ke **'Proses Bank'** atau **'Pindah Bank'**. Data SP3K lama akan tetap tersimpan di database namun tidak aktif/tampil di list utama sampai statusnya kembali ke SP3K.
