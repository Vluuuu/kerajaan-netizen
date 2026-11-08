# AGENTS.md — Kerajaan Netizen

> Instruksi untuk semua AI coding agents yang bekerja pada repository ini.

## Status proyek / batasan saat ini
**PLANNING ONLY.** Dilarang membuat aplikasi, menulis implementasi fitur, menambah dependency, melakukan deployment, membuat database, mengubah arsitektur final, atau memasang skill tanpa persetujuan eksplisit pemilik proyek. Pekerjaan dokumentasi dan review saja diperbolehkan.

## Baca sebelum mengusulkan perubahan
1. `README.md`
2. `docs/01-vision-and-canon.md`
3. `docs/07-decisions.md`
4. `docs/04-architecture-proposal.md` (belum final)
5. `docs/05-engineering-standards.md`
6. Dokumentasi relevan lainnya.

## Canon yang tidak boleh diubah sembarangan
- Nama brand/channel disepakati **DUNIAJOKO.ID** (nama teknis repository tetap `kerajaan-netizen`); jangan menyimpulkan domain `duniajoko.id` telah dibeli atau terverifikasi. Nama kerajaan in-universe belum ditetapkan.
- Joko adalah pencipta dunia, **bukan raja**.
- Dunia mulai dengan alam luas, **tanpa manusia**; manusia pertama berasal dari komentar terpilih.
- Komentar manual lintas platform, **BUKAN voting**.
- Nama NPC = username netizen; satu netizen yang teridentifikasi = satu NPC permanen. Role awal ditentukan Joko.
- **Follower = Calon Warga Kerajaan**, bukan warga aktif atau NPC yang langsung dibangkitkan.
- Pembangunan awal oleh Joko, animasi lengkap di satu episode.
- Perubahan besar live di website saat episode tayang.
- Waktu hybrid; simulasi domain independen dari render 3D; web dan video dari satu world canon.
- Visual ultra-low-poly sangat ringan; region jauh tidak perlu langsung aktif.
- Tidak mencampur aset/lore/data Pulau Gobi.

## Sumber teknologi
- Three.js **resmi**: https://github.com/mrdoob/three.js
- Remotion Agent Skills **resmi**: https://github.com/remotion-dev/skills
- R3F, backend, database, deployment dan tambahan skills belum otomatis disetujui.

## Cara bekerja ketika implementasi DIIZINKAN di kemudian hari
- Mulai dengan memahami kode dan dokumen paling baru; tetapkan ruang lingkup/risiko/acceptance criteria.
- Beri rencana focused patch sebelum coding. Hindari refactor besar, rewriting, dependency dan tool baru tanpa justifikasi.
- Pisahkan domain simulation, visual presentation, persistence, user input, dan cinematic playback.
- Kunci identity stable IDs; jangan gunakan username sebagai primary key.
- Jangan menganggap browser berhak menulis canonical world state.
- Simulasi deterministik sejauh layak (clock terpisah, seeded randomness, snapshot/version).
- Buat recovery NPC untuk stuck path, missing target, resource conflict, action timeout, decision oscillation.
- Jalankan typecheck/lint/unit/integration/E2E sesuai fitur dan catat **bukti** hasilnya.
- Jika tes tidak bisa dijalankan, nyatakan 'NOT VERIFIED' beserta alasannya.
- Bugfix = reproduksi -> root cause -> minimal patch -> regression test -> verifikasi.
- Kerja branch -> PR -> review -> merge untuk perubahan kode; jika agent paralel, sepakati kepemilikan file/modul.
- Jangan auto-merge PR, deploy, atau mengubah live state tanpa izin pemilik.
- Jangan menghapus data atau world history permanen tanpa approval dan prosedur backup/restore.

## Format laporan kerja agent
- **Tujuan dan scope**
- **Keputusan/spec yang dijadikan dasar**
- **Perubahan per file**
- **Pengujian dijalankan dan hasil persisnya**
- **Risiko atau keterbatasan**
- **Hal yang perlu persetujuan**
