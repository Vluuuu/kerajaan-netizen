# DUNIAJOKO.ID — Kerajaan Netizen (Project Codename)

> **Status:** dokumentasi & brainstorming — belum ada implementasi aplikasi, database, simulasi, atau rendering produksi.
>
> **Brand/channel dipilih:** **DUNIAJOKO.ID**. Ini penetapan nama kreatif; belum berarti domain `duniajoko.id` telah dibeli atau diverifikasi tersedia. **Kerajaan Netizen** tetap nama kerja repository/proyek teknis. Nama kerajaan pertama di dalam dunia masih belum ditentukan.

**Visi:** satu dunia fantasi kerajaan 3D permanen yang berkembang dari **komentar penonton terpilih**, dapat dikunjungi melalui website, dan menjadi sumber kanonis untuk video sinematik dengan Remotion. Joko berperan sebagai pencipta/pengamat dunia, **bukan raja**. Raja pertama baru akan diangkat kemudian dari netizen.

## Prinsip inti

- Dunia berawal dengan alam yang **luas** (wilayah utama lembah dekat sungai) dan **satu castle kosong yang sudah disiapkan Joko**, tetapi **tanpa manusia, raja, permukiman, atau kehidupan kerajaan**.
- Manusia pertama dipilih dari **komentar netizen**. Komentar bisa berasal dari TikTok, YouTube, Instagram, atau Facebook; Joko melakukan kurasi, **bukan voting**.
- Netizen terpilih menjadi NPC permanen dengan **nama sesuai username**, identitas unik per platform/akun, dan pekerjaan/peran ditetapkan Joko. Satu identitas netizen terverifikasi = satu NPC; komentar berikutnya mengembangkan karakter yang sama.
- Jumlah follower ditampilkan sebagai **Calon Warga Kerajaan**, bukan populasi NPC aktual atau jumlah warga resmi.
- NPC melakukan aktivitas mandiri (kebutuhan, pekerjaan, relasi sosial ringan) tetapi keputusan besar tetap di tangan Joko/aturan dunia.
- Pembangunan awal diwujudkan Joko melalui **animasi pembentukan dalam satu video**, bukan proses konstruksi dunia nyata berhari-hari.
- Perubahan besar menjadi **resmi di website pada saat episode dipublikasikan**; aktivitas NPC rutin terus berlangsung.
- Visual sangat ringan: **ultra-low-poly** dan reusable. Dunia geografis luas, tetapi area detail/simulasi aktif dikembangkan bertahap.
- Dunia interaktif dan video memakai **satu sumber data kanonis**, bukan dua world state independen.
- Proyek ini **terpisah dari Pulau Gobi**: aset, karakter, lore, repo, dan data tidak dicampur.

## Dokumentasi

| Dokumen | Isi |
| --- | --- |
| [Vision & creative canon](docs/01-vision-and-canon.md) | Keputusan dunia, Joko, netizen, dan batasan kreatif |
| [World & NPC design](docs/02-world-and-npc.md) | Region, kamera, NPC, perilaku, performa awal |
| [Kingdom masterplan backlog](docs/09-spatial-masterplan-backlog.md) | Tata ruang kerajaan, Kampung Pelopor, aturan placement, zonasi, QA, dan tahapan peningkatan ke depan |
| [Community & episodes](docs/03-community-and-episodes.md) | Komentar lintas platform, warga, produksi video, publikasi |
| [Episode 1 creative blueprint](docs/episodes/episode-01-blueprint.md) | Naskah VO v1.2 untuk ElevenLabs, castle awal, storyboard, subtitle dinamis, CTA follow + komen |
| [Architecture proposal](docs/04-architecture-proposal.md) | Batas subsistem dan alur data **usulan, belum final** |
| [Engineering quality standards](docs/05-engineering-standards.md) | Kriteria mutu disesuaikan skala proyek |
| [MVP & roadmap](docs/06-mvp-roadmap.md) | Milestone bertahap dan acceptance criteria |
| [Decision log](docs/07-decisions.md) | Disepakati vs belum diputuskan |
| [Agent guidelines](AGENTS.md) | Aturan kerja AI coding agents sebelum & saat implementasi |
| [References](docs/08-references.md) | Dokumentasi dan repo resmi |

## Tahap saat ini

**Proyek sudah dalam fase implementasi lokal menurut laporan pemilik:** Episode 1 dan 2 telah dipublikasikan, viewer 3D MVP dan render pipeline sedang dikembangkan. Detail kode terbaru bisa berada di branch/working tree lokal yang belum masuk GitHub; cek keadaan repository sebelum memodifikasi. **Website belum disetujui untuk deploy publik.** Improvement masterplan yang dicatat adalah backlog, belum izin implementasi.

Referensi teknis utama yang diprioritaskan:
- Three.js resmi: https://github.com/mrdoob/three.js
- Remotion Agent Skills resmi: https://github.com/remotion-dev/skills

Keputusan dalam dokumen dibedakan antara **disepakati**, **usulan**, dan **belum diputuskan**; usulan bukan mandat implementasi.
