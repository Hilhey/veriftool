# 📚 Panduan Penggunaan SheerID Verification Tool

## 🎯 Daftar Isi
- [Persyaratan Sistem](#-persyaratan-sistem)
- [Instalasi](#-instalasi)
- [Menjalankan Aplikasi](#-menjalankan-aplikasi)
- [Cara Menggunakan](#-cara-menggunakan)
- [Service yang Didukung](#-service-yang-didukung)
- [Troubleshooting](#-troubleshooting)

---

## 💻 Persyaratan Sistem

| Komponen | Requirement |
|----------|-------------|
| Node.js | v16 atau lebih tinggi |
| NPM | v8 atau lebih tinggi |
| Browser | Chrome, Firefox, Edge (modern) |
| OS | Windows, macOS, Linux |

---

## 📦 Instalasi

### 1. Install Dependencies Backend

```bash
cd auto-verify-tool
npm install
```

### 2. Struktur Folder

```
SheerID-Verification-Tool/
├── index.html              # Frontend UI
├── auto-verify-tool/       # Backend Server
│   ├── server.js           # Express API Server
│   ├── verifier.js         # Verification Logic
│   ├── generator.js        # Document Generator
│   └── package.json        # Dependencies
└── README2.md              # Panduan ini
```

---

## 🚀 Menjalankan Aplikasi

### Step 1: Jalankan Backend Server

Buka terminal/command prompt dan jalankan:

```bash
cd auto-verify-tool
node server.js
```

Output yang diharapkan:
```
Server running at http://localhost:3000
```

> ⚠️ **Penting**: Backend HARUS tetap berjalan selama menggunakan tool ini!

### Step 2: Buka Frontend

Buka file `index.html` di browser dengan cara:
- Double-click file `index.html`, atau
- Klik kanan → Open with → Browser pilihan Anda

---

## 📖 Cara Menggunakan

### 1️⃣ Pilih Jenis Service

Pada dropdown menu, pilih salah satu service:
- **Spotify Premium (Student)** - Untuk diskon pelajar Spotify
- **YouTube Premium (Student)** - Untuk diskon pelajar YouTube
- **Google Gemini (Student)** - Untuk akses pelajar Gemini
- **Bolt.new (Teacher)** - Untuk verifikasi guru
- **ChatGPT (Teacher)** - Untuk verifikasi guru ChatGPT

### 2️⃣ Dapatkan Link Verifikasi SheerID

1. Buka halaman registrasi service yang dipilih (Spotify/YouTube/Gemini/dll)
2. Mulai proses verifikasi pelajar/guru
3. Anda akan diarahkan ke halaman SheerID
4. Copy URL dari address bar browser
   - URL harus dimulai dengan: `https://services.sheerid.com/verify/...`
   - URL harus mengandung: `?verificationId=...`

**Contoh URL yang valid:**
```
https://services.sheerid.com/verify/67c8c14f5f17a83b745e3f82/?verificationId=696e318eb3c9111ee5544b4e
```

### 3️⃣ Paste URL dan Klik Verify

1. Paste URL verifikasi ke input field
2. Klik tombol **"VERIFY NOW"**
3. Tunggu proses verifikasi (1-2 menit)
4. Lihat hasil di Progress Log

### 4️⃣ Hasil Verifikasi

| Status | Keterangan |
|--------|------------|
| ✅ Success | Verifikasi berhasil! Cek email untuk kode reward |
| ❌ Link Expired | Link sudah tidak valid, dapatkan link baru |
| ❌ Network Error | Backend server tidak berjalan |

---

## 🎓 Service yang Didukung

### Student Verification
| Service | Dropdown Option |
|---------|-----------------|
| Spotify Premium Student | `Spotify Premium (Student)` |
| YouTube Premium Student | `YouTube Premium (Student)` |
| Google Gemini | `Google Gemini (Student)` |

### Teacher Verification
| Service | Dropdown Option |
|---------|-----------------|
| Bolt.new | `Bolt.new (Teacher)` |
| ChatGPT Plus | `ChatGPT (Teacher)` |

---

## 🔧 Troubleshooting

### ❌ "Network Error. Is the backend running on port 3000?"

**Penyebab:** Backend server tidak berjalan.

**Solusi:**
```bash
cd auto-verify-tool
node server.js
```

### ❌ "Invalid or expired verification link"

**Penyebab:** Link verifikasi sudah expired atau tidak valid.

**Solusi:**
1. Kembali ke halaman registrasi service
2. Mulai proses verifikasi dari awal
3. Dapatkan link baru
4. Coba lagi dengan link yang baru

### ❌ "npm: cannot be loaded because running scripts is disabled"

**Penyebab:** PowerShell execution policy di Windows.

**Solusi:**
```bash
# Gunakan cmd sebagai pengganti PowerShell
cmd /c "npm install"
cmd /c "node server.js"
```

### ❌ Port 3000 sudah digunakan

**Solusi:**
1. Hentikan aplikasi lain yang menggunakan port 3000
2. Atau ubah port di `auto-verify-tool/server.js`:
   ```javascript
   const PORT = process.env.PORT || 3001; // Ganti ke port lain
   ```
3. Update juga `BACKEND_URL` di `index.html`:
   ```javascript
   const BACKEND_URL = 'http://localhost:3001';
   ```

---

## 📌 Tips Penting

1. **Selalu gunakan link verifikasi yang fresh** - Link expired setelah beberapa waktu
2. **Jangan refresh halaman** saat proses verifikasi berjalan
3. **Pastikan backend server tetap running** selama menggunakan tool
4. **Cek email** setelah verifikasi berhasil untuk mendapatkan kode

---

## 🔗 Metode Alternatif

Jika Auto Verifier tidak bekerja, gunakan metode alternatif yang tersedia di halaman:
- **SheerID VIP Bot** - Bot Telegram
- **SheerID VN Bot** - Bot Telegram Vietnam
- **Batch 1Key.me** - Web tool untuk batch verification
- **Student Card Generator** - Generate kartu pelajar
- **Payslip Generator** - Generate slip gaji

---

## 📞 Bantuan

Jika mengalami masalah:
1. Cek GitHub Issues di repository
2. Baca `TESTING_GUIDE.md` untuk panduan testing
3. Baca `README.md` untuk informasi teknis

---

**Terakhir diperbarui:** Januari 2026
