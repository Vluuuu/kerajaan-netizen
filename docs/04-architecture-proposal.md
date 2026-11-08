# Architecture Proposal — NOT APPROVED FOR IMPLEMENTATION

> Dokumen ini hanya opsi desain awal. Tidak memberi izin agent membuat kode, database, API, deployment, atau infrastruktur.

## Batas sistem yang diusulkan
1. **World domain / simulation**: entitas NPC, bangunan, region, resource, clock, aturan, keputusan; tidak bergantung pada Three.js atau Remotion.
2. **Persistence & history**: canonical world state, durable IDs, migrations, audit events, snapshots, backup.
3. **Command/approval layer**: validasi dan otorisasi perintah Joko; browser pengunjung tidak boleh mengubah world state otoritatif.
4. **World delivery API**: menyediakan snapshot/konten terpublikasi dan read models untuk website.
5. **3D browser renderer**: render world state dengan Three.js; kontrol kamera, interaksi klik, UI.
6. **Video production**: Remotion membaca snapshot episode dan aset kanonis, memakai animation clock berbasis frame.
7. **Creator tools**: memilih komentar, meninjau perubahan, mengunci snapshot episode, dan publikasi. MVP bisa manual, belum perlu CMS besar.

## Alur data
Komentar manusia -> **kurasi Joko** -> command terotorisasi -> status perubahan pending -> snapshot episode + aset -> render Remotion -> publikasi episode -> apply event ke canonical world state -> world read API -> website 3D.

Aktivitas NPC rutin: simulation clock -> state transition -> persistence/event history -> world read API -> website 3D. Sinematik memakai snapshot terkunci; tidak menulis balik ke live simulation.

## Single source of truth
- Satu world state otoritatif, **bukan** satu state web dan satu state video yang dihitung sendiri-sendiri.
- Stable entity IDs, schema version, event IDs, time/idempotency keys.
- Snapshot sebagai potongan status saat waktu tertentu. Event history sebagai audit perubahan penting. Full event sourcing **opsional**, bukan persyaratan.
- Perintah write harus tervalidasi; perubahan publikasi besar harus idempotent/atomic agar posting ulang tidak menduplikasi NPC atau bangunan.

## Kandidat stack (belum final)
- **Three.js resmi** (https://github.com/mrdoob/three.js) untuk 3D. R3F **opsional** jika terbukti mempermudah integrasi React, bukan syarat dan bukan pengganti Three.js.
- **Remotion + skill resmi** (https://github.com/remotion-dev/skills) untuk produksi video.
- TypeScript untuk domain/simulation agar dapat digunakan ulang oleh tool terkait.
- Backend Node/TypeScript dan PostgreSQL **kandidat**, bukan keputusan.
- Deployment, hosting, autentikasi kreator, penyimpanan aset, job scheduling: belum dipilih.

## Time, simulation & rendering
- Pisahkan simulation clock (waktu dunia), renderer clock (browser), dan cinematic frame clock (video).
- Evaluasi fixed simulation timestep + seeded randomness pada bagian relevan.
- Simulasi bisa berjalan headless/periodik dengan catch-up yang dibatasi; **tidak** perlu render 3D 24/7 di server.
- Waktu jauh tanpa pengunjung tidak perlu dihitung tiap frame; pilih kebijakan rekonstruksi yang deterministik dan diuji.
- Render visual selalu membaca state; animasi tidak menjadi otoritas peristiwa.

## Risiko arsitektur yang perlu diuji
- State NPC konsisten saat reload/restart dan catch-up offline.
- Race condition saat dua NPC memperebutkan resource atau dua event publikasi bersamaan.
- Identitas akun berganti username atau menggunakan nama yang sama lintas platform.
- Konsistensi versi snapshot video dengan schema terbaru.
- Performa/browser mobile dan memori aset pada world yang terus bertambah.
- Sinkronisasi status tayang video dan apply world event.
- Biaya database, server simulasi, penyimpanan snapshot/aset, dan render.

## Anti-overengineering
Tidak perlu microservices, real-time multiplayer, full event sourcing, LLM per NPC, procedural planet, persistent GPU rendering atau queue kompleks untuk MVP. Pilih keputusan teknis setelah vertical slice terbukti, catat alasannya dalam ADR.
