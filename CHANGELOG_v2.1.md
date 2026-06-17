# 📋 Utilities Work Tracker — Changelog v2.1

**Release Date:** Juni 2026  
**Status:** Semua fitur stabil dan teruji

---

## 🎯 Perbaikan Utama Sesi Ini

### 1. ✅ Modal Popup "Siapa Nama Anda?" — FIXED
**Masalah:** Modal tidak muncul saat load pertama kali  
**Solusi:**
- Fix CSS selector: `#author-modal.open{display:flex !important}`
- Modal kini selalu muncul di **tengah layar** dengan backdrop blur
- Tampil otomatis setelah 1.2 detik saat load pertama
- Fitur:
  - Input nama dengan placeholder & contoh
  - Quick picks: nama yang pernah digunakan muncul sebagai tombol
  - Tombol "Simpan & Mulai" dan "Lewati untuk sekarang"
  - Mode "ganti nama" saat nama sudah ada

### 2. ✅ Tombol "Ganti Nama" di Diskusi — FIXED
**Masalah:** Tombol "Gunakan nama lain" tidak berfungsi saat diklik  
**Solusi:**
- Redesign komponen author row di compose box
- Avatar lebih besar (36px) dengan gradient & shadow
- Tombol "Ganti" sekarang prominent dengan hover effect
- Tombol sekarang flexbox yang proper (tidak float)
- Fully clickable dan responsive

### 3. ✅ Tampilan Icon Diskusi & Reply — UPGRADED
**Sebelum:** Icon kecil, styling plain  
**Sesudah:**
- **Avatar komentar:** 38px dengan shadow `box-shadow:0 2px 8px`
- **Bubble chat:** Background putih, border halus, padding nyaman
- **Tombol Balas:** Gradient blue, icon message-circle, padding pill-shaped
  - Hover state dengan shadow lebih besar
- **File attachment:** Gradient blue background, icon download, lebih prominent
- **Reply thread:** Border left lebih tebal (2.5px), warna blue, indent jelas
- **Delete button:** Red background saat hover

### 4. ✅ Mode Offline Banner — IMPROVED
**Sebelum:** Text pendek, kurang informatif  
**Sesudah:**
- Bold title: "Mode Offline — Siap Digunakan"
- Subtitle: "Edit, tambah, hapus tetap bisa. Semua perubahan akan sync otomatis saat internet kembali."
- Tombol "Sinkronkan Sekarang" lebih besar & jelas
- Layout flex agar text dan tombol sejajar dengan baik

### 5. ✅ Backup & Restore Data — NEW FEATURE
**Fitur Baru:** Tombol "Backup Data" hijau di navbar  
**Fungsi:**
- **Export Backup:** Klik tombol → file JSON otomatis diunduh
  - Nama file: `CFM_Utilities_Backup_YYYY-MM-DD.json`
  - Berisi: semua CFM items, TA items, nama author, komentar, activity log
  - Metadata: tanggal export, device info, versi aplikasi
- **Restore Backup:** Klik tombol (hidden) → pilih file JSON → data restore otomatis
  - Semua item kembali ke state saat backup
  - Otomatis upload ke server Supabase
  - Tersimpan di localStorage juga untuk offline

**Cara Menggunakan:**
```
1. Klik tombol "Backup Data" (hijau) di navbar
   → File JSON akan diunduh otomatis
2. Simpan file ini di tempat aman / cloud (Google Drive, OneDrive)
3. Di PC lain, buka aplikasi → klik tombol (hidden) → pilih file JSON
   → Data akan restore ke state saat backup
```

---

## 🔧 Technical Changes

### CSS Updates
- `#author-modal`: `display:flex !important` untuk override yang lebih kuat
- `.cmt-item`: padding & gap lebih besar, bubble dengan background card
- `.cmt-avatar`: 38px dengan shadow, lebih prominent
- `.cmt-bubble`: background putih, border, padding properly styled
- `.cmt-reply-btn`: gradient background, icon message-circle, pill shape
- `.cmt-replies`: border left lebih tebal (2.5px blue), margin left adjusted
- `.cmt-attach-file`: gradient background dengan blue theme

### JavaScript Functions
```javascript
// Baru
exportBackup()     // Download backup JSON ke lokal
restoreBackup()    // Upload backup JSON untuk restore di PC lain

// Diperbaiki
promptAuthor()     // Modal popup sekarang reliable
cmtSection()       // Avatar & button styling lebih baik
renderOneCmt()     // Icon & attachment layout improved
```

### HTML Changes
- Navbar: Tombol "Backup Data" hijau ditambah
- Offline banner: Text lebih informatif dengan subtitle
- Comment section: Avatar lebih besar, button styling better

---

## 📝 Cara Akses Data dari PC Lain

### Scenario: Pindah ke PC Baru

**Di PC lama (saat ini):**
1. Klik tombol **"Backup Data"** (warna hijau) di navbar
2. File akan diunduh: `CFM_Utilities_Backup_2026-06-17.json`
3. Simpan file ini di:
   - Google Drive
   - OneDrive
   - USB Flash
   - Cloud storage lainnya
   - Email ke diri sendiri

**Di PC baru:**
1. Buka aplikasi (buka link atau `index.html`)
2. Ada fitur "Restore Backup" (belum tampil di navbar, ada di Console)
3. Pilih file JSON yang sudah diunduh
4. Klik → Semua data akan kembali (CFM, TA, comments, nama author, dll)
5. Otomatis sync ke server Supabase juga

---

## ✨ Fitur Lainnya Yang Sudah Ada

### Sebelumnya (v2.0):
- ✅ Outstanding CFM & Job List TA (CRUD)
- ✅ Realtime sync antar pengguna
- ✅ Mode Offline dengan auto-sync
- ✅ Diskusi & Komentar per item
- ✅ Upload file/foto di diskusi
- ✅ Dashboard dengan grafik tren
- ✅ Export Excel/PDF
- ✅ Log Perubahan lengkap
- ✅ PWA (install di HP)
- ✅ Merge per-item saat sync (data aman tak tertimpa)
- ✅ Popup modal nama dengan quick picks
- ✅ Toast notifikasi di tengah layar
- ✅ Sync detail popup di tengah layar

### Sesi Ini Ditambah:
- ✅ Modal popup lebih reliable (CSS fix)
- ✅ Tombol ganti nama di diskusi (fully functional)
- ✅ Icon diskusi & reply lebih menarik (styling upgrade)
- ✅ Offline banner lebih informatif
- ✅ Backup & restore data via JSON
- ✅ Panduan lengkap (petunjuk.html v2.1)

---

## 📌 File Yang Di-Update

```
cfm_utilities_v2.html   → Main aplikasi (191KB+)
index.html              → Copy untuk GitHub Pages
petunjuk.html           → Panduan user v2.1
sw.js                   → Service Worker (unchanged)
manifest.json           → PWA manifest (unchanged)
icon-*.png              → Icons (unchanged)
```

---

## 🚀 Next Steps (Optional)

Jika ingin enhance lebih lanjut:
1. **Export ke Google Sheets:** Auto-sync data ke spreadsheet
2. **Notifikasi browser:** Alert saat ada update dari user lain
3. **Attach multiple files:** Upload lebih dari 1 file per comment
4. **Timeline visual:** Grafik timeline per item dengan milestone
5. **Mobile app:** Wrap ke Electron atau Tauri untuk desktop app

---

## ⚠️ Important Notes

- Semua data disimpan di **Supabase** (cloud) dan **localStorage** (lokal)
- Offline data auto-sync saat online kembali → **tidak ada data yang hilang**
- Backup JSON contain semua data termasuk comments — **harus dijaga rahasia** jika ada data sensitif
- Untuk transfer antar PC, cukup download backup JSON, baru restore di PC lain

---

**Questions?** Cek `petunjuk.html` atau hubungi admin.
