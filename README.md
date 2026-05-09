# 🍽️ Menu Online — Google Apps Script

Menu digital gratis untuk warung, cafe, atau UMKM apapun. Cukup salin template, isi data, klik deploy — tanpa perlu coding sama sekali. Data menu dikelola langsung dari **Google Sheets**.

**Demo:** [menu-online](https://sites.google.com/view/web-menu-online)

---

## ✨ Fitur

- Halaman menu berbasis Google Sheets, tanpa coding ulang untuk update menu
- Kategori menu otomatis dari nama sheet
- Tema warna bisa diganti lewat Sheets (`warm`, `matcha`, `rose`)
- Tombol WhatsApp floating untuk pemesanan langsung
- Foto menu dari URL eksternal (Google Drive, Imgur, dll.)
- Mobile-friendly & dapat di-embed di iframe

---

## 📋 Prasyarat

- Akun Google

---

## 🚀 Cara Deploy

### Langkah 1 — Salin Template Google Sheets

Sudah tersedia template Spreadsheet yang siap pakai, lengkap dengan contoh data dan kode Apps Script yang sudah terpasang.

1. Buka link template berikut: **[🔗 Buka Template Google Sheets](https://docs.google.com/spreadsheets/d/11izq9wDQaMWNg3fD7iAxkFhzo7_60TjjrGCcG8-rDXQ)**
2. Klik menu **File** di pojok kiri atas → klik **Make a copy**
3. Akan muncul pop-up untuk memberi nama file baru — sesuaikan dengan nama tokomu
4. Di pop-up yang sama akan ada keterangan bahwa file sudah memiliki **Attached Apps Script file** — bagian ini **tidak perlu diubah**, biarkan saja
5. Pilih lokasi penyimpanan di Google Drive sesuai keinginanmu, lalu klik **Make a copy**

Spreadsheet hasil salinan sudah langsung siap digunakan — tidak perlu menyalin kode apapun secara manual.

---

### Langkah 2 — Isi Data Toko di Spreadsheet

Buka Spreadsheet hasil salinan tadi, lalu edit data sesuai informasi tokomu.

#### Sheet `info_toko`

Sheet ini berisi profil toko. Edit nilai di **Kolom B** sesuai data tokomu:

| Kolom A (key) | Kolom B (value) |
|---|---|
| nama_toko | Warung Bu Sari |
| deskripsi_toko | Masakan rumahan enak dan murah |
| jam_buka | Senin–Sabtu, 08.00–21.00 |
| lokasi | Jl. Melati No. 12, Bandar Lampung |
| link_gmaps | https://maps.app.goo.gl/xxx |
| nomor_hp | 08123456789 |
| logo | *(URL gambar logo, opsional)* |
| tema | warm |

> **Pilihan tema:** `warm` (default), `matcha`, `rose`

#### Sheet Kategori Menu

Template sudah menyertakan contoh sheet kategori menu. Edit isinya sesuai menu tokomu, atau tambah sheet baru untuk kategori tambahan. Nama sheet otomatis jadi nama tab di halaman web.

Format data menu (mulai baris ke-3):

| nama_menu | deskripsi | harga | gambar | status |
|---|---|---|---|---|
| Nasi Goreng | Nasi goreng spesial | 15000 | https://... | aktif |
| Es Teh Manis | Teh manis dingin | 5000 | https://... | aktif |
| Ayam Bakar | *(menu tidak aktif)* | 20000 | | tidak aktif |

> - Kolom `status` wajib diisi `aktif` agar menu tampil. Isi lainnya akan disembunyikan.
> - Kolom `gambar` berisi URL langsung ke foto (bukan link share Google Drive biasa — gunakan *direct image URL*).
> - Kolom `harga` diisi angka saja (tanpa Rp, tanpa titik).

---

### Langkah 3 — Buka Google Apps Script

1. Di Spreadsheet, klik menu **Ekstensi → Apps Script**
2. Tab editor Apps Script akan terbuka — kode sudah ada di sana, tidak perlu diubah

---

### Langkah 4 — Deploy sebagai Web App

1. Klik tombol **Deploy** berwarna biru di pojok kanan atas → pilih **New deployment**
2. Klik ikon ⚙️ di samping tulisan **Select type** — pastikan **Web app** sudah tercentang. Jika belum, klik untuk mencentangnya
3. Isi konfigurasi:
   - **Description:** (opsional, contoh: `v1`)
   - **Execute as:** `Me`
   - **Who has access:** `Anyone` *(agar bisa diakses publik tanpa login)*
4. Klik **Deploy**
5. Klik **Authorize access** — browser akan membuka tab baru untuk memilih akun Google yang akan digunakan *(terkadang Google akan meminta verifikasi akun terlebih dahulu)*
6. Akan muncul peringatan dari Google:
   > *"Google hasn't verified this app. The app is requesting access to sensitive info in your Google Account. Until the developer verifies this app with Google, you shouldn't use it."*

   Ini normal karena kamu adalah developer-nya sendiri. Klik **Advanced** di pojok kiri bawah, lalu klik **Go to [nama project] (unsafe)**
7. Dialog akan berubah dan menampilkan bahwa script ini akan meminta akses ke Google Sheets. Scroll ke bawah lalu klik **Continue**
8. Browser akan kembali ke tab editor Apps Script dan menunggu proses deployment selesai. Setelah loading selesai, dialog akan menampilkan konfirmasi bahwa deployment berhasil
9. Salin **Web app URL** yang muncul di bawah tulisan *Web app* — klik URL-nya atau gunakan tombol **Copy** di bawahnya. Link ini adalah link menu toko kamu.

> **Catatan:** Setiap kali kamu mengubah kode (`Code.gs` atau `index.html`), kamu perlu deploy ulang agar perubahan aktif. Caranya: klik **Deploy** → **Manage deployments** → klik ikon edit (pensil) → klik kolom **Version** dan pilih **New version** → klik **Deploy**.
>
> Perubahan data di Sheets langsung aktif tanpa deploy ulang (setelah cache habis, maksimal 30 detik).

---

### Langkah 5 — Tampilkan di Google Sites (Opsional)

Google Sites memungkinkan kamu membuat halaman web sederhana secara gratis. Selain itu, URL dari Google Sites jauh lebih pendek dan mudah dibaca dibanding URL hasil deploy Apps Script yang panjang — sehingga lebih nyaman untuk dibagikan ke pelanggan.

1. Buka [sites.google.com](https://sites.google.com) dan masuk dengan akun Google kamu
2. Di bagian **Start a new site**, pilih **Blank site** — kamu akan langsung masuk ke halaman editor
3. Di panel kanan, buka tab **Pages**, arahkan kursor ke ikon **+** lalu pilih **Full page embed**
4. Beri nama halaman baru — nama ini akan muncul sebagai nama tab browser menu digitalmu
5. Klik tombol **Add Embed** pada halaman yang baru saja dibuat, lalu tempel **Web app URL** dari Langkah 4. Tunggu hingga loading selesai, lalu klik **Insert**
6. Kembali ke tab **Pages**, klik ikon tiga titik pada halaman yang baru saja dibuat lalu pilih **Make homepage**
7. Hapus halaman **Home** bawaan dengan klik tiga titik di sampingnya lalu pilih **Delete**
8. Klik ikon **gear** di pojok kanan atas — akan muncul dialog pop-up. Klik menu **Brand image**, lalu di bagian **Favicon** upload atau pilih gambar yang ingin digunakan sebagai logo pada tab browser, lalu tutup dialog
9. Klik tombol **Publish** di pojok kanan atas
10. Tentukan nama URL untuk sitesmu (contoh: `sites.google.com/view/nama-toko`), lalu klik **Publish** untuk mengonfirmasi

Setelah dipublikasikan, URL Google Sites tersebut sudah bisa dibagikan ke pelanggan.

---

## 🔧 Kustomisasi

### Ganti Tema Warna

Di sheet `info_toko`, ubah nilai baris `tema` menjadi salah satu dari:

| Nama | Tampilan |
|---|---|
| `warm` | Cokelat/oranye hangat (default) |
| `matcha` | Hijau matcha |
| `rose` | Merah muda/mawar |

### Tambah Kategori Menu

Cukup tambah sheet baru di Spreadsheet — nama sheet langsung jadi nama tab kategori. Tidak perlu ubah kode apapun.

### Nonaktifkan Menu Sementara

Ubah kolom `status` item menu dari `aktif` menjadi apapun (misalnya `tidak aktif` atau dikosongkan). Menu akan langsung hilang dari halaman (setelah cache habis).

### Cache Data

Defaultnya data di-cache selama **30 detik** untuk menghemat kuota baca Sheets. Bisa diubah di `Code.gs`:

```javascript
var CACHE_SECONDS = 30; // ubah sesuai kebutuhan
```

---

## ❓ FAQ

**Q: Foto menu atau logo tidak muncul?**
Pastikan URL yang dipakai adalah *direct link* — link yang langsung mengarah ke file gambarnya, bukan ke halaman preview atau halaman berbagi. Kalau foto disimpan di layanan lain (Imgur, hosting foto, dll.), pastikan URL-nya berakhiran `.jpg`, `.png`, atau format gambar lainnya.

Jika menggunakan **Google Drive**, link biasa dari tombol Share tidak bisa langsung dipakai. Gunakan sheet **Converter Link Google Drive ke Thumbnail** yang sudah ada di template:
1. Klik kanan file di Google Drive → **Share** → **Copy link** (pastikan akses sudah diubah ke "Anyone with the link")
2. Tempel link tersebut ke kolom **Sumber** di sheet Converter
3. Salin link yang muncul di kolom **Hasil** — link ini sudah siap dipakai
4. Tempel link Hasil ke kolom `gambar` (untuk foto menu) atau `logo` (untuk foto profil toko)

**Q: Perubahan di Sheets tidak langsung terlihat?**
Normal — data di-cache hingga 30 detik. Tunggu sebentar atau ubah `CACHE_SECONDS` ke nilai lebih kecil di `Code.gs`.

**Q: Apakah bisa dipakai untuk lebih dari satu toko?**
Bisa. Cukup buat Spreadsheet baru dan ulangi proses deploy dari awal untuk setiap toko.

---
