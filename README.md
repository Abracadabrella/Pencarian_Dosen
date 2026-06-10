# 🎓 dosen_lookup

CLI tool untuk mencari data **dosen** perguruan tinggi Indonesia langsung dari terminal Linux — mencakup profil, riwayat pendidikan, riwayat mengajar, dan portofolio akademik.

> **Catatan:** Didistribusikan sebagai binary Linux yang sudah dikompilasi. Tidak membutuhkan Python atau dependensi tambahan di sistem target.

---

## ⚠️ Peringatan & Ketentuan Penggunaan

> **BACA SEBELUM MENGGUNAKAN**

Alat ini mengakses data akademik dosen dari basis data resmi pemerintah Indonesia. Dengan menggunakan alat ini, Anda menyatakan memahami dan menyetujui ketentuan berikut:

1. **Hanya untuk keperluan sah**, seperti:
   - Verifikasi data akademik untuk keperluan pribadi atau institusi
   - Riset dan pengembangan sistem informasi akademik
   - Keperluan administrasi kampus yang sah

2. **Dilarang keras** menggunakan alat ini untuk:
   - Pengumpulan massal data dosen tanpa izin (*scraping* tidak bertanggung jawab)
   - Penyebaran, penjualan, atau komersialisasi data yang diperoleh
   - Tujuan diskriminasi, pelecehan, atau intimidasi terhadap individu
   - Pembuatan basis data tandingan yang melanggar hak cipta
   - Otomasi pencarian dalam jumlah besar yang membebani server (flooding/DDoS)

3. **Data yang ditampilkan adalah milik negara.** Penggunaan data tunduk pada peraturan perundang-undangan yang berlaku, termasuk UU No. 27 Tahun 2022 tentang Perlindungan Data Pribadi (UU PDP).

4. **Penulis tidak bertanggung jawab** atas segala bentuk penyalahgunaan. Konsekuensi hukum dari penggunaan yang tidak sah sepenuhnya menjadi tanggung jawab pengguna.

5. **Gunakan dengan bijak.** Jeda antar request sudah diatur secara default — jangan mengubahnya menjadi terlalu cepat.

---

## 📦 Instalasi

```bash
# Download binary dari halaman Releases
wget https://github.com/<username>/dosen_lookup/releases/latest/download/dosen_lookup

# Beri izin eksekusi
chmod +x dosen_lookup

# Jalankan
./dosen_lookup --name "Nama Dosen"
```

> Tidak perlu instalasi apapun. Binary langsung bisa dijalankan di Linux x86-64.

---

## 🚀 Cara Penggunaan

### Sintaks dasar

```bash
./dosen_lookup --name "NAMA DOSEN"
```

### Contoh penggunaan

```bash
# Cari dosen, tampilkan list (maks 20 hasil)
./dosen_lookup --name "Samsul Bahri"

# Tampilkan hingga 50 hasil
./dosen_lookup --name "Samsul Bahri" --limit 50

# Langsung pilih dosen nomor 2 tanpa prompt interaktif
./dosen_lookup --name "Samsul Bahri" --select 2

# Hanya tampilkan list dosen, tidak perlu pilih detail
./dosen_lookup --name "Samsul Bahri" --no-detail

# Tampilkan detail dengan maks 30 item per section
./dosen_lookup --name "Samsul Bahri" --limit 25 --detail-limit 30

# Simpan hasil pencarian dan detail ke file JSON
./dosen_lookup --name "Samsul Bahri" \
    --json-out dosen.json \
    --detail-json-out detail_dosen.json

```

---

## 🖥️ Alur Interaktif

```
1. Jalankan perintah dengan --name
2. Tool menampilkan daftar dosen yang cocok dengan nama
3. Masukkan nomor urut dosen yang ingin dilihat detailnya
4. Tool mengambil dan menampilkan:
   ├─ Profil dosen
   ├─ Riwayat pendidikan
   ├─ Riwayat mengajar
   ├─ Portofolio pengabdian
   ├─ Portofolio penelitian
   ├─ Portofolio paten
   └─ Portofolio karya
```

---

## ⚙️ Referensi Argumen

| Argumen | Default | Deskripsi |
|---|---|---|
| `--name` | *(wajib)* | Nama dosen yang dicari |
| `--limit` | `20` | Maksimal data dosen yang ditampilkan |
| `--detail-limit` | `10` | Maksimal item per section pada detail |
| `--select` | *(interaktif)* | Langsung pilih nomor dosen, skip prompt |
| `--no-detail` | `false` | Hanya tampilkan list, tidak ambil detail |
| `--json-out` | — | Simpan list dosen ke file JSON |
| `--detail-json-out` | — | Simpan detail dosen ke file JSON |

---

## 📋 Contoh Output

```
╔══════════════════════════════════════╗
║     Pencarian Dosen — Terminal CLI   ║
╚══════════════════════════════════════╝

▌ DOSEN (3 data)
──────────────────────────────────────────────────────────────────────────────
  1. Nama: SAMSUL BAHRI  NIDN: 0012345678  Perguruan Tinggi: Universitas ...
  2. Nama: SAMSUL BAHRI  NIDN: 0087654321  Perguruan Tinggi: Institut ...
  3. Nama: SAMSUL BAHRI  NIDN: 0011223344  Perguruan Tinggi: Politeknik ...

Pilih nomor dosen 1-3 (Enter/q untuk batal): 1

  [info] Mengambil detail dosen terpilih ...

▌ PROFILE DOSEN
──────────────────────────────────────────────────────────────────────────────
  Nama: SAMSUL BAHRI  Nidn: 0012345678  Jenis Kelamin: L
  Jabatan Fungsional: Lektor Kepala  Pendidikan Tertinggi: S3
  ...
```

---

## 🔧 Troubleshooting

**Binary tidak bisa dijalankan:**
```bash
chmod +x ./dosen_lookup
```


**Hasil kosong / tidak ditemukan:**
- Gunakan nama tanpa gelar (contoh: `"Samsul Bahri"` bukan `"Dr. Samsul Bahri, M.T."`)
- Coba nama yang lebih pendek atau lebih spesifik

