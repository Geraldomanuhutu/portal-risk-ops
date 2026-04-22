# Portal Risiko Operasional

Self-service portal untuk seluruh divisi internal.

## 📁 Struktur Repo

```
├── .github/workflows/
│   └── update-data.yml         ← GitHub Actions (jangan diubah)
├── public/
│   ├── index.html              ← Portal web
│   ├── data.js                 ← AUTO-GENERATED, jangan edit manual
│   └── files/                  ← Taruh PDF/XLSX/dll di sini
├── Datamart_Risiko_Operasional.xlsx   ← ← ← Ini Master excel nya ya
├── update_data.py              ← Dijalankan otomatis oleh GitHub Actions
├── requirements.txt
└── vercel.json
```

---

Internal — Manajemen Risiko Operasional
