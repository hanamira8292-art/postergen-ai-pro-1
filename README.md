# PosterGen AI Pro — Cloudflare Pages

Projek HTML/CSS/JavaScript tanpa build framework, dengan Cloudflare Pages Function untuk penjanaan imej OpenAI.

## Kandungan
- `index.html`, `style.css`, `app.js` — antaramuka Studio, Templat dan Galeri
- `manifest.webmanifest` — metadata PWA
- `functions/api/generate.js` — backend Cloudflare Pages di `/api/generate`
- `_routes.json` — jalankan Function untuk laluan API sahaja

## Deploy menggunakan Android + GitHub
1. Ekstrak ZIP dan muat naik **isi folder** projek ke root repositori GitHub (pastikan `index.html` dan `functions/` di root, bukan dalam subfolder).
2. Buka https://dash.cloudflare.com/ di Chrome, log masuk.
3. Buka **Workers & Pages** → **Create** → **Pages** → **Connect to Git** (nama butang boleh berubah).
4. Benarkan akses GitHub dan pilih repositori PosterGen.
5. Framework preset: **None**; Build command: **kosong**; Build output directory: **/** atau **.** mengikut pilihan dashboard. Jika Cloudflare memerlukan direktori output khusus, tetapkan `public` dan pindahkan fail statik ke folder `public` (kekalkan `functions` di root).
6. Deploy. Domain akan berbentuk `nama-projek.pages.dev`.
7. Cloudflare → Workers & Pages → projek → **Settings → Variables and Secrets** (atau Environment variables) → tambah `OPENAI_API_KEY` sebagai **Secret** untuk Production. Simpan dan **Redeploy**.
8. Cuba Studio → isi prompt → Jana Poster AI. API key mesti mempunyai akses imej OpenAI dan baki kredit API.

**Penting:** GitHub-connected Cloudflare Pages menyokong folder `functions/`. Kaedah Direct Upload di dashboard mungkin tidak menerbitkan Functions daripada ZIP; gunakan Git integration atau Wrangler untuk backend.

## Semakan
- Demo, galeri dan editor poster boleh digunakan tanpa API key.
- API `/api/generate` memerlukan Cloudflare Pages Functions; membuka `index.html` terus dari storan telefon tidak akan menjalankan API.
- Poster galeri disimpan secara tempatan dalam browser; padam data pelayar boleh memadam galeri.
- Label kredit dalam UI bukan baki sebenar; tiada pembayaran, login, kuota atau rate limiting. **Jangan terbitkan API berbayar kepada umum tanpa kawalan penggunaan / autentikasi.**
- Sesetengah model imej dan saiz memerlukan akses dan bil OpenAI yang aktif. Fungsi mungkin tertakluk pada had masa dan saiz respons Cloudflare.
