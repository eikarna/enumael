<div align="center">

# ⚡ Qoder Automation

**Full Automation dengan UI Interaction — Auto-claim Pro Trial + 300 Credits untuk Qoder**

![Version](https://img.shields.io/badge/version-5.0.0-blue)
![Python](https://img.shields.io/badge/Python-3.8%2B-yellow?logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-lightgrey)
![Playwright](https://img.shields.io/badge/Playwright-Stealth-2EAD33?logo=playwright&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-green)

[Fitur](#-fitur) • [Instalasi](#-instalasi) • [Cara Pakai](#-cara-menggunakan) • [Menu](#-daftar-menu) • [FAQ](#-faq)

</div>

---

## 📖 Tentang

Script Python berbasis **Playwright + Stealth** yang mengotomatisasi proses login akun Qoder melalui interaksi UI penuh (klik tombol Sign In, isi form, dll.), lengkap dengan fitur patching data aplikasi, reset menyeluruh, dan logging.

> 💡 Cocok untuk kamu yang ingin mengelola banyak akun tanpa klik manual satu per satu.

---

## ✨ Fitur

| Fitur | Keterangan |
|:---:|---|
| 🤖 | **Auto Client Login** — proses semua akun otomatis dengan interaksi UI penuh (headless + stealth) |
| 🛡️ | **Stealth Mode** — `camoufox` + `playwright-stealth` untuk menghindari deteksi bot |
| 🔧 | **Patch Qoder Data** — generate identitas baru (fake MAC, machine ID, MS device ID, UMID) |
| ♻️ | **Reset & Deep Reset** — reset aplikasi Qoder, termasuk opsi hapus semua data |
| 🖥️ | **Multi-Platform** — macOS, Windows, Linux (bisa diganti saat runtime) |
| 📄 | **Logging & Hasil** — semua aktivitas tercatat, hasil sukses/gagal terpisah |
| ⏭️ | **Smart Skip** — email yang sudah sukses tidak diproses ulang |
| ⏳ | **Random Delay** — jeda acak 30–60 detik antar akun agar lebih natural |

---

## 📋 Persyaratan

- ✅ Python **3.8+**
- ✅ Aplikasi **Qoder** sudah terinstall
- ✅ **Google Chrome** terinstall (direkomendasikan — dipakai sebagai browser prioritas)

---

## 🚀 Instalasi

### ⚡ Quick Start

```bash
git clone https://github.com/okky-x0f/qoder-creator.git
cd qoder-creator
pip install -r requirements.txt
python main.py
```

<details>
<summary><b>📦 Instalasi lengkap dengan virtual environment (klik untuk membuka)</b></summary>

<br>

```bash
# 1. Clone repository
git clone https://github.com/okky-x0f/qoder-creator.git
cd qoder-creator

# 2. Buat virtual environment (opsional tapi disarankan)
python3 -m venv venv
source venv/bin/activate        # macOS/Linux
# venv\Scripts\activate         # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Install browser Playwright (juga dicek otomatis saat script berjalan)
playwright install
```

</details>

### 📚 Dependencies

| Package | Fungsi |
|---|---|
| [`boto3`](https://pypi.org/project/boto3/) | AWS SDK |
| [`colorama`](https://pypi.org/project/colorama/) | Output warna di terminal |
| [`fake-useragent`](https://pypi.org/project/fake-useragent/) | User-Agent acak |
| [`camoufox`](https://pypi.org/project/camoufox/) | Browser anti-deteksi |
| [`playwright`](https://pypi.org/project/playwright/) | Otomasi browser/UI |
| [`playwright-stealth`](https://pypi.org/project/playwright-stealth/) | Plugin stealth untuk Playwright |

---

## 🏃 Cara Menggunakan

### Langkah 1️⃣ — Jalankan script

```bash
python main.py
```

### Langkah 2️⃣ — Pilih platform

```text
1. macOS (Default)
2. Windows
3. Linux
```

### Langkah 3️⃣ — Siapkan file akun

Buat file `qoder_akun.txt` di folder yang sama dengan `main.py`, satu akun per baris:

```text
email1@example.com|password1
email2@example.com|password2
```

> ⚠️ **Format wajib:** `EMAIL|PASSWORD` dipisahkan karakter `|`

### Langkah 4️⃣ — Pilih menu dan biarkan script bekerja 🎉

---

## 📜 Daftar Menu

| No | Menu | Kategori | Keterangan |
|:--:|---|---|---|
| `1` | Process All Accounts | 🔐 Login | Proses semua akun di `qoder_akun.txt` secara otomatis |
| `2` | Process Single Account | 🔐 Login | Login satu akun (input email & password manual) |
| `3` | Patch Qoder Data | 🔧 Patch | Generate identitas baru & patch data aplikasi |
| `4` | Reset Qoder Completely | 🔧 Patch | Reset aplikasi Qoder (dengan konfirmasi) |
| `9` | Deep Reset (All Data) | 🔧 Patch | Hapus **SEMUA** data Qoder (dengan konfirmasi) |
| `5` | Change Platform | 🖥️ Platform | Ganti target platform saat runtime |
| `6` | View Results | 🛠️ Utility | Lihat 10 hasil sukses terakhir + jumlah credits |
| `7` | View Log | 🛠️ Utility | Lihat 20 entri log terakhir |
| `8` | Check Qoder Status | 🛠️ Utility | Cek binary, data directory, dan status instalasi |
| `0` | Exit | — | Keluar dari program |

---

## 📁 File Output

File-file ini dibuat otomatis oleh script saat berjalan:

| File | Isi |
|---|---|
| 📥 `qoder_akun.txt` | Daftar akun input — format `EMAIL\|PASSWORD` |
| ✅ `qoder_sukses.txt` | Akun berhasil — format `email\|{data, credits}\|timestamp` |
| ❌ `qoder_failed.txt` | Akun gagal — format `email\|error\|timestamp` |
| 📝 `qoder_log.txt` | Log aktivitas lengkap dengan timestamp |

> 🔒 **Tips:** jangan commit file-file ini ke repository. Lihat bagian [.gitignore](#-keamanan--gitignore) di bawah.

---

## 🏗️ Struktur Kode

<details>
<summary><b>Komponen utama di <code>main.py</code> (klik untuk membuka)</b></summary>

<br>

| Komponen | Keterangan |
|---|---|
| `QoderClientAutomation` | Otomasi login client via Playwright (stealth, UI interaction) |
| `QoderPatcher` | Patching data aplikasi & generate identitas baru per platform |
| `get_platform_config()` | Konfigurasi path aplikasi Qoder per platform |
| `init_platform()` | Inisialisasi path berdasarkan platform yang dipilih |
| `ensure_playwright_browsers()` | Cek & pastikan browser Playwright/Chrome tersedia |
| `reset_qoder_completely()` | Reset aplikasi Qoder secara menyeluruh |
| `reset_qoder_deep()` | Deep reset — hapus semua data Qoder |

</details>

---

## ❓ FAQ

<details>
<summary><b>Browser tidak ditemukan / Playwright error?</b></summary>

<br>

Jalankan install browser secara manual:

```bash
playwright install
```

Script juga akan mencoba mengecek dan menginstall browser secara otomatis saat startup.

</details>

<details>
<summary><b>Script tidak menemukan aplikasi Qoder?</b></summary>

<br>

Pastikan Qoder terinstall di path standar:

- **macOS:** `/Applications/Qoder.app`
- **Windows:** `C:\Program Files\Qoder\` atau `%LOCALAPPDATA%\Qoder\`
- **Linux:** `/usr/bin/qoder` atau `/usr/local/bin/qoder`

Gunakan menu **8 (Check Qoder Status)** untuk memverifikasi deteksi aplikasi.

</details>

<details>
<summary><b>Akun saya tidak diproses ulang, kenapa?</b></summary>

<br>

Ini fitur **Smart Skip** — email yang sudah tercatat sukses di `qoder_sukses.txt` otomatis dilewati. Hapus baris email tersebut dari `qoder_sukses.txt` jika ingin memprosesnya lagi.

</details>

---

## 🔐 Keamanan & .gitignore

File `qoder_akun.txt` berisi **kredensial akun** — jangan pernah di-upload ke repository publik. Tambahkan `.gitignore` berikut:

```gitignore
qoder_akun.txt
qoder_sukses.txt
qoder_failed.txt
qoder_log.txt
venv/
__pycache__/
```

---

## ⚠️ Disclaimer

> Project ini dibuat untuk tujuan **edukasi dan pembelajaran otomasi** saja. Penggunaan script ini dapat melanggar Terms of Service dari Qoder. Segala risiko penggunaan sepenuhnya menjadi tanggung jawab pengguna. **Gunakan dengan bijak.**

---

## 📄 Lisensi

Dilisensikan di bawah [MIT License](LICENSE) © [okky-x0f](https://github.com/okky-x0f)

---

<div align="center">

⭐ **Suka dengan project ini? Beri bintang di repository ini!** ⭐

[🐛 Report Bug](https://github.com/okky-x0f/qoder-creator/issues) • [💡 Request Feature](https://github.com/okky-x0f/qoder-creator/issues)

</div>
