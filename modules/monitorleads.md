# 📊 Panduan Modul Monitoring Prospek

Modul **Monitoring Prospek** adalah pusat data yang memungkinkan Supervisor dan Manager memantau kinerja seluruh anggota tim marketing dalam satu tampilan terpadu. Berbeda dengan daftar prospek biasa, modul ini dilengkapi filter canggih untuk analisis data yang lebih mendalam.

Fitur ini sangat berguna untuk:
1.  **Evaluasi Kinerja:** Melihat berapa banyak prospek yang didapat setiap marketing.
2.  **Audit Data:** Memastikan tidak ada prospek yang terbengkalai (status tidak update).
3.  **Remarketing (Blast WA):** Memilih sekumpulan prospek spesifik untuk dikirimi pesan massal.

---

## A. Navigasi & Filter Data

Halaman Monitoring (`monitor/index`) menyediakan panel filter lengkap di bagian atas.

### 1. Filter Berdasarkan Kriteria
Anda bisa menyaring data berdasarkan kombinasi berikut:
*   **Periode Tanggal:** Rentang waktu prospek masuk (Default: Bulan ini).
*   **Status:** Saring berdasarkan tahapan (Misal: Hanya tampilkan yang *Hot* atau *Booking*).
*   **Marketing:** Pilih nama marketing tertentu untuk melihat kinerjanya.
*   **Sumber:** Analisis efektivitas kanal marketing (Misal: Berapa banyak leads dari *Facebook Ads* vs *Pameran*).

### 2. Ekspor Laporan
Di pojok kanan atas tabel, terdapat tombol ekspor instan:
*   **Excel:** Mengunduh data tabel ke format `.xlsx` untuk diolah lebih lanjut.
*   **PDF:** Mencetak laporan siap saji dalam format landscape.
*   **Print:** Mencetak langsung ke printer.

---

## B. Integrasi WhatsApp Blast (Siaran Pesan)

Salah satu kekuatan utama modul Monitoring adalah integrasinya dengan fitur **WhatsApp Blast**. Anda bisa menyeleksi audiens target dari sini sebelum mengirim pesan massal.

### Skenario Penggunaan:
*   *Menhubungi ulang 50 prospek "Cold" bulan lalu dengan promo baru.*
*   *Mengirim ucapan terima kasih kepada seluruh konsumen yang sudah "Booking".*
*   *Follow-up massal kepada leads yang masih berstatus "New".*

### Langkah-langkah Blast dari Monitoring:

1.  **Filter Data Dulu:**
    Gunakan filter untuk menampilkan target audiens Anda.
    *   *Contoh:* Set Filter Status = **Hot**, marketing = **Semua**, Tanggal = **Bulan Lalu**.
2.  **Pilih Prospek:**
    *   Centang kotak (*checkbox*) di sebelah kiri nama prospek yang ingin dikirimi pesan.
    *   Atau centang **Pilih Semua** di judul kolom untuk memilih satu halaman sekaligus.
3.  **Klik Tombol "Blast Terpilih":**
    *   Tombol ini ada di deretan tombol ekspor (warna biru kemerahan).
    *   Sistem akan mengarahkan Anda ke halaman **Buat Kampanye Blast**.
4.  **Konfigurasi Pesan:**
    *   Di halaman Blast, daftar prospek yang Anda pilih tadi sudah otomatis masuk ke daftar penerima.
    *   Anda tinggal menulis nama kampanye dan isi pesan (bisa pakai template).
5.  **Kirim:**
    *   Klik Simpan/Kirim untuk mulai memproses antrian pesan.

---

## C. Pivot Report (Analisis Data Lanjutan)

Selain tabel daftar, modul Monitoring menyediakan fitur **Pivot Report** — sebuah tabel analisis interaktif yang memungkinkan Anda mengolah data prospek dari berbagai sudut pandang tanpa perlu aplikasi spreadsheet terpisah.

### Cara Mengakses:
1.  Di halaman utama Monitoring Prospek, klik tombol **📊 Pivot Report** di pojok kanan atas (di sebelah judul halaman).

### Fitur Pivot:
Halaman Pivot menampilkan tabel interaktif yang bisa Anda konfigurasi sendiri:

*   **Baris (Rows):** Pilih dimensi untuk baris tabel. Misalnya: *Status*, *Marketing*, *Sumber Leads*.
*   **Kolom (Cols):** Pilih dimensi untuk kolom. Misalnya: *Bulan Input*, *Project*.
*   **Nilai (Values):** Data yang dihitung. Default: *Jumlah (Count)* prospek.
*   **Filter:** Klik pada label dimensi untuk menyaring hanya data tertentu.

### Contoh Analisis yang Bisa Dilakukan:
| Analisis | Baris | Kolom | Hasil |
| :--- | :--- | :--- | :--- |
| Kinerja marketing per Bulan | Marketing | Bulan Input | Berapa leads tiap marketing per bulan |
| Efektivitas Kanal | Sumber Leads | Status | Berapa persen leads dari FB Ads yang jadi Booking |
| Perbandingan Project | Project | Status | Project mana yang paling banyak leads Hot |

### Toolbar Pivot:
*   **🔄 Refresh Data:** Memuat ulang data terbaru dari database.
*   **📄 Download PDF:** Mengunduh tampilan pivot saat ini sebagai file PDF.
*   **⬅ Kembali:** Kembali ke halaman Monitoring utama.

---

## FAQ (Tanya Jawab)

**Q: Kenapa saya tidak bisa melihat pilihan "Semua Project"?**
> Akses data dibatasi oleh *Role* Anda. Hanya Direksi dan Admin Pusat yang bisa melihat lintas proyek (*All Projects Scope*). Supervisor hanya bisa melihat data satu proyek yang dikelolanya.

**Q: Apakah marketing bisa melihat modul ini?**
> Bisa, namun _data scope_-nya terbatas pada prospek milik sendiri.

**Q: Berapa batas maksimal prospek yang bisa di-blast sekaligus?**
> Secara teknis tidak dibatasi, tapi disarankan membagi dalam *batch* kecil (misal per 50-100 nomor) untuk menghindari blokir WhatsApp dan agar tim marketing siap membalas respon yang masuk bersamaan.
