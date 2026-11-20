# Usulan amandemen protokol

Status: usulan, belum disetujui tim. Bila protokol belum terdaftar di PROSPERO, ini perubahan, bukan deviasi. Tiap perubahan yang disetujui dicatat dengan tanggal.

Dasar: pencarian pilot PubMed 2026-11-20 (`../pencarian/log-pencarian.md`).

## A1. Database: Embase dan CENTRAL tidak tersedia

Keadaan: tim hanya punya PubMed dan Scopus.

Usulan: ganti "PubMed, Embase, Scopus, Cochrane CENTRAL" menjadi "PubMed dan Scopus", dengan ClinicalTrials.gov, Chinese Clinical Trial Registry, dan penelusuran daftar pustaka tetap. Ketiadaan Embase dan CENTRAL dinyatakan sebagai keterbatasan. Butir 4 AMSTAR 2 masih bisa dipenuhi (dua database, string lengkap, registry, daftar pustaka, pencarian diulang), tetapi risiko studi terlewat naik.

Perubahan ikutan di protokol:
- Langkah berikutnya: "pencarian pilot di Embase" diganti "pencarian pilot di PubMed dan Scopus".
- Tingkat keyakinan "sedang": kondisi naik ke tinggi (konfirmasi minimal 6 studi) dinilai ulang dengan PubMed dan Scopus. S1 sudah memberi sedikitnya 6 studi cGVHD-spesifik di PubMed.

Opsional untuk didiskusikan: cek apakah kampus punya akses ke Embase atau CENTRAL, atau apakah Cochrane Library dan Europe PMC bisa ditelusuri gratis dengan ekspor yang memadai. Belum diverifikasi oleh asisten.

## A2. Buang blok 3 (refrakter) dari string pencarian

Bukti: Chen 2019 (PMID 31668569) tidak muncul di S1 tetapi muncul di S0. Empat studi lain ikut hilang (Shen 2022, Zhou 2010, Savaş 2026, Ringdén 2011). Studi BOS dan studi dengan istilah lain ("multidrug-resistant") jarang memakai kata "refractory" di judul atau abstrak.

Usulan: cari populasi dan intervensi saja, lalu tegakkan "refrakter atau bergantung steroid" pada tahap penyaringan, memakai definisi PICOS yang sudah ada.

Biaya: lebih banyak abstrak. S3 (tanpa blok 3) memberi 207 hit PubMed, lalu ditambah Scopus sebelum dedup. Perkiraan beban "60 sampai 80 abstrak" perlu direvisi. Dengan 7 anggota dan dua penelaah per rekaman, beban ini masih wajar.

## A3. Perketat blok 2 (manifestasi organ)

Bukti: S0 (340 hit) berisi noise dari istilah organ yang berdiri sendiri (dry eye non-GVHD, plantar fasciitis, Stevens-Johnson, model hewan).

Usulan: istilah inti cGVHD tetap berdiri sendiri; istilah organ hanya dihitung bila muncul bersama istilah GVHD atau transplantasi (blok ANCHOR di log). String S3 dengan perubahan ini: 207 hit, dan semua kandidat yang diperiksa tertangkap kecuali Zhang 2025 (40269970), yang perlu dibuka untuk dinilai.

Syarat: protokol menyebut penghapusan blok organ sebagai penyimpangan. Karena blok organ tetap ada hanya dengan syarat tambahan, tuliskan pengetatan ini secara eksplisit di naskah.

## A4. Tabel kandidat: nama penulis tidak cocok dengan PubMed

Protokol sendiri menyatakan nama penulis belum diverifikasi. Pencocokan di bawah hanya berdasarkan jurnal, tahun, dan topik. Abstrak belum dibuka.

| Protokol | Temuan PubMed | Catatan |
|---|---|---|
| Chen 2019 EBioMedicine | Chen S, 31668569 | cocok; hilang di blok 3 |
| Kim 2024 Int J Mol Sci | Kim N, 38928436 | cocok |
| Boberg 2022 SCTM | Macías-Sánchez 2022 SCTM, 35348788 | penulis beda; Boberg 2020 SCTM fase II cGVHD (32573983) tidak ada di tabel protokol |
| Chen 2023 SCRT | Mohseni R 2023 SCRT, 37726865 | penulis beda |
| Weng 2012 Mol Ther | Weng J, 23070118 | cocok |
| Ringden 2022 Ther Adv Hematol | Shen MZ 2022 Ther Adv Hematol, 35096361 | penulis beda; hilang di blok 3 |
| Hoog 2024 Front Pediatr | Pérez-Torres Lobato 2024 Front Pediatr, 38783918 | penulis beda |
| Baysal 2026 J Clin Med | Savaş EM 2026 J Clin Med, 42881871 | penulis beda; hilang di blok 3 |
| Blokhin 2026 | tidak ditemukan di PubMed | sesuai protokol (tidak terindeks) |

Usulan: ganti nama di tabel protokol dengan PMID setelah diverifikasi, atau tulis "kandidat, penulis dikonfirmasi saat penyaringan".

## A5. Penelaah independen

Protokol meminta dua penelaah independen. Dengan tim 7 orang, usulan: bentuk pasangan dari anggota tim. Asisten menyiapkan bahan (daftar rekaman, formulir, draf ekstraksi) tetapi tidak menjadi penelaah formal, sehingga tidak ada penyimpangan dari butir proses dua penelaah.
