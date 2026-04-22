# Portal Risiko Operasional

Self-service portal untuk seluruh divisi internal.

---

## 🔒 Repo Private + Vercel = Aman

- Repo ini **private** — kode & data tidak bisa diakses orang lain
- Vercel tetap bisa deploy dari repo private (sudah dikonfigurasi)
- Yang bisa diakses publik hanya URL portal: `https://nama-project.vercel.app`

---

## 🚀 Setup Pertama Kali (hanya sekali)

### 1. Push repo ini ke GitHub (private)
```
Buat repo baru di github.com → Private → upload semua file ini
```

### 2. Connect ke Vercel
```
vercel.com → Add New Project → Import repo ini → Deploy
```
> Vercel otomatis baca `vercel.json` dan deploy folder `public/`

### 3. Aktifkan GitHub Actions
```
Di repo GitHub → tab Actions → klik "I understand my workflows, enable them"
```

Selesai. Sekarang setiap kali lo upload Excel baru, portal update otomatis.

---

## 📅 Cara Update Data (TANPA CODING)

### Langkah 1 — Update Excel
Buka `Datamart_Risiko_Operasional.xlsx` di komputer:
- Sheet **DATAMART** → isi kolom kuning (periode baru)
- Sheet **LAPORAN** → tambah/edit baris dokumen kalau ada yang baru
- Simpan file

### Langkah 2 — Upload ke GitHub (drag & drop)
1. Buka repo ini di **github.com**
2. Klik file `Datamart_Risiko_Operasional.xlsx`
3. Klik ikon **pensil (edit)** atau tombol **"..."** → **Replace file**
   > Atau: di halaman utama repo → drag & drop file Excel langsung ke browser
4. Scroll ke bawah → **Commit changes** → klik **Commit changes**

### Langkah 3 — Tunggu ~1 menit
GitHub Actions otomatis:
- Baca Excel
- Generate ulang `public/data.js`
- Push ke repo
- Vercel re-deploy portal

**Portal langsung update — tidak perlu buka terminal sama sekali.**

### Cek status update
Tab **Actions** di GitHub → lihat workflow "Update Portal Data" → harus ✅ hijau

---

## 📁 Cara Tambah File Dokumen Baru

1. **Upload file** ke folder `public/files/` di GitHub
   - Buka folder `public/files/` di repo → **Add file → Upload files**
2. **Tambah baris** di sheet `LAPORAN` di Excel:
   - Kolom Link: `files/nama_file.pdf`
   - Kolom Aktif: `Y`
3. Upload ulang Excel → otomatis update seperti biasa

---

## 📁 Struktur Repo

```
├── .github/workflows/
│   └── update-data.yml         ← GitHub Actions (jangan diubah)
├── public/
│   ├── index.html              ← Portal web
│   ├── data.js                 ← AUTO-GENERATED, jangan edit manual
│   └── files/                  ← Taruh PDF/XLSX/dll di sini
├── Datamart_Risiko_Operasional.xlsx   ← ← ← EDIT INI
├── update_data.py              ← Dijalankan otomatis oleh GitHub Actions
├── requirements.txt
└── vercel.json
```

---

Internal — Manajemen Risiko Operasional
