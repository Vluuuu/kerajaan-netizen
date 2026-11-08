# MVP & Roadmap — Proposal

> **Belum disetujui untuk coding.** Milestone di bawah untuk menilai kelayakan dan mencegah scope creep.

## M0 — Dokumentasi dan keputusan
**Tujuan:** aturan dunia, identitas karakter, rencana simulasi, kontrak world state, dan sumber data video jelas.

**Done when:** canon vs proposal tercatat; rute data dari komentar sampai episode dipetakan; risiko prioritas diidentifikasi; tugas demo teknis disepakati.

## M1 — 3D visual proof of concept (setelah izin implementasi)
**Tujuan:** bukti ultra-low-poly lembah luas dekat sungai dapat tampil ringan di browser desktop/mobile.

**Scope maksimal awal:** 1 area render detail, lanskap jauh murah, kamera aerial pan/rotate/zoom, 1 prefab sederhana untuk uji animasi (bukan NPC kanonis jika Episode 1 masih tanpa manusia).

**Gate:** scene memuat, kontrol konsisten, tidak ada error WebGL utama; performa dan penggunaan memori **diukur** di perangkat referensi, lalu budget difinalkan.

## M2 — NPC vertical slice & persistensi
**Tujuan:** uji NPC live tanpa rendering sebagai ketergantungan.

**Scope:** 1–3 NPC uji/simulasi (data dummy nonkanonis); kebutuhan lapar & energi, keputusan bekerja/makan/istirahat, satu interaksi NPC, navigasi sederhana dan fallback, penyimpanan/reload.

**Gate:** state valid dan tahan restart, tidak ada duplikasi NPC akibat reprocess, dua NPC tidak dapat memakai resource eksklusif bersamaan, stuck dapat pulih; tes unit/integration minimum lulus.

## M3 — World canon & episode activation
**Tujuan:** perubahan dari komentar terpilih menjadi status dunia yang aman dan bisa ditelusuri.

**Scope:** alur kurasi manual, record asal komentar, NPC warga resmi dengan username, event pending/published, creator activation manual, snapshot versi.

**Gate:** event terpublikasi tepat sekali, identitas tidak terduplikasi, situs tidak menampilkan spoiler pending, visitor read-only.

## M4 — Remotion proof of concept
**Tujuan:** satu video contoh yang memakai world snapshot dan aset/scene definitions bersama.

**Scope:** 1080x1920 @30fps, shot camera ringan, animasi pembangunan lengkap dalam satu episode, subtitle dan VO/SFX placeholders yang sah, hasil terkunci.

**Gate:** rerender snapshot sama konsisten, situs menunjukkan hasil episode setelah activation, sejarah dunia tidak hilang.

**Catatan:** prototipe video kecil perlu dieksplorasi **awal** untuk menemukan masalah kompatibilitas Three.js/Remotion; M4 berarti penyelesaian pipeline utuh, bukan menunda eksperimen integrasi sampai akhir.

## M5 — Publikasi terbatas & QA
**Tujuan:** validasi penggunaan website dan keberlanjutan proses konten.

**Scope:** pengujian perangkat nyata dan akses publik terbatas, monitoring dasar, backup/restore, moderasi dasar, rate limits bila ada input publik.

**Gate:** smoke-test lulus, tidak ada bug blocker yang diketahui, data penting dapat dipulihkan, biaya operasional dipahami.

## Hal di luar MVP
- Multiplayer/avatar yang dikendalikan penonton.
- Menikah/beranak/menua/meninggal.
- Perang/bencana/pemberontakan skala besar.
- Simulasi seluruh region jauh pada tiap tick.
- AI generatif/LLM percakapan tiap NPC.
- Ekonomi kompleks, jaringan kerajaan/negara lain.
- Automated ingestion semua komentar/followers atau verifikasi follow.

## Aturan proses
- Scope tiap milestone jelas dan kecil.
- Tes/regresi/risiko ditulis sebelum 'done'.
- Bug yang memengaruhi data, scene dasar, atau pipeline episode diselesaikan sebelum memperluas NPC atau region.
- Jangan menyatakan fitur sudah ada karena tertulis di roadmap.
