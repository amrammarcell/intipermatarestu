# Intipermata Restu — Website Project

Landing page untuk **PT Intipermata Restu**, produsen lateks pekat (natural latex) sejak 1990. Dibangun sebagai satu file HTML (self-contained), dipublish sebagai Claude Artifact.

- **Artifact (live):** https://claude.ai/code/artifact/d5b8085e-0a49-4799-ae6f-1841b89dd9ee
- **Sumber data harga:** Google Sheet "LATEX PRICE INDEX" — https://docs.google.com/spreadsheets/d/10L3clCnaRo9v8O-Ygjko1tbMIizgu7DxwjMMdCK1OgA/edit

## Profil Perusahaan

- PT Intipermata Restu, berdiri 1990. Lini bisnis: manufaktur lateks pekat, distribusi bahan kimia (Aquadest, PAC, Caustic Soda, Silica Gel, dll), dan Palm Acid Oil (PAO, sejak 2018, ekspor ke Pakistan/Korea/India).
- Sertifikasi: ISO 9001:2015 (Manufacture of Natural Latex), No. 10000435242-MSC-JAS-ANZ-IDN.
- Alamat resmi: Jl. Raya Serang KM 10,5 RT 2/RW 4 No. 177, Desa Cisereh, Kel. Kadu Jaya, Kec. Curug, Kab. Tangerang - Banten 15720. Telp 021 5981 264 / 021 6917 535, email intipermatarestu@yahoo.com.
  *(Catatan: mockup website versi awal sempat pakai kontak lama — WA +62 819-0967-8978, email salesintipermata1@gmail.com. Perlu dikonfirmasi versi mana yang dipakai final.)*
- Klien Natural Latex (terkonfirmasi dari company profile resmi): PT Indokordsa, PT Dunlopillo, PT Asia Chemical, CV Aneka Warna Indah, PT Dharma Medipro, CV Kobe Global International.
- Klien Chemical: PT Indokordsa, CV Aneka Warna Indah.
- Klien PAO: Joon Chemical Co., SRK International, Active Enterprice, JB Energy, Highchem M&M, Xiamen Xingzhong Environmental Protection Chemical.

## Struktur Halaman (urutan section, per revisi terbaru)

1. Header (sticky, logo + nav + toggle bahasa ID/EN)
2. **Hero** — headline utama + kartu "Today's Reference" (dipindah jadi section pertama)
3. **Pusat Data Harga** — meta strip (Tanggal Acuan, USD/IDR, CNY/IDR, RM/IDR), judul statis "Latex Price Index", tabel 3 baris (SHFE/SGX/MRE), grafik tren harga
4. About / Tentang Kami
5. **Products** — 1 produk: "Lateks" (dulu "Lateks Pekat"; "Lateks Cair" sudah dihapus)
6. Why Choose Us
7. Clients (marquee logo/nama partner)
8. Testimonials
9. Gallery (6 foto asli pabrik)
10. Contact
11. Footer

## Status Revisi (sesi berjalan)

Semua item dari `Revisi Web.md` (7 poin) sudah diterapkan dan diverifikasi di 3 mode tampilan (PC/tablet/HP):

- [x] Hero dipindah jadi section pertama
- [x] Tile "VOL 24H" & "Index" diganti "CNY/IDR" & "RM/IDR"
- [x] Tab filter (Semua/Lateks/Karet Padat) dihapus → judul statis "Latex Price Index"
- [x] Header tabel: "Grade" → "Latex Type", "FOB" dihapus dari header kedua
- [x] Kolom "Perubahan" dihitung riil dari harga sebelumnya (bukan angka statis) — lihat catatan data di bawah
- [x] Tabel harga direstrukturisasi total: dari 8 grade karet generik menjadi 3 baris **SHFE / SGX / MRE** sesuai Google Sheet user; grafik tren disinkronkan dengan data yang sama
- [x] Kartu duplikat "Today's Reference" (LIVE badge + disclaimer) di dekat grafik — dihapus
- [x] Section Produk: "Lateks Cair" dihapus; "Lateks Pekat" → "Lateks" dengan spesifikasi baru (Total Solids 61%, Non-Rubber Solids 2.5% max, VFA 0.05 max, KOH 0.4–0.6, Mechanical Stability 900 detik; Dry Rubber Content & Ammonia tidak berubah)

- [x] Logo partner di section Clients — 2 logo resmi berhasil diambil & ditempel: **Dunlopillo** (dunlopillo.co.id) dan **Indokordsa** (indokordsa.com). Klien lain yang terkonfirmasi resmi (Asia Chemical, Dharma Medipro, Aneka Warna Indah) tidak punya sumber logo resmi yang jelas/legit saat dicari, jadi tetap tampil sebagai teks sesuai instruksi ("jika tidak ada tidak perlu").
- [x] Kartu "Today's Reference" di Hero disinkronkan agar mengambil data riil dari `priceData` (baris SHFE) alih-alih angka statis lama ("LATEX 60% DRC" / Rp 28.950) yang sudah tidak sesuai model data baru.
- [x] Teks hero diperbarui — hapus referensi "lateks cair" (produk sudah dihapus dari katalog).
- [x] Artifact sudah dipublish ulang dengan seluruh perubahan final (revisi 7 poin + data SHFE/SGX/MRE + logo klien + sinkronisasi hero).

**Belum selesai:** tidak ada — semua item revisi selesai.

## Status Revisi (sesi 2026-09-21)

- [x] Section Clients dipecah jadi 2 area: strip logo sliding tersendiri ("Klien dengan Logo Resmi" — Dunlopillo & Indokordsa) dan grid teks statis untuk klien tanpa logo ("Dipercaya juga oleh"). Kalau ke depan tidak ada klien berlogo sama sekali, strip logo otomatis disembunyikan (`renderClients()`).
- [x] Data harga, tanggal acuan, dan kurs (USD/CNY/RM per IDR) sekarang ditarik **live** dari Google Sheet lewat endpoint `gviz/tq` (JSONP script-tag, bukan `fetch`, supaya tidak kena CORS) — lihat detail di bawah. Tren grafik ditarik dari histori harian di **Sheet2**.
- [x] Semua CTA WhatsApp (tombol "Chat via WhatsApp" & ikon fab mengambang) diarahkan ke nomor `081805188897`.
- [x] Tabel kontak di bagian bawah: nomor `081805188897` jadi **Telepon/WhatsApp (Utama)**, nomor lama `0819-0967-8978` jadi **Sekunder**, ditambah kontak baru **Roni — 0853-7250-0491**.
- [x] Ditambahkan `<meta charset="UTF-8">` (glyph ▲/▼/– sempat rusak saat file di-serve tanpa header charset eksplisit) dan `<meta name="viewport">` (bug pra-eksisting: tanpa tag ini, HP sungguhan me-render layout desktop 980px lalu di-zoom-out, bukan layout mobile responsif — ditemukan saat pengujian mobile sesi ini).

## Catatan Data Harga (SHFE/SGX/MRE)

- Data harga tabel & grafik bersumber dari Google Sheet "LATEX PRICE INDEX", Sheet1 (gid=0; kolom TYPE/RAW PRICE/LATEX PRICE/UNIT/kg-price/idr-kg price/KURS-IDR/TANGGAL).
- **Live fetch (sesi ini):** halaman memuat `<script src="https://docs.google.com/.../gviz/tq?tqx=out:json;responseHandler:...&gid=...">` saat load — trik JSONP klasik yang tidak butuh header CORS dari Google, jadi jalan dari hosting statis biasa. Sheet1 (gid `0`) untuk harga/kurs/tanggal terbaru, Sheet2 (gid `540037232`) untuk histori tren grafik. Kalau fetch gagal (offline, atau di-host di tempat yang CSP-nya membatasi origin skrip eksternal — termasuk kemungkinan Claude Artifact, yang hanya izinkan origin CDN tertentu) halaman diam-diam fallback ke snapshot statis di `priceData`/`chartSeries` dalam HTML, sama seperti sebelumnya.
- Kolom "Perubahan" (%) dihitung nyata di JavaScript (`price - prev` dibagi `prev`). `prev` diambil dari entri Sheet2 SEBELUM entri terbaru untuk type yang sama; kalau baru ada 1 entri (hari pertama dicatat), `prev` = `price` hari ini → tampil +0.00%, sesuai desain awal.
- Riwayat harga harian direkam manual di **Sheet2** pada Google Sheet yang sama (kolom TANGGAL/TYPE/LATEX PRICE/IDR-KG PRICE/KURS-IDR) — ini yang jadi sumber `prev` dan sumber titik-titik tren grafik.
- Meta strip kurs: CNY/IDR diambil dari kurs baris SHFE, USD/IDR dari baris SGX, RM/IDR dari baris MRE (masing-masing row memang dihitung pakai mata uang aslinya di sheet).

## File Kerja

- Source HTML utama (di cloud workspace sesi ini): `intipermata-restu.html`
- Mulai sesi ini, folder kerja project disimpan juga ke folder lokal user: `C:\Users\MATEBOOK D15\OneDrive\Desktop\intipermatarestu\intipermatarestu\` (repo git ini).
