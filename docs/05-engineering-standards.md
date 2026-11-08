# Engineering & Quality Standards — Planning Policy

**Status:** prinsip untuk implementasi masa depan, **bukan perintah membangun seluruh infrastrukturnya sekarang**. Terapkan bertahap sesuai risiko dan ukuran tim kecil + AI coding agents.

## 1. Architecture first
- Klarifikasi ruang lingkup, modul, kontrak data, pemilik world state, dan dampak perubahan sebelum coding.
- Pisahkan simulation domain, renderer 3D, UI pengunjung, persistence, command authorization, video playback.
- Hindari arsitektur besar tanpa bukti kebutuhan.

## 2. Single source of truth
- Web dan Remotion membaca world canon yang konsisten; tidak memelihara dua dunia independen.
- Gunakan stable entity ID, versioned schemas, snapshots/event history secukupnya.
- Bedakan draft peristiwa episode, world state live, dan snapshot video immutable.

## 3. NPC reliability
- NPC harus dapat menyelesaikan tugas dan pulih dari kegagalan navigasi, target tidak tersedia, konflik reservasi resource, serta kebutuhan bertentangan.
- Timeout, cooldown, fallback, dan diagnosa stuck/decision thrashing.
- Animasi mengikuti simulasi, tidak menentukan state faktual.
- Uji reload, restart, dan catch-up offline.

## 4. Deterministic simulation & video
- Evaluasi fixed timestep/seeded randomness; log parameter dan versi aturan.
- Pisahkan clocks: simulation, browser animation, Remotion frames.
- Simpan snapshot + versi aset/komposisi yang dibutuhkan render ulang episode.
- Perbaikan simulasi di masa depan tidak boleh diam-diam mengubah hasil video terdahulu.

## 5. Performance
- Profiling dulu, kemudian tentukan budget berdasarkan mobile target nyata.
- Perhatikan draw calls, polygon count, jumlah instance, material, tekstur, texture compression, culling, LOD, lazy loading, caching, memori, disposal Three.js, dan jumlah NPC aktif.
- Avoid false optimization: tidak perlu shader rumit/LOD engine khusus sebelum benchmark membutuhkannya.
- Tetapkan gate performa terukur **setelah** benchmark awal, bukan angka spekulatif.

## 6. Automated testing berbasis risiko
- Unit tests untuk kebutuhan, pilihan aksi, aturan waktu, identitas, dan resource.
- Integration tests untuk save/restore, event publication idempotency, snapshot, schema migration.
- E2E untuk buka website, load scene, kamera, klik NPC, serta read-only visitor permissions.
- Visual screenshot/snapshot regression untuk perubahan 3D yang penting.
- Smoke build/deploy dan regression tests untuk bug yang ditemukan.
- Persentase coverage bukan satu-satunya tanda mutu.

## 7. Save-data integrity
- Stable IDs, validasi schema, migrations, atomic transitions, transaction untuk multi-entity changes.
- Backup dan **uji restore**; catat schema version dan strategi rollback.
- Jangan menghapus data NPC/netizen atau bangunan permanen akibat refactor/upgrade.
- Batasi operasi concurrency; perubahan publikasi harus idempotent.

## 8. Security & privacy
- Semua write otoritatif hanya melalui backend/alat admin terotorisasi; validasi server-side.
- RBAC sederhana (visitor read-only vs Joko/admin) pada MVP.
- Rate limiting, sanitasi username/komentar, XSS prevention, input moderation, secrets management, API protection.
- Audit perubahan penting, hindari mencatat token atau informasi sensitif dalam log.
- Jangan mengasumsikan follow/identitas lintas platform bisa diverifikasi otomatis.

## 9. GitHub workflow
- Dokumen awal di-bootstrap; pekerjaan fitur selanjutnya melalui branch focused -> PR -> review -> checks -> merge.
- CI minimum saat kode benar-benar ada: typecheck, lint, test, build; tambah performance/visual test bila layak.
- Commits punya tujuan jelas, release tags untuk milestone stabil, dokumentasi keputusan teknis (ADR) untuk perubahan arsitektur.
- Untuk agent paralel, tetapkan file ownership/area kerja dan satu integrator; hindari edit file sama secara bersamaan.

## 10. Debugging & regressions
1. Reproduksi bug dan dokumentasikan kondisi.
2. Tentukan penyebab yang terbukti, bukan gejala.
3. Patch minimal dan scoped.
4. Tambah regression test bila relevan.
5. Jalankan pengujian yang terkait dan catat hasil.
6. Laporkan keterbatasan serta risiko tersisa.
Tidak ada klaim 'fixed' bila pengujian belum dilakukan.

## 11. Observability
- Rancang structured logs yang menautkan NPC ID, event ID, simulation tick, world version, request ID bila ada.
- Catat invalid action, stuck navigation, failure to save, recovery; error tracking dan performance metrics ditambah sesuai kebutuhan nyata.
- Data log minimum, tanpa data sensitif atau kredensial.

## 12. Incremental development
- Setiap milestone: goal, scope, acceptance criteria, tests, risiko, evidence.
- Batasi pekerjaan simultan; stabilkan vertical slice sebelum menambah fitur besar.
- Bukan target membuat semua sistem sekaligus.

## 13. Definition of Done
Fitur disebut selesai hanya ketika:
- sesuai spesifikasi terbaru dan tidak mengubah canon tanpa persetujuan;
- lulus tes terkait serta review;
- tidak ada error kritis yang diketahui;
- world state, data, akses, dan performa sesuai kriteria yang telah disepakati;
- dokumentasi terdampak diperbarui;
- keterbatasan dan status verifikasi dilaporkan.
'Belum diuji' berarti **belum terverifikasi**, bukan selesai.

## 14. AI coding agent conduct
- Baca README, AGENTS.md, keputusan, ADR, dan kode terbaru sebelum mengusulkan perubahan.
- Sebelum coding: rencana singkat, impacted modules, risiko, tes rencana.
- Focused patch. Jangan menghapus perilaku lama, mencampur proyek Pulau Gobi, melakukan refactor besar tidak diminta, atau menambah dependency tanpa justifikasi.
- Jalankan checks yang tersedia dan berikan bukti nyata, jangan mengarang output test.
- Jangan melakukan deployment, mutasi database, atau tindakan destruktif tanpa izin yang sesuai.

## Prioritas penerapan
**Dokumentasi sekarang:** canon, decision log, agent rules, MVP, risk register.

**Milestone implementasi awal (setelah disetujui):** typecheck/lint/tests minimal, stable IDs, save/restore, smoke test web, basic logging, manual backup/restore.

**Belakangan jika diperlukan:** CI visual regression menyeluruh, monitoring lengkap, load-test skala besar, auth publik multi-role, queueing, sophisticated asset streaming, multiplayer.

Ini standar operasional proporsional, bukan checklist untuk memaksakan seluruh teknologi di hari pertama.
