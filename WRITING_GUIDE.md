# Panduan Kontribusi Dokumentasi

Panduan ini menjelaskan cara menambahkan halaman baru, mengedit konten, dan memelihara dokumentasi AMS.

## Menambahkan Halaman Baru

1.  **Buat File Markdown**: Buat file `.md` baru di direktori yang sesuai (misalnya, `modules/fitur-baru.md`).
2.  **Tambahkan Konten**: Tulis dokumentasi Anda menggunakan Markdown standar.
3.  **Perbarui Sidebar**: Buka `_sidebar.md` dan tambahkan tautan ke file baru Anda.

    ```markdown
    * **Bagian Baru**
      * [Judul Fitur Baru](modules/fitur-baru.md)
    ```

## Dasar-Dasar Markdown

### Judul
Gunakan `#` untuk judul utama dan `##` untuk judul bagian.

```markdown
# Judul Halaman
## Judul Bagian
### Judul Sub-bagian
```

### Pemformatan
- **Tebal**: `**teks**` -> **teks**
- *Miring*: `*teks*` -> *teks*
- `Kode`: `` `teks` `` -> `teks`

### Daftar
- Daftar berpoin: Gunakan `-` atau `*`
- Daftar bernomor: Gunakan `1.`

### Tautan dan Gambar
- Tautan: `[Teks Tautan](url)`
- Gambar: `![Teks Alt](path/ke/gambar.png)`

> [!TIP]
> **Tips Folder Gambar:**
> - Jika file Markdown Anda ada di **root** (seperti `README.md`), gunakan: `![ket](img/namafile.png)`
> - Jika file Markdown Anda ada di **dalam folder** (seperti `modules/finance.md`), Anda harus "keluar" dulu satu level menggunakan `..`: `![ket](../img/namafile.png)`


## Fitur Lanjutan

### Peringatan (Alerts)
Anda dapat menggunakan blockquotes khusus untuk peringatan:

```markdown
> [!NOTE]
> Ini adalah catatan.

> [!TIP]
> Ini adalah tip.

> [!WARNING]
> Ini adalah peringatan.
```

### Blok Kode
Gunakan tiga backticks untuk potongan kode:

```javascript
function hello() {
  console.log("Halo Dunia");
}
```

## Pratinjau Perubahan Anda

Karena Docsify mengambil file secara dinamis, Anda mungkin memerlukan server lokal untuk melihat perubahan dengan benar karena pengaturan keamanan browser (CORS).

**Metode 1: VS Code Live Server**
1.  Instal ekstensi "Live Server".
2.  Klik kanan `index.html` dan pilih "Open with Live Server".

**Metode 2: Python**
Buka terminal di folder `docAMS` dan jalankan:
`python -m http.server 3000`
Lalu buka `http://localhost:3000` di browser Anda.

**Metode 3: Laragon (Sesuai Setup Anda)**
Akses langsung melalui: [http://docAMS.test](http://docAMS.test) atau [http://localhost/docAMS](http://localhost/docAMS)
