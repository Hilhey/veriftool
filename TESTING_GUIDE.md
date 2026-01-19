# Testing Guide - Gemini Student Verification

## Masalah yang Diperbaiki
✅ **Penyebab Error**: Backend URL di `index.html` menunjuk ke Azure deployment yang tidak aktif.
✅ **Solusi**: Diubah ke `http://localhost:3000` untuk pengembangan lokal.

## Setup dan Jalankan Server

### 1. Install Dependencies
```bash
cd auto-verify-tool
npm install
```

### 2. Jalankan Backend Server
```bash
npm start
```

Anda akan melihat output:
```
Server running at http://localhost:3000
```

### 3. Buka Frontend
Buka `index.html` di browser (atau gunakan Live Server):
- Cari di VS Code: Install ekstensi "Live Server"
- Right-click pada `index.html` → "Open with Live Server"
- Browser akan membuka di `http://localhost:5500` atau sesuai konfigurasi

## Testing Gemini Student Verification

### Verification URL yang Akan Ditest
```
https://services.sheerid.com/verify/67c8c14f5f17a83b745e3f82/?verificationId=696e318eb3c9111ee5544b4e
```

### Langkah Testing:
1. Pilih **Service Type**: `gemini` (dropdown)
2. Paste URL di input field
3. Klik **VERIFY NOW**
4. Amati logs di panel bawah

### Expected Output (Success)
```
📝 [HH:MM:SS] Starting verification process...
📝 [HH:MM:SS] Service type: gemini
📝 [HH:MM:SS] Connecting to backend server...
📝 [HH:MM:SS] Sending verification request...
⚠️ [HH:MM:SS] ⏱️ This may take 1-2 minutes, please wait...
📝 [HH:MM:SS] 🔍 SheerID GEMINI Student Verification
✅ [HH:MM:SS] Verification completed!
```

### Troubleshooting

| Error | Penyebab | Solusi |
|-------|---------|--------|
| ❌ Network Error | Backend belum dijalankan | Pastikan `npm start` sudah berjalan di terminal |
| ❌ Failed to fetch | URL salah atau port tidak cocok | Verifikasi BACKEND_URL di index.html = `http://localhost:3000` |
| ⚠️ Link is invalid or expired | Verification link sudah expired | Gunakan link yang baru |
| ⏱️ Timeout | Processing terlalu lama | Tunggu 1-2 menit, atau cek logs untuk detail error |

## File yang Dimodifikasi
- ✅ `index.html` (Line 632): Ubah BACKEND_URL ke `http://localhost:3000`

## Struktur Request-Response

### Frontend → Backend
```
POST http://localhost:3000/api/verify
Body: {
  url: "https://services.sheerid.com/verify/...",
  type: "gemini",
  sessionId: "session_xxx"
}
```

### Backend → SheerID API
```
POST https://services.sheerid.com/verification/{id}/step/collectStudentPersonalInfo
```

### Real-time Logs (SSE)
```
GET http://localhost:3000/api/logs?sessionId=session_xxx
```

## Endpoints Tersedia

| Endpoint | Method | Deskripsi |
|----------|--------|-----------|
| `/` | GET | Health check |
| `/api/verify` | POST | Jalankan verifikasi |
| `/api/logs` | GET (SSE) | Real-time logs streaming |

## Notes
- Backend berjalan di **port 3000**
- Frontend dapat berjalan di port berbeda (Live Server biasanya 5500)
- CORS sudah dikonfigurasi di server.js
- Logs streaming menggunakan Server-Sent Events (SSE)
