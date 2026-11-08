# DUNIAJOKO.ID — Episode 1: Membangun Kerajaan dari Nol

> **Status: Episode 1 creative plan approved; VO copy locked for first ElevenLabs take.** Belum direkam, diproduksi, dirender, atau diterbitkan. Versi v1.2, 2026-11-08. Timing masih menunggu audio asli.

## Fokus episode
Dalam hook pertama, Joko mengumumkan akan membangun **kerajaan dari nol**. Dunia sudah memiliki **satu castle/istana kosong** sebagai simbol awal arah pembangunan; alam luas sudah ada tetapi **manusia, raja, warga, desa dan peradaban belum ada**. Jangan menggambarkan Joko sebagai raja: ia adalah pencipta/pengamat dunia. Episode pertama berakhir dengan ajakan **follow + komentar** untuk berpeluang menjadi **manusia pertama**.

## Naskah VO — versi 1.2 (siap dicoba di ElevenLabs)

> Gue Joko, dan gue lagi bangun kerajaan dari nol.
>
> Castlenya udah ada.
>
> Dunianya juga udah siap. Ada sungai, hutan, gunung, semuanya luas banget.
>
> Tapi masalahnya... belum ada satu manusia pun di sini.
>
> Jadi sekarang gue butuh kalian buat ngisi dunia ini.
>
> Komentar yang gue pilih, bakal gue wujudin langsung di kerajaan ini.
>
> Mau jadi manusia pertama?
>
> Follow dulu biar jadi calon warga kerajaan, terus komen di bawah.
>
> Nanti gue pilih satu orang!

**Cara baca:** santai, natural, antusias secukupnya, sedikit kocak; jeda komedi setelah “Tapi masalahnya...”; CTA jelas tetapi tidak teriak. Jangan memaksa audio cocok dengan timing storyboard; desain timing setelah VO asli tersedia.

## Shot list (urutan disepakati, durasi belum dikunci)
1. **Hook / aerial reveal** — kamera terbang di atas lembah memperlihatkan **castle tunggal** di tengah dunia luas. Overlay pendek **MEMBANGUN KERAJAAN DARI NOL**, bukan layar teks panjang.
2. **Castle reveal** — close-medium shot sederhana pada castle kosong. VO “Castlenya udah ada.” Jangan menampilkan raja, penjaga, atau manusia di castle.
3. **Panorama alam** — kamera menyusuri sungai/hutan/pegunungan; bentuk dunia sangat sederhana, view distance tampak luas dengan aset jauh low-detail.
4. **Masalah / komedi** — kamera menyorot halaman castle atau dataran kosong, berhenti sesaat. Teks ekspresif **PENDUDUK: 0** dan SFX jeda ringan boleh dipakai.
5. **Premis komentar** — kamera orbit perlahan di castle dan dataran sekelilingnya. Jangan menampilkan komentar nyata/fiktif seolah sudah terpilih; bila ingin overlay, pakai callout generik tanpa username/engagement palsu.
6. **CTA** — kamera mendekat ke dataran kosong. Teks **MAU JADI MANUSIA PERTAMA?** lalu **FOLLOW + KOMEN**. Frame akhir tetap tanpa NPC.

## Subtitle dinamis mengikuti VO
Mengacu pada **pacing dan fungsi subtitle** video referensi pengguna, **bukan meniru layout/branding atau asetnya secara identik**.

- Jangan menampilkan kalimat penuh statis. Pecah subtitle menjadi **potongan frasa pendek** sesuai ucapan.
- **Kata yang sedang diucapkan** diberi highlight per-kata atau per-frasa (bukan semua kata secara bersamaan).
- Saat VO mengucap “kerajaan”, “dari nol”, “castle”, “manusia pertama”, “follow”, “komen” bisa ada pop/scale ringan secara selektif.
- Teks ekspresif **PENDUDUK: 0** hanya saat shot kosong. Jangan menabrak subtitle utama.
- Tempatkan subtitle di safe area vertikal, dengan ruang bagi UI Shorts/TikTok/Reels.
- **Timestamp/kata-per-kata belum ditetapkan** sampai audio ElevenLabs diterima. Timing otomatis perlu dikoreksi manual pada bagian yang sulit.

Contoh fragmentasi (bukan timestamps final):
- “Gue Joko” → “gue lagi bangun” → “kerajaan” → “dari nol”
- “Castlenya” → “udah ada”
- “Tapi masalahnya...” → “belum ada” → “satu manusia pun”
- “Follow dulu” → “calon warga kerajaan” → “komen di bawah”

## World state kanonis pada akhir Episode 1
- **Castle/istana: 1 (sudah ada sejak awal, kosong, dibuat Joko).**
- **Bangunan lain: 0.**
- **Warga resmi: 0; NPC manusia: 0; raja: 0.**
- Alam: lembah luas dekat sungai, pepohonan/hutan, pegunungan; jangan membuat wilayah terlalu berat hanya untuk video.
- **Calon Warga Kerajaan** mengikuti follower/community metric jika benar-benar tersedia, **bukan NPC/warga aktual**.
- Tidak ada nama, profesi, atau identitas manusia pertama sebelum Joko memilih komentar nyata.
- Kehadiran fisik Joko **tidak wajib** pada Episode 1; VO dan kamera pengamat sudah memadai.

## Target teknis setelah diizinkan implementasi
- Video vertikal **1080×1920, 30 FPS**.
- Render lanskap/castle melalui **Three.js resmi** (mrdoob/three.js) dan komposisi video **Remotion** dengan skill resmi.
- Ultra-low-poly, geometri sederhana, material reusable, pencahayaan ringan, tanpa fisika atau karakter NPC di Episode 1.
- Gunakan definisi aset dan world state kanonis yang dapat dipakai ulang website; tidak membuat world-state terpisah untuk video.
- Animasi castle **tidak perlu dirakit** pada Episode 1 karena secara cerita sudah ada. Pembangunan Joko dari komentar pada masa depan dapat memiliki animasi proses sesuai kebijakan proyek.

## Review gate
- [x] Kerajaan disebut dari detik pertama secara naratif.
- [x] Castle sudah ada tetapi belum dihuni dan tidak memiliki raja.
- [x] Dunia alami luas, ultra-low-poly, ringan.
- [x] Tidak ada manusia pada episode ini.
- [x] Naskah mengajak follow sebagai **calon warga** dan komen untuk berpeluang dipilih.
- [x] Subtitle per-frasa/per-kata menyorot kata sesuai VO, merujuk feel video contoh.
- [ ] Rekam/generate VO ElevenLabs, dengar dan perbaiki intonasi/durasi jika diperlukan.
- [ ] Tetapkan timestamp subtitle dari audio asli.
- [ ] Build/preview, cek ritme kamera, safe area, kesesuaian VO, SFX, dan performa.
- [ ] Render dan QA audio-video final.

## Batas kreatif
**Hanya Episode 1 yang direncanakan.** Plot dan entitas Episode 2+ hanya ditetapkan setelah ada komentar nyata dan pilihan Joko. Tidak ada skrip episode berikutnya, voting, atau klaim bahwa komentar tertentu sudah dipilih.