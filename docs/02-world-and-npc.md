# World & NPC — Working Design

## Dunia: luas secara geografis, ringan saat dijalankan
- Bentuk: satu daratan luas berkelanjutan yang dapat diorganisasi ke beberapa region; **bukan pulau kecil**.
- Region pertama: **lembah datar luas dekat sungai**, tanah hijau, pohon seperlunya, hutan dan perbukitan/pegunungan di kejauhan.
- Episode 1: tidak ada manusia, bangunan, atau peradaban.
- Region lain boleh dirancang skematis, tetapi **tidak perlu full-detail, tidak perlu simulasi NPC aktif** sebelum dibutuhkan.
- Dunia tidak boleh di-reset hanya karena video/fitur baru; ekspansi harus mempertahankan koordinat dan identitas objek lama.

## Batas visual awal
- Ultra-low-poly: geometri murah, material sederhana, warna terbatas, model reusable.
- Tanah sederhana, bukan grass blades massal. Pohon berulang dapat memakai instancing. Sungai memakai pendekatan visual ringan, bukan fisika air.
- Pegunungan jauh hanya latar sederhana. Hindari efek post-processing, bayangan kompleks, cloth/physics, dan shader mahal sebelum profiling membuktikan perlu.
- Kamera website visi akhir: **mode pengamat aerial + mode berjalan**; **MVP hanya mode pengamat pan/rotate/zoom/klik objek**.
- Optimasi berdasarkan pengukuran perangkat mobile nyata, bukan asumsi angka FPS/draw calls yang belum diukur.

## Model identitas NPC — konseptual, bukan skema database final
- Stable internal NPC ID.
- Platform asal + ID akun platform yang tersedia/terverifikasi + username display. **Username bukan primary key**: dapat berubah/tidak unik lintas platform.
- Status warga resmi, pekerjaan/peran awal ditetapkan Joko, rumah/lokasi jika sudah ada.
- Kebutuhan dasar (lapar/energi), kegiatan saat ini, tujuan, status interaksi/relasi sosial sederhana.
- Riwayat kejadian relevan dan timestamp dunia; hubungan antarkarakter.
- Satu netizen teridentifikasi = satu NPC. Jika komentar terpilih kembali, perbarui karakter yang sama, jangan buat duplikat.
- Akun dua platform **tidak otomatis** dianggap orang sama; penggabungan identitas memerlukan verifikasi dan aturan jelas.

## Kebebasan NPC
- Joko menetapkan **pekerjaan atau peran awal**.
- NPC memilih kegiatan harian secara kontekstual: bekerja, makan, tidur, istirahat, bersosialisasi, membantu, protes atau berkonflik ringan.
- Tidak bebas menetapkan sendiri perubahan jabatan, aturan negara, atau kepemilikan aset besar.
- Sistem usia, pernikahan, keturunan dan kematian: **di luar MVP**, evaluasi nanti karena identitas NPC permanen milik netizen.

## Perilaku — rekomendasi teknis untuk dievaluasi
- Kandidat **Utility AI** untuk prioritas kebutuhan + **FSM** untuk mengeksekusi aktivitas.
- Behavior Tree/GOAP dan generative LLM bukan prasyarat awal.
- Simulasi **independen dari frame-rate renderer**, berinput world state + simulation clock + konfigurasi yang terversi.
- Nav/pathfinding harus dapat mendeteksi tujuan tak terjangkau; fallback ke posisi aman/tugas lain setelah batas percobaan.
- Reservasi resource untuk mencegah dua NPC memakai item/slot secara tidak konsisten.
- Hysteresis/cooldown untuk mencegah NPC bolak-balik ganti keputusan; timeout aktivitas, stuck detection, recovery.
- Animasi visual merepresentasikan state simulasi, bukan menjadi sumber kebenaran state.

## Waktu dunia
- Model **hybrid disepakati**: waktu simulasi berjalan dan bisa dipercepat terukur, video dapat membuat montase dari snapshot tanpa mengubah riwayat.
- Contoh rasio 1 hari dunia = 1 jam nyata adalah **usulan**, bukan keputusan.
- Perlu batasan sim tick, saat offline, catch-up, penyimpanan status pekerjaan, dan cara merekonstruksi aktivitas.

## MVP behavioral slice (usulan)
- 1 area kecil yang dapat dijelajahi kamera meskipun dunia terlihat luas.
- 1–8 NPC setelah komentar terpilih; **Episode 1 tetap tanpa NPC**.
- Dua kebutuhan (lapar dan energi); setidaknya dua perilaku selain idle.
- Satu resource sederhana, satu interaksi sosial ringan, satu kasus gagal path yang pulih.
- Persistensi dapat diverifikasi setelah reload/restart sebelum skala bertambah.
