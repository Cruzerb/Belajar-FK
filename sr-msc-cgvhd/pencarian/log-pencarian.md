# Log pencarian

## Pilot PubMed, 2026-11-20

Metode: NCBI E-utilities `esearch` (db=pubmed), tanpa batas tahun dan bahasa. Tool PubMed di sesi asisten membatasi 20 operator boolean per query, sedangkan string protokol punya 29, jadi string dijalankan lewat E-utilities. Jumlah hit adalah hitungan pada tanggal ini.

Blok dipakai ulang di semua string:

```
B1 = "mesenchymal stem cell*"[tiab] OR "mesenchymal stromal cell*"[tiab] OR MSC[tiab] OR MSCs[tiab] OR "multipotent stromal cell*"[tiab] OR "Wharton jelly"[tiab] OR "umbilical cord derived stromal cell*"[tiab]

B2 = "chronic graft-versus-host disease"[tiab] OR "chronic graft versus host disease"[tiab] OR "chronic GVHD"[tiab] OR cGVHD[tiab] OR "bronchiolitis obliterans"[tiab] OR sclerodermatous[tiab] OR "sclerotic GVHD"[tiab] OR "dry eye"[tiab] OR keratoconjunctivitis[tiab] OR "lichen planus"[tiab] OR fasciitis[tiab] OR "vaginal stenosis"[tiab] OR "oral GVHD"[tiab] OR "hepatic GVHD"[tiab]

B3 = "steroid-refractory"[tiab] OR "steroid refractory"[tiab] OR "steroid-resistant"[tiab] OR "steroid-dependent"[tiab] OR "corticosteroid refractory"[tiab] OR refractory[tiab] OR salvage[tiab] OR "second-line"[tiab] OR "third-line"[tiab]

CORE   = "chronic graft-versus-host disease"[tiab] OR "chronic graft versus host disease"[tiab] OR "chronic GVHD"[tiab] OR cGVHD[tiab]
ORGAN  = "bronchiolitis obliterans"[tiab] OR sclerodermatous[tiab] OR "sclerotic GVHD"[tiab] OR "dry eye"[tiab] OR keratoconjunctivitis[tiab] OR "lichen planus"[tiab] OR fasciitis[tiab] OR "vaginal stenosis"[tiab] OR "oral GVHD"[tiab] OR "hepatic GVHD"[tiab]
ANCHOR = GVHD[tiab] OR "graft-versus-host"[tiab] OR "graft versus host"[tiab] OR "hematopoietic stem cell transplant*"[tiab] OR "haematopoietic stem cell transplant*"[tiab] OR HSCT[tiab] OR allogeneic[tiab] OR "bone marrow transplant*"[tiab]
```

| Kode | String | Hit |
|---|---|---|
| S1 | (B1) AND (B2) AND (B3), literal protokol | 81 |
| S0 | (B1) AND (B2), tanpa blok 3 | 340 |
| S2 | S1 dengan tambahan MeSH "Mesenchymal Stem Cells", "Mesenchymal Stem Cell Transplantation", "Graft vs Host Disease" | 244 |
| S3 | (B1) AND ((CORE) OR ((ORGAN) AND (ANCHOR))), usulan | 207 |
| S4 | (MSC terms) AND ("bronchiolitis obliterans" OR "bronchiolitis obliterans syndrome"), tanpa blok 3 | 30 |

S4 dijalankan lewat tool PubMed, sisanya lewat E-utilities. Daftar rekaman S0 dengan penanda keanggotaan S1 dan S3: `pubmed-pilot-2026-11-20.csv`.

## Temuan

1. Perkiraan beban protokol (60 sampai 80 abstrak) cocok dengan S1 (81 hit PubMed saja, belum termasuk Scopus).
2. Chen 2019 (PMID 31668569), yang protokol sebut "kandidat utama", ada di S0 tetapi tidak di S1. Penyebabnya blok 3, bukan blok 2. String literal protokol tidak menangkap studi jangkarnya sendiri.
3. Studi lain yang ikut hilang di blok 3: Shen 2022 Ther Adv Hematol (35096361, "multidrug-resistant"), Zhou 2010 BBMT (19925878, sclerodermatous), Savaş 2026 J Clin Med (42881871, BOS), Ringdén 2011 BMT (21307841).
4. S3 menahan keempatnya dan semua kandidat lain yang diperiksa, kecuali Zhang 2025 SCRT (40269970, UC-MSC eye drops) yang tidak lolos blok anchor. Perlu dibuka abstraknya untuk tahu apakah itu GVHD.
5. S0 berisi noise berat (dry eye non-GVHD, plantar fasciitis, Stevens-Johnson, hewan). Alasan blok organ perlu dikaitkan dengan istilah GVHD atau transplantasi.

## Kandidat awal dari hasil pilot (belum disaring, abstrak belum dibuka)

Ditambahkan dari S1 dan di luar tabel kandidat protokol: Boberg 2020 SCTM fase II cGVHD (32573983), Weng 2010 BMT (20818445), Peng 2015 Leukemia (25034146), Jurado 2017 Cytotherapy (28662983), Zhou 2010 BBMT (19925878), Li 2024 BGER (36856529), Stenger 2022 Front Immunol (36189324), Yi 2016 (26807024), Erbey 2016 (26783400), Krasowska-Kwiecien 2019 (30979480), Zhang 2025 SCRT (40269970). Banyak yang era sebelum 2020 kemungkinan sudah ada di Morata-Tarifa 2020; pemetaannya dilakukan saat penyaringan.

## Belum dikerjakan

- Scopus (butuh ekspor tim), ClinicalTrials.gov, Chinese Clinical Trial Registry, PROSPERO, OSF, INPLASY.
- Verifikasi DOI dan abstrak untuk kecocokan nama penulis (lihat amandemen A4).
