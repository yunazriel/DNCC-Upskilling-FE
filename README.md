# React + Tailwind CSS — Panduan Instalasi & Menjalankan Project

---

## Prasyarat

Pastikan sudah terinstall di komputer kamu:

- **Node.js** versi 18 ke atas → [nodejs.org](https://nodejs.org)
- **VSCode** → [code.visualstudio.com](https://code.visualstudio.com)
- **Git** → [git-scm.com](https://git-scm.com)

Cek apakah sudah terinstall:

```bash
node -v
git --version
```

---

## VSCode Extensions yang Direkomendasikan

| Extension | Fungsi | Status |
|---|---|---|
| ES7+ React/Redux/React-Native Snippets | Shortcut bikin komponen, ketik `rfc` → auto-generate | Wajib |
| Tailwind CSS IntelliSense | Autocomplete & preview class Tailwind | Wajib |
| Prettier – Code Formatter | Auto-format code saat save | Wajib |
| Auto Rename Tag | Rename opening tag → closing tag ikut otomatis | Rekomendasi |
| GitLens | Lihat history git per baris code | Rekomendasi |

---

## Cara Menjalankan Project

### 1. Clone repository

```bash
git clone https://github.com/yunazriel/DNCC-Upskilling-FE.git
```

### 2. Masuk ke folder project

```bash
cd nama-repo
```

### 3. Install dependencies

```bash
npm install
```

> ⚠️ Jangan skip langkah ini — tanpa `npm install` project tidak bisa jalan.

### 4. Jalankan project

```bash
npm run dev
```

Buka browser di: **http://localhost:5173**

---

## Kenapa `node_modules` Tidak Ada?

Folder `node_modules` berisi ribuan file dengan ukuran ratusan MB sehingga tidak di-upload ke GitHub. Cukup jalankan `npm install` dan semua dependencies akan didownload otomatis sesuai daftar di file `package.json`.
