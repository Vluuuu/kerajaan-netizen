# Decision Log & Open Questions

Status:
- **DECIDED** = disepakati dalam percakapan brainstorming.
- **PROPOSED** = saran/kandidat; masih dapat berubah.
- **OPEN** = perlu keputusan berikutnya.
- Tanggal awal pengumpulan: 2026-11-08.

## Decided
| ID | Keputusan |
| --- | --- |
| D-001 | Proyek terpisah sepenuhnya dari Pulau Gobi. |
| D-002 | Satu dunia 3D permanen untuk website dan video Remotion. |
| D-003 | Joko adalah pencipta/pengamat, bukan raja; bisa muncul fisik sesekali. |
| D-004 | Alam sudah ada sejak awal, luas; belum ada manusia/peradaban. |
| D-005 | Dunia satu daratan luas, beberapa region tersambung; detail dikembangkan bertahap. |
| D-006 | Wilayah awal lembah luas di dekat sungai. |
| D-007 | Manusia pertama diwujudkan dari komentar terpilih. |
| D-008 | Komentar, **bukan voting**, menjadi mekanisme utama; Joko kurator/otoritas akhir. |
| D-009 | Komentar TikTok, YouTube, Instagram, Facebook dapat dipilih; awalnya manual. |
| D-010 | NPC mewakili netizen yang dipilih; memakai nama sesuai username; peran/pekerjaan ditetapkan Joko. |
| D-011 | Satu netizen teridentifikasi satu NPC; komentar berikutnya mengembangkan NPC yang ada, bukan duplikasi. |
| D-012 | Follower ditampilkan sebagai **Calon Warga Kerajaan**, bukan warga/NPC aktual. |
| D-013 | Raja pertama tidak muncul segera; penduduk dan kehidupan terbentuk lebih dulu. |
| D-014 | NPC punya kebutuhan, pekerjaan, relasi dasar, memori sederhana; belum usia/keluarga/kematian di MVP. |
| D-015 | NPC bebas melakukan rutinitas dan interaksi harian, tetapi keputusan besar dikendalikan Joko/aturan. |
| D-016 | Waktu hybrid: simulasi dapat berjalan terus, sinematik mempercepat presentasi tanpa mengubah canon. |
| D-017 | Pembangunan awal dilakukan Joko dengan animasi proses selesai dalam satu video. |
| D-018 | Intervensi besar resmi di website saat episode terbit; rutinitas NPC tetap berjalan. |
| D-019 | Website visi gabungan aerial dan walk mode; MVP aerial dahulu. |
| D-020 | Komentar bisa mengubah kehidupan NPC dan peristiwa kecil, bukan sekadar membangun. |
| D-021 | Visual sangat ringan/ultra-low-poly; NPC blocky sangat sederhana. |
| D-022 | Fondasi referensi 3D resmi **mrdoob/three.js**, dan skill AI Remotion resmi **remotion-dev/skills**; R3F belum diputuskan. |
| D-023 | Kombinasi kreatif pertumbuhan A + komedi B + drama NPC C; petualangan D belakangan. |
| D-024 | Nama brand/channel dipilih: **DUNIAJOKO.ID**. Nama repo `kerajaan-netizen` tetap; nama kerajaan dalam cerita belum diputuskan. |
| D-025 | Episode 1 dibuka dengan **Joko menyatakan ingin membangun kerajaan dari nol** dalam 3 detik awal; narasi santai, natural, sedikit kocak. |
| D-026 | Episode 1 berakhir dengan **follow + komentar** untuk berpeluang menjadi manusia pertama; tidak ada manusia atau raja pada episode tersebut. |
| D-027 | **Fokus produksi hanya Episode 1**; Episode 2 dan seterusnya tidak diplot lebih dahulu, tetapi ditentukan oleh komentar penonton nyata yang dikurasi Joko. |
| D-028 | **Satu castle/istana kosong sudah ada sejak awal Episode 1**, disiapkan Joko sebagai simbol kerajaan masa depan; belum ada manusia, raja, rumah, atau bangunan lain. |
| D-029 | Episode 1 memakai VO versi 1.2 untuk percobaan ElevenLabs dan **subtitle dinamis per-frasa/kata dengan highlight sesuai VO** seperti fungsi subtitle video referensi (tidak meniru identitasnya). |

## Approved direction added 2026-11-09 (pending reconciliation with newer local decision IDs)
- Setelah Episode 2 terbit, **tata ruang kerajaan harus terencana dan konsisten**: rumah, jalan, castle dan fasilitas masa depan tidak boleh ditempatkan secara acak.
- **Tiga rumah kanonis Episode 2 tetap menjadi Kampung Pelopor**; jangan memindahkan atau menghilangkannya diam-diam. Jika relokasi memang dibutuhkan, perlu keputusan pemilik dan peristiwa kanonis yang diceritakan.
- **Rincian zonasi dan implementasi belum disetujui**. Masterplan dipertimbangkan sebagai next improvement, bukan instruksi untuk coding sekarang. Lihat `docs/09-spatial-masterplan-backlog.md`.
- Sengaja tidak menerbitkan nomor D-030+ di branch dokumentasi ini: menurut laporan Claude Code, decision log lokal telah mencakup D-033; nomor harus direkonsiliasi saat integrasi branch untuk mencegah benturan.

## Proposed (bukan locked)
| ID | Usulan |
| --- | --- |
| P-001 | Persona Joko santai tapi berkuasa; dewa humanoid simple melayang. |
| P-002 | Palet Joko putih gading/emas lembut/cyan; masih membutuhkan visual approval. |
| P-003 | Calon raja diambil dari warga/NPC yang sudah punya cerita, bukan netizen baru mendadak. |
| P-004 | 1 hari simulasi setara 1 jam nyata; perlu diuji dan belum diputuskan. |
| P-005 | Utility AI + FSM untuk NPC; fixed tick bila cocok. |
| P-006 | Backend TypeScript + PostgreSQL; hanya kandidat. |
| P-007 | R3F untuk integrasi React/Remotion jika memberi keuntungan; tidak wajib. |
| P-008 | 5–8 NPC di MVP setelah warga mulai muncul, tidak semua dalam satu frame. |
| P-009 | Manual activation episode sampai sinkronisasi publikasi otomatis benar-benar dibutuhkan. |

## Open Questions — urut prioritas
1. Nama kerajaan dalam cerita, kemungkinan nama dunia, dan verifikasi ketersediaan/kepemilikan domain serta handle `DUNIAJOKO.ID`.
2. Visual bible Joko yang benar-benar disetujui (silhouette, warna, proporsi, rig).
3. Bentuk data identitas netizen: moderasi username, perubahan nama, platform duplicate, klaim akun, opt-out.
4. Ketentuan calon warga: sumber angka follower, penggabungan antar-platform, interval pembaruan, saat follower turun.
5. Kapan dan bagaimana raja pertama dipilih serta kekuasaannya.
6. Rasio waktu dan kebijakan offline/catch-up NPC.
7. Ukuran region aktif, perangkat target dan performance budget hasil benchmark.
8. Bentuk simulasi ekonomi awal dan daftar bangunan paling minimum.
9. Kontrak data simulasi/world state, versioning, snapshot, event activation.
10. Keputusan Three.js langsung vs React Three Fiber; integrasi 3D ke Remotion.
11. Pilihan backend/database dan hosting berdasarkan proof of concept.
12. Frekuensi episode dan titik resmi aktivasi (multi-platform tidak selalu publish serentak).
13. Sistem izin dan moderasi untuk pemakaian komentar/username di video publik.
14. Acceptance criteria dan risiko teknis yang perlu dites sebelum skala.

## Cara memperbarui
Catat perubahan keputusan dalam PR, sertakan alasan dan dampaknya; revisi dokumen canon/MVP/AGENTS.md yang terdampak. Jangan diam-diam mengubah status PROPOSED menjadi DECIDED.
