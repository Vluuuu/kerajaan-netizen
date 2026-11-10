# AGENTS.md — Kerajaan Netizen

> Instruksi untuk semua AI coding agents yang bekerja pada repository ini.

## Status proyek / batasan saat ini
**ACTIVE DEVELOPMENT, OWNER-GATED.** Berdasarkan laporan pengguna: Episode 1 dan Episode 2 sudah dipublikasikan, scene/simulasi Episode 2 dan viewer web MVP telah diimplementasikan di workspace Claude Code lokal. **Jangan berasumsi branch GitHub yang sedang dibaca sudah memuat seluruh kode lokal terbaru**; audit branch/working tree sebelum bekerja. Tidak boleh menambah fitur, dependency, memproduksi episode baru, memutasi canon, atau deploy tanpa permintaan eksplisit pemilik. Saat ini tugas yang disetujui **hanya mencatat arah game isometrik dan backlog/masterplan**, bukan mengeksekusinya.

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
- Dunia mulai dengan alam luas dan **satu castle kosong yang telah disiapkan Joko**, tetapi **tanpa manusia, raja, rumah, atau bangunan lain**; manusia pertama berasal dari komentar terpilih.
- Komentar manual lintas platform, **BUKAN voting**.
- Nama NPC = username netizen; satu netizen yang teridentifikasi = satu NPC permanen. Role awal ditentukan Joko.
- **Follower = Calon Warga Kerajaan**, bukan warga aktif atau NPC yang langsung dibangkitkan.
- Pembangunan awal oleh Joko, animasi lengkap di satu episode.
- Perubahan besar live di website saat episode tayang.
- Waktu hybrid; simulasi domain independen dari renderer; **video tetap 3D Three.js/Remotion, arah game publik 2D isometrik/2.5D** dari satu world canon.
- Visual ultra-low-poly sangat ringan; region jauh tidak perlu langsung aktif.
- Episode 1 menggunakan blueprint `docs/episodes/episode-01-blueprint.md`; Episode 2 (sudah tayang menurut pemilik) berisi **9 warga resmi dan 3 rumah pertama** sebagai asal **Kampung Pelopor** berdasarkan komentar netizen terpilih. Jangan mengarang cerita Episode 3 atau memindah rumah yang sudah tampil di video secara diam-diam.
- Tidak mencampur aset/lore/data Pulau Gobi.

## Arah kualitas tata ruang — wajib dibaca sebelum pekerjaan world-building berikutnya
- Baca **`docs/09-spatial-masterplan-backlog.md`** sebelum membuat/memindahkan bangunan, jalan, batas wilayah, atau mengubah terrain yang mempengaruhi akses.
- Kingdom harus punya hirarki ruang yang koheren: castle/citadel, pelataran dan jalur gerbang yang bebas, Kampung Pelopor (3 rumah lama), calon alun-alun, cadangan kampung baru, area pasar/kerajinan, pertanian/koridor sungai. **Zona calon bukan bangunan yang boleh dibuat begitu saja.**
- **Dilarang menebak titik koordinat atau menggeser bangunan historis**. Audit world snapshot/transform/footprint/jalan/sungai di source code aktual, tampilkan minimal dua opsi spatial plan untuk persetujuan kreator. Semua rencana bersifat editor-only sampai dipilih dan tayang di episode relevan.
- Setiap placement baru perlu pemeriksaan footprint+collision, kemiringan/height tanah, floodplain/river buffer, akses jalan dan NPC, framing kamera castle, performa, serta konsistensi snapshot/event yang deterministik.
- Peta/zoning/placement preview harus membedakan rencana vs world canon. Jangan mengubah world state atau website publik hanya karena preview.
- **Kreator sendiri yang menjalankan preview, screenshot, still frame, render Remotion, dan deployment secara manual.** Agent boleh menjalankan typecheck/lint/unit test dan build non-render yang diminta, tetapi jangan render otomatis, push, merge, atau deploy tanpa izin.

## Arah game publik — keputusan 2026-11-10, belum izin implementasi
- **Baca `docs/10-isometric-game-direction.md`** untuk pekerjaan website/game berikutnya. Game publik 2D isometrik/2.5D, video 3D sinematik; satu snapshot/event/koordinat world canon.
- Viewer 3D lokal dan proyek Remotion tidak boleh dihapus atau rusak karena peralihan UI game. Jangan membuat world save independen.
- Pilihan renderer masih perlu dievaluasi: sprite 2D hasil aset 3D, ortografik Three.js sebagai prototipe, atau hybrid. Kamera ortografik 3D **tidak otomatis setara renderer 2D ringan**. Perlu benchmark.
- Belum ada izin coding, asset generation massal, rendering screenshot/video otomatis, refactor penuh, atau deploy.

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
