# Nota KQ5 — Pembuat Nota Pesanan Ayam Bakar KQ5

Aplikasi PWA terpisah (sebelumnya Nota 234) untuk membuat nota pesanan dengan cepat dan menyimpannya sebagai PDF. HTML/CSS/JavaScript tanpa build step dan tanpa library luar. Data tersimpan di IndexedDB (`nota234`) pada HP, tidak bercampur dengan aplikasi Penyetan 234.

## Fitur
- **Rekening pembayaran:** isi di Pengaturan (bank/e-wallet, nomor, atas nama; boleh lebih dari satu). Selalu tampil di PDF, gambar nota, dan pesan WhatsApp ke pelanggan selama sudah diisi.
- **Tampilan simpel:** form hanya menampilkan nama, nomor WhatsApp, menu, dan total. Tanggal, jam, alamat, diskon, pajak, DP, status lunas, dan catatan ada di *Opsi lainnya* (terbuka otomatis saat edit bila sudah terisi). Tombol utama *Buat & Kirim ke Pelanggan*, tombol kedua *Simpan Saja*.
- Buat nota: pelanggan, telepon, tanggal, jam di lokasi, alamat, daftar menu, diskon (Rp/%), pajak (%), DP, status lunas, catatan. Total dihitung otomatis.
- Nomor nota berurutan `N-0001`, nama berkas PDF `NOTA-TanggalNota-NomorUrut.pdf` (mis. `NOTA-20261022-0003.pdf`).
- PDF nota dibuat langsung di HP (tanpa internet), memakai logo Ayam Bakar KQ5.
- **Kirim gambar nota:** *Buat & Kirim ke Pelanggan* dan *Kirim Gambar ke Pelanggan* selalu mengirim **gambar PNG** (bukan teks) lewat menu bagikan Android; nomor pelanggan disalin otomatis untuk dicari di WhatsApp dan kontak dipilih sendiri. Jika HP tidak mendukung berbagi file, gambar disimpan dan chat nomor pelanggan dibuka untuk melampirkannya. Cara lain ada di *Cara kirim lainnya* (buka chat nomor pelanggan, teks WhatsApp, teks ke grup, salin).
- Kirim WhatsApp ke pelanggan, kirim teks ringkas ke grup WhatsApp (pilih grup di WhatsApp), salin teks.
- Riwayat: cari, lihat, edit (nomor tetap), duplikat, tandai lunas, hapus, ekspor CSV.
- Menu cepat (nama + harga) agar harga terisi otomatis; autofill telepon dan alamat untuk pelanggan lama.
- Cadangan JSON (unduh/pulihkan), offline, bisa dipasang di layar utama.

## Catatan
- Nota ini bukan pembukuan: tidak ada laporan omzet atau laba.
- Data hanya di satu HP; hapus data browser = data hilang. Unduh cadangan rutin (Pengaturan).
- WhatsApp tidak mengizinkan aplikasi web mengirim gambar otomatis ke nomor tertentu; pengguna tetap menekan kirim sendiri.
- Aplikasi tidak bisa memilih grup WhatsApp otomatis dan tidak tahu apakah pesan terkirim.

## Menjalankan & deploy
```
python3 -m http.server 8080      # lalu buka http://localhost:8080
node --test tests/nota.test.mjs
```
GitHub Pages: unggah isi folder ke repositori **baru** (atau subfolder), aktifkan Pages. Semua path relatif. Naikkan `VERSION` di `service-worker.js` setiap ada perubahan.
