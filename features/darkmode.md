# 🌙 Fitur Dark Mode (AMS)

AMS hadir dengan dukungan **Dark Mode** yang dirancang untuk kenyamanan mata pengguna saat bekerja dalam waktu lama atau di lingkungan minim cahaya.
---

## 🚀 Fitur Unggulan (Powerful Features)

### 1. Intelligent Hybrid Engine
AMS menggunakan kombinasi dua teknologi untuk menyajikan tampilan gelap yang sempurna:
*   **Dynamic Theme Generation:** Menggunakan pustaka *DarkReader* untuk memproses elemen konten dinamis secara *on-the-fly*.
*   **Custom CSS Variables:** AMS memiliki variabel CSS khusus (`--bg-primary`, `--text-primary`, dll.) untuk memastikan komponen utama seperti Dashboard, Tabel, dan Card memiliki kontras yang presisi dan estetika yang premium.

### 2. Flicker-Free Initialization (Anti-Flash)
Salah satu keunggulan AMS adalah hilangnya "kilatan putih" saat berpindah halaman dalam mode gelap. Sistem mencegat proses rendering di tingkat paling awal (di dalam `<head>`) untuk langsung menerapkan tema gelap jika pengguna sebelumnya telah memilihnya.

### 3. Smart High-Contrast Components
Warna-warna peringatan dan status disesuaikan secara cerdas:
*   **Badges:** Warna hijau, merah, dan kuning diubah menjadi versi "Pulsing Glow" yang lebih cerah sehingga tetap mudah dibaca namun tidak menyilaukan di latar belakang gelap.
*   **DataTables:** Baris belang (*striped rows*) dan teks pencarian dioptimalkan agar data besar tetap nyaman dipindai.
*   **Logo Adaptive:** Logo AMS secara otomatis berubah menjadi putih/monokrom melalui filter CSS saat mode gelap aktif.

### 4. Third-Party Integration
Tema gelap tidak hanya berlaku pada AMS, tapi juga menyentuh komponen pihak ketiga:
*   **JQuery UI Datepicker:** Kalender tanggal otomatis berubah menjadi gelap.
*   **Autocomplete Menu:** Daftar pilihan otomatis menyesuaikan warna tema.
*   **Summernote Editor:** Editor teks kaya (Rich Text) tetap nyaman digunakan.

---

## 🛠️ Cara Penggunaan

1.  **Aktifkan Togle:** Klik ikon **Bulan/Matahari** pada bagian pojok kanan atas di samping ikon lonceng notifikasi.
2.  **Auto-Save:** Pilihan Anda akan disimpan secara permanen di browser. Saat Anda login kembali besok atau lusa, AMS akan tetap berada di mode terakhir yang Anda pilih.
3.  **Visual Feedback:** Sistem akan melakukan transisi halus (*smooth transition*) selama 0.3 detik untuk memberikan efek visual yang elegan saat berpindah tema.

---

## 🛡️ Aturan & Validasi Visual

1.  **Softer Dark Policy:** AMS tidak menggunakan warna hitam pekat (`#000000`) melainkan warna *Deep Navy/Grey* (`#1a1d23`) untuk mengurangi kelelahan mata (*Eye Strain*).
2.  **Element Isolation:** Elemen gambar seperti foto progres konstruksi atau bukti transfer tidak akan terkena filter warna gelap agar dokumen tetap terlihat asli dan akurat.
3.  **Brightness Buffer:** Komponen yang memiliki teks putih (seperti Navbar) akan memiliki bayangan (*shadow*) yang lebih dalam di mode gelap untuk mempertahankan kesan *Glassmorphism*.

---

## ⌨️ Tips & Shortcut

| Kebutuhan | Cara |
| :--- | :--- |
| **Cek Mode Cepat** | Lihat warna teks di Navbar. Jika teks putih dan latar gelap, Anda di Mode Gelap. |
| **Reset ke Light Mode** | Klik kembali ikon Matahari di toolbar atas. |
| **Masalah Tampilan** | Jika ada bagian yang terlihat aneh, coba lakukan *Force Reload* (`Ctrl + F5`) untuk menyegarkan cache CSS Dark Mode. |

---

## ❓ FAQ

**Q: Apakah Dark Mode menghemat baterai?**
> A: Ya, pada perangkat dengan layar OLED/AMOLED (seperti smartphone modern), Dark Mode AMS dapat membantu menghemat konsumsi daya karena piksel gelap menggunakan lebih sedikit energi.

**Q: Mengapa logo perusahaan menjadi putih di mode gelap?**
> A: Ini adalah fitur *Smart Filtering* AMS agar brand tetap terlihat jelas dan kontras. Tanpa fitur ini, logo berwarna hijau tua mungkin akan "tenggelam" di latar belakang gelap.

**Q: Apakah saya harus mengaktifkan Dark Mode setiap kali login?**
> A: Tidak. AMS mengingat preferensi Anda berdasarkan perangkat yang Anda gunakan.
