# deutschklasse
# Portal Belajar Mandiri — Deutschklasse XII ULW (v2)

**Bahasa Jerman · Kelas XII ULW · SMKN 1 Sewon · Fase F · TP 2026/2027**
Penyusun: Yudha Nur Wicaksono

Portal web satu-link untuk siswa, dibuka lewat HP. Dibangun dengan React 18 + Tailwind CSS
(lewat CDN, tanpa proses build). Alur tiap materi: **video pengantar → rangkuman → latihan**.

## Cara membagikan
Buka galeri Artifacts (claude.ai/code/artifacts) → **Deutschklasse XII ULW** → menu Share.
Artifact privat sampai dibagikan. Isi bisa diperbarui kapan saja tanpa tautannya berubah.

## Struktur (v2)
| No | Materi | Video YouTube | Latihan |
|---|---|---|---|
| 01 | Kata Benda & Artikel Dasar | `4cRAhte5oe0` | 9 |
| 02 | Akkusativ für Anfänger & Kata Kerja | `4i5rbghwRto` | 12 |
| 03 | Keluarga & Kepemilikan (Possessivartikel) | `luhPMbPRs3o` | 16 |
| 04 | Aktivitas Bersama Teman | `1BVkzaBL_Hc` | 8 |
| 05 | Negasi: Membantah dengan nicht | `1jnW4aKkHtU` | 8 |
| 06 | Länder & Städte | — | 7 |
| ⚡ | Daily Challenge (5 soal campuran) | — | 5 |
| A–Z | Wortschatz / Kamus Cepat (90+ kata) | — | — |
| ★ | Akkusativ Survival Kit (artifact terpisah, tertaut) | — | 10 |

Total 65 latihan di dalam portal.

## Integrasi materi tercecer
- **Verben mit Akkusativ** (haben, brauchen, essen, trinken, sehen, kaufen, finden, kennen,
  nehmen) masuk sebagai sub-bab ketiga di Materi 02, tepat setelah The Golden Rule.
- **Negasi `nicht`** dipisah jadi Materi 05 dan diikat langsung ke Materi 04: dua baris teratas
  tabel posisi `nicht` memakai kalimat aktivitas jamak (`Wir spielen nicht Fußball`,
  `Ihr spielt nicht Gitarre`), dan Materi 04 ditutup dengan pengantar ke Materi 05.

## Catatan teknis penting
- **Embed YouTube tidak bisa dipakai di halaman Artifact.** Iframe sempat dipasang persis sesuai
  spesifikasi, tapi Content Security Policy halaman Artifact memblokir konten dari domain luar —
  yang muncul pesan *"This content is blocked. Contact the site owner to fix the issue."*
  Sejak v3, iframe diganti **kartu tautan** bertombol putar yang membuka video di tab YouTube.
  Kartu tetap diletakkan paling atas tiap materi, sebelum rangkuman, sehingga aturan video-first
  tetap terpenuhi. Kelas `aspect-video w-full` ikut dilepas karena tidak ada lagi player yang
  perlu dijaga rasio-nya.
- **Kalau video ingin benar-benar tertanam** (bisa diputar tanpa pindah tab), portal harus
  di-hosting di luar Artifact — GitHub Pages, Netlify, atau server sekolah. Di sana tidak ada
  pembatasan tersebut. File HTML-nya bisa diminta kapan saja.
- **Isi video belum terverifikasi.** YouTube memblokir akses pemeriksaan, jadi ID video dipakai
  apa adanya sesuai yang diberikan. Video A/B pada spesifikasi Materi 4 dibagi: A ke Materi 04
  (aktivitas), B ke Materi 05 (negasi). Bisa ditukar kalau ternyata terbalik.
- **Progres siswa aman.** Kunci penyimpanan dan id materi tidak diubah, jadi nilai terbaik yang
  sudah tercatat di HP siswa tetap terbawa antarversi.
- Daftar nama siswa pada Lampiran 3 kedua modul **tidak** dimasukkan (data pribadi).
- Contoh `telefonieren + Akkusativ` diganti `besuchen / sehen / kennen` (bentuk baku
  `telefonieren mit + Dativ`, atau `anrufen` yang transitif).
- `die USA` ditandai jamak → `aus / in den USA`.

## Tindak lanjut
Materi baru tinggal ditambahkan sebagai entri di array `TOPICS`. Soal Daily Challenge ada di
array `CHALLENGE`. Minta saja kalau perlu ditambah atau diubah.

## Versi mandiri untuk GitHub Pages (`index.html`)
Selain versi Artifact, ada berkas `index.html` mandiri: dokumen HTML5 utuh, satu file, tanpa
proses build. React 18 (UMD) dan Tailwind dipanggil dari CDN, jadi tidak perlu Node.js/NPM/Vite.

- **Iframe YouTube aktif kembali** di versi ini (GitHub Pages tidak memberlakukan CSP seperti
  halaman Artifact). Wadahnya `aspect-video w-full`; di belakangnya tetap ada panel cadangan
  bertombol putar, dan di bawahnya tautan "Buka di YouTube" untuk jaringan sekolah yang memblokir.
- Pemuat React memakai jsDelivr sebagai CDN utama dengan unpkg sebagai cadangan, plus pesan
  ramah kalau keduanya gagal.
- **Perlu diperhatikan:** kartu *Akkusativ Survival Kit* menuju halaman Artifact di claude.ai.
  Supaya bisa dibuka siswa dari situs publik, artifact itu harus dibagikan dulu lewat menu Share —
  kalau tidak, kartunya sebaiknya dihapus dari `index.html`.
- Cara terbit: repo GitHub publik → unggah `index.html` di root → Settings → Pages →
  Deploy from a branch → branch `main`, folder `/ (root)` → Save. Tautan terbit dalam 1–3 menit
  di `https://<username>.github.io/<nama-repo>/`. Memperbarui isi cukup dengan mengunggah ulang
  `index.html` bernama sama.
