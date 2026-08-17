# Generator Cover LHV — BBSPJPPI

Aplikasi client-side (tanpa server/backend) untuk membuat cover Laporan Hasil
Verifikasi (LHV) TKDN Produksi Sendiri, TKDN Kerja Sama Produksi, BMP, dan
TKDN Jasa — otomatis mengisi teks & foto ke atas 11 template desain resmi.

## Cara menjalankan

### Opsi 1 — Buka langsung
Klik dua kali `index.html`. Sebagian browser membatasi pemuatan gambar lokal
(`assets/*.png`) saat dibuka langsung dari file (`file://`). Jika template
tidak muncul, gunakan Opsi 2.

### Opsi 2 — Local server (disarankan)
```bash
cd lhv-cover-app
python3 -m http.server 8000
```
Lalu buka `http://localhost:8000` di browser.

### Opsi 3 — Deploy ke GitHub Pages
1. Push folder ini (`index.html` + `assets/`) ke sebuah repo GitHub.
2. Settings → Pages → aktifkan dari branch utama.
3. Aplikasi akan tersedia di `https://<username>.github.io/<repo>/`.

## Alur penggunaan
1. **Pilih Jenis Cover** — TKDN Produksi Sendiri, TKDN Kerja Sama Produksi,
   BMP, atau TKDN Jasa.
2. **Pilih Varian** — 5 pilihan warna/desain untuk TKDN & BMP, 1 desain untuk
   TKDN Jasa.
3. **Isi Data** — No. LHV, Nama Perusahaan (+ Nama Perusahaan Industri untuk
   Kerja Sama), Bidang Usaha, Nama Produk/Jasa, dan foto (opsional, otomatis
   dipotong mengikuti bentuk heksagon/lingkaran pada template).
4. **Unduh** — tombol Unduh PNG atau Unduh PDF, ukuran asli 1414×2000 px.

## Struktur file
```
lhv-cover-app/
├── index.html          ← aplikasi (React + Canvas, satu file)
└── assets/
    ├── tkdn-1.png ... tkdn-5.png     (5 varian TKDN Barang)
    ├── bmp-1.png  ... bmp-5.png      (5 varian BMP)
    └── jasa-1.png                    (1 varian TKDN Jasa)
```

## Catatan teknis / penyesuaian posisi
Semua koordinat teks & bentuk foto (heksagon/lingkaran) diukur langsung dari
pixel template asli dan divalidasi dengan render uji coba. Jika ada teks yang
perlu digeser sedikit (misal karena font berbeda saat dirender di browser),
edit objek `POS` di bagian atas script pada `index.html` — setiap field punya
`x`, `y`/`yTop`, `fontSize`, dan `width` yang bisa disesuaikan langsung.

Font judul/label mengikuti gaya template asli menggunakan **Poppins** (dimuat
dari Google Fonts). Pastikan koneksi internet aktif saat menjalankan aplikasi
agar font & pustaka (React, jsPDF) termuat dengan benar.

## Belum diuji di browser sungguhan
Aplikasi ini dibangun dan divalidasi secara matematis/pixel-level di
lingkungan tanpa browser. Mohon dicoba dan dikoreksi jika ada pergeseran
posisi teks/foto sebelum dipakai produksi — beri tahu saya bagian mana yang
perlu disesuaikan dan saya perbaiki koordinatnya.
