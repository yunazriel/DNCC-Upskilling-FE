# React + Tailwind CSS — Panduan Setup

Panduan lengkap instalasi dan setup project **React** dengan **Tailwind CSS v4** menggunakan **Vite**.

---

## Prasyarat

Pastikan sudah terinstall di komputer kamu:

- **Node.js** versi 18 ke atas → [nodejs.org](https://nodejs.org)
- **VSCode** → [code.visualstudio.com](https://code.visualstudio.com)

Cek versi Node.js:

```bash
node -v
```

---

## VSCode Extensions yang Direkomendasikan

Install ekstensi berikut sebelum mulai coding:

| Extension | Fungsi | Status |
|---|---|---|
| ES7+ React/Redux/React-Native Snippets | Shortcut bikin komponen, ketik `rfc` → auto-generate | Wajib |
| Tailwind CSS IntelliSense | Autocomplete & preview class Tailwind | Wajib |
| Prettier – Code Formatter | Auto-format code saat save | Wajib |
| Auto Rename Tag | Rename opening tag → closing tag ikut otomatis | Rekomendasi |

---

## Membuat Project Baru

### 1. Buat project React dengan Vite

Ada dua cara, pilih salah satu:

**Cara 1 — Interaktif (muncul pilihan di terminal):**
```bash
npm create vite@latest nama-project
```

Ikuti pilihan berikut saat muncul:
```
? Select a framework › React
? Select a variant  › JavaScript
```

**Cara 2 — Langsung tanpa pilihan:**
```bash
npm create vite@latest nama-project -- --template react
```

### 2. Masuk ke folder project

```bash
cd nama-project
```

### 3. Install dependencies bawaan

```bash
npm install
```

---

## Instalasi Tailwind CSS v4

### 1. Install package Tailwind

```bash
npm install tailwindcss @tailwindcss/vite
```

> ⚠️ **Jika muncul error konflik versi**, jalankan perintah berikut untuk downgrade Vite terlebih dahulu:
> ```bash
> npm install vite@7 @vitejs/plugin-react@4 --save-dev
> ```
> Lalu install ulang Tailwind:
> ```bash
> npm install tailwindcss @tailwindcss/vite
> ```

### 2. Daftarkan plugin di `vite.config.js`

Buka file `vite.config.js`, lalu sesuaikan menjadi seperti ini:

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
})
```

### 3. Setup `src/index.css`

sesuikan dengan project kalian nanti ya ges, contohnya seperti ini

```css
@import "tailwindcss";

@theme {
  --color-primary-50: #fff1f1;
  --color-primary-100: #ffe0e0;
  --color-primary-200: #ffc5c5;
  --color-primary-300: #ff9d9d;
  --color-primary-400: #ff6464;
  --color-primary-500: #ed1c24;
  --color-primary-600: #d91920;
  --color-primary-700: #c8151c;
  --color-primary-800: #a51218;
  --color-primary-900: #881414;
  --color-dark: #111111;
  --color-light: #f8f8f8;

  --font-body: "Roboto", sans-serif;
  --font-heading: "Roboto", sans-serif;
  --font-sans: "Plus Jakarta Sans", sans-serif;
  --animate-fade-in: fadeIn 0.6s ease-out forwards;
  --animate-slide-up: slideUp 0.6s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@layer base {
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  html {
    scroll-behavior: smooth;
  }

  body {
    font-family: var(--font-body);
    color: var(--color-dark);
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  h1, h2, h3, h4, h5, h6 {
    font-family: var(--font-heading);
    font-weight: 700;
  }

  p {
    font-family: var(--font-body);
  }
}

@layer utilities {
  .container-page {
    width: 100%;
    margin: 0 auto;
    padding-left: 1rem;
    padding-right: 1rem;
  }

  @media (min-width: 1024px) {
    .container-page {
      padding-left: 1.5rem;
      padding-right: 1.5rem;
    }
  }

  .container-inner {
    width: 100%;
    max-width: 1400px;
    margin: 0 auto;
  }
}
```

> ✅ Tailwind v4 cukup satu baris `@import "tailwindcss"` — tidak perlu lagi `tailwind.config.js` dan tidak perlu 3 baris `@tailwind base/components/utilities` seperti versi sebelumnya.

---

## Instalasi React Router

React Router digunakan untuk berpindah antar halaman tanpa reload browser.

```bash
npm install react-router-dom
```

### Setup `src/App.jsx`

Setelah install, buka `src/App.jsx` dan sesuaikan seperti ini. Tambahkan halaman baru sesuai kebutuhan project kamu:

```jsx
import "./index.css";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import LandingPage from "./pages/LandingPage";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<LandingPage />} />
        {/* Tambahkan route lain di sini */}
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

> 💡 Setiap halaman baru = buat file baru di folder `pages/`, lalu tambahkan `<Route>` baru di sini.

---

## Menjalankan Project

```bash
npm run dev
```

Buka browser di: **http://localhost:5173**

---

## Struktur Folder yang Direkomendasikan

```
src/
├── assets/          → gambar, icon, font
├── components/
│   ├── ui/          → komponen kecil reusable (Button, Input, Card)
│   └── layout/      → komponen layout (Navbar, Footer, Sidebar)
├── pages/           → satu file = satu halaman
├── hooks/           → custom React hooks
├── utils/           → helper functions
├── App.jsx
├── main.jsx
└── index.css
```