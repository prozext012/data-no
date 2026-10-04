# Buku Nomor HP — Arsip Akun (PWA)

App pencatat nomor HP, username, dan tanggal registrasi akun — tampilan ala buku register, bisa dicari, difilter, dan di-backup. Bisa di-install jadi aplikasi di HP.

Ini **static site murni** (HTML/CSS/JS biasa) — **gak butuh `npm install` atau proses build sama sekali**. Tinggal upload & deploy apa adanya.

## Deploy ke Vercel lewat GitHub

1. Push semua file di folder ini ke repo GitHub baru.
2. Buka [vercel.com](https://vercel.com) → **Add New Project** → import repo tadi.
3. Di pengaturan project:
   - Framework Preset: **Other**
   - Build Command: **kosongkan** (gak perlu build)
   - Output Directory: **kosongkan** / `.`
4. Deploy. Buka URL-nya di HP.

## Cara install di HP

- **Android (Chrome)**: buka situsnya, tunggu sebentar, tap menu titik tiga → **Install app** / **Add to Home screen**.
- **iOS (Safari)**: tap tombol **Share** → **Add to Home Screen** (iOS gak punya tombol install otomatis, ini batasan dari Apple).

## Struktur project

```
index.html       # seluruh app (HTML+CSS+JS jadi satu)
manifest.json     # metadata PWA
sw.js             # service worker (wajib untuk installability)
icons/            # logo app (tema buku ledger) di berbagai ukuran
vercel.json       # header cache untuk sw.js & manifest.json
```

## Fitur

- Tambah data: Nomor HP, Username, Tanggal (default hari ini)
- Tekan lama di satu baris data untuk Edit / Hapus
- Jam otomatis tercatat di bawah tanggal tiap data
- Pencarian username / nomor HP
- Filter Periode (Hari ini, Kemarin, 7 hari terakhir, Bulan ini) & Jam (Pagi/Siang/Malam) — bisa pilih lebih dari satu sekaligus
- Backup: unduh `.json` (buat restore), unduh `.csv` (buka di Excel), cetak/simpan PDF
- Pulihkan data dari file backup `.json`

## Catatan soal data

Data kesimpen otomatis di `localStorage` HP/browser yang kamu pakai — jadi nempel di situ doang, gak sinkron ke device lain kecuali kamu pakai fitur **Backup Data** (.json) di dalam app buat pindahin manual ke HP lain.
