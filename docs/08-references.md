# References & Skills — Curated, not blindly installed

## Resmi dan diprioritaskan
- **Three.js source**: https://github.com/mrdoob/three.js
- **Three.js documentation**: https://threejs.org/docs/
- **Three.js examples**: https://threejs.org/examples/
- **Remotion Agent Skills**: https://github.com/remotion-dev/skills
- **Remotion documentation**: https://www.remotion.dev/docs/
- **Remotion Three.js / React Three Fiber integration**: https://www.remotion.dev/docs/three

## Penting: bedakan library vs Agent Skill
- `mrdoob/three.js` adalah **source code library**, bukan paket instruksi agent `SKILL.md`; gunakan sebagai rujukan resmi library dan implementasi grafis.
- `remotion-dev/skills` adalah **kumpulan Agent Skills resmi** yang dapat diinstal ke tool agent kompatibel.
- Skill komunitas Three.js bukan sumber utama default dan tidak perlu dimasukkan tanpa alasan yang disetujui.

## Referensi tambahan yang mungkin dievaluasi nantinya
- React Three Fiber: https://r3f.docs.pmnd.rs/ — wrapper React opsional untuk Three.js, bukan penggantinya.
- Playwright: https://playwright.dev/ — E2E browser, baru dipakai saat kode ada.
- Dokumentasi PostgreSQL: https://www.postgresql.org/docs/ — kandidat database; belum dipilih.

## Panduan memilih skill untuk AI agent
1. Pilih skill resmi/provider pertama jika tersedia dan relevan.
2. Audit instruksi dan dependensi skill komunitas sebelum memasang.
3. Gunakan skill khusus untuk kebutuhan (scene, performance, Remotion render, testing); hindari puluhan skill yang tumpang tindih.
4. Utamakan instruksi internal `AGENTS.md` dan canon proyek untuk keputusan domain.
5. Tidak ada klaim 'skill sudah diinstal' sampai agent dan lingkungannya benar-benar diverifikasi.
