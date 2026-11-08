# Community, Comments & Episode Workflow

## Mekanisme utama: komentar, bukan voting
- Joko memilih komentar secara **manual** dari TikTok, YouTube, Instagram, dan Facebook.
- Komentar **tidak** otomatis dijalankan atau menjadi perintah langsung ke simulasi.
- Joko menetapkan hasil akhir: bangunan, fungsi, lokasi, pekerjaan pengusul, dan konsekuensi cerita.
- Komentar dapat mengusulkan pembangunan, penduduk, hewan, hadiah, perubahan kehidupan, konflik sosial ringan, dan humor.
- Saran destruktif/bencana/pergantian penguasa skala besar bukan prioritas fase awal.
- Tidak menjanjikan pemilihan komentar berdasarkan like tertinggi, voting, atau otomatisasi verifikasi follow.

## Calon warga vs warga resmi
- **Calon Warga Kerajaan:** indikator ukuran komunitas/follower (cara menggabungkan platform dan duplikasi belum final).
- **Warga Resmi:** akun yang dipilih untuk memiliki NPC kanonis, dengan stable ID dan username tampil.
- **NPC ditampilkan di video:** subset dari warga resmi yang relevan; bukan semua follower dan bukan harus semua NPC aktif dalam simulasi.
- Satu akun/netizen teridentifikasi hanya punya satu NPC. Komentar terpilih berulang mengubah kisah/atributnya, tidak menciptakan duplikat.

## Identitas & keamanan komunitas
- Simpan asal platform dan referensi komentar secara aman; jangan bergantung pada username sebagai identifier unik.
- Perhatikan izin publikasi, perubahan username, peniruan identitas, penghapusan komentar/akun, dan permintaan menghapus atribusi.
- Username dan komentar berpotensi mengandung konten yang tidak layak; perlu filter/moderasi dan fallback display sebelum dipakai di video atau scene 3D.
- Data yang tersimpan minimal; jangan menambahkan data sensitif atau melakukan scraping tanpa evaluasi aturan platform.
- Klaim jumlah follower sebaiknya jelas: metrik calon warga, bukan total orang unik yang telah diverifikasi.

## Dua jalur perubahan dunia
**A. Peristiwa rutin simulasi:** kebutuhan, pekerjaan, gerakan, relasi sosial; terus berkembang sesuai aturan simulation clock.

**B. Intervensi Joko / episode:** komentar dikurasi, perubahan besar direncanakan untuk snapshot dan video, lalu **diaktifkan di world state kanonis saat episode terbit**.

## Pipeline video yang ditargetkan
1. Joko memilih komentar + mencatat asalnya.
2. Menyusun daftar perubahan dunia (entitas ditambahkan/diperbarui, peran baru, lokasi, konsekuensi).
3. Membuat versi snapshot dunia untuk episode; perubahan besar masih pending dan tidak bocor ke website live.
4. Menulis beat cerita, shot list, kamera, VO, acting, subtitle, sound effects.
5. Animasi pembangunan oleh Joko terjadi tuntas **dalam video yang sama** (timelapse/perakitan visual).
6. Render video melalui Remotion dari snapshot versi terkunci, target **1080x1920 30 FPS**.
7. Setelah video diterbitkan, kreator mengaktifkan event perubahan kanonis melalui alur publikasi terkontrol; catat waktu dan referensi episode.
8. Website memuat keadaan terkini; peristiwa rutin NPC terus berlanjut.

**Penting:** Publikasi lintas platform tidak serentak secara alami. Untuk MVP, perubahan bisa diaktifkan **manual** dengan satu titik publikasi resmi yang ditentukan kreator, bukan mengandalkan webhook posting yang belum tersedia. Status 'terbit' tidak otomatis membuktikan perubahan sudah diterapkan; verifikasi terpisah.

## Episode 1 — blueprint kreatif disetujui
- Naskah VO, hook kerajaan dari nol, arah shot, CTA komentar, dan status dunia tersimpan di [Episode 1 Blueprint](episodes/episode-01-blueprint.md).
- Episode 1 sudah **disetujui secara kreatif**, tetapi **belum diproduksi/dirender/diterbitkan**. Rencana durasi 30–40 detik dan timing per shot masih bisa disesuaikan ketika preview VO.

## Episode berikutnya — sketsa, bukan skrip final
- Episode 1: panorama alam luas tanpa manusia, Joko memperkenalkan dunia, mengundang komentar untuk calon manusia pertama.
- Episode 2: salah satu komentar terpilih; NPC pertama muncul dan mulai hidup.
- Selanjutnya: komentar membentuk fasilitas dan warga baru, memunculkan dinamika sederhana.
- Raja **belum hadir pada awal**; muncul setelah warga dan kehidupan mereka cukup berkembang.

## Konsistensi
- Video tidak punya database 'dunia video' yang terpisah.
- Snapshot+event history harus menjelaskan kondisi world canon saat suatu episode dibuat.
- Pencahayaan, kamera, pose, dan montage boleh sinematik; identitas, bangunan, peristiwa besar, hasil pilihan dan kronologi harus konsisten.
- Video lama harus dapat dirender ulang dari versi data/aset/komposisi yang dikunci, sejauh dependensi dan tooling masih tersedia.
