# Kandidat Case Report untuk EBCR

Tanggal penelusuran: 12 November 2026. Topik dibiarkan kosong pada permintaan, jadi saya perlakukan sebagai bebas dan mengutamakan kondisi yang relevan untuk dokter umum di Indonesia (infeksi tropis, keracunan, anak). Rentang terbit 2020–2026.

Hasil: **4 kandidat yang lolos**, bukan 5. Satu kandidat kelima (typhoid XDR) gugur karena data kasus dan bukti pembanding terlalu tipis; alasannya ada di bagian "Kandidat yang gugur".

## Cara kerja

### String pencarian case report (Europe PMC REST API)

Filter dasar yang ditempelkan ke semua query:

```
AND PUB_TYPE:"Case Reports" AND OPEN_ACCESS:Y AND PUB_YEAR:[2020 TO 2026]
```

Query topik yang dipakai (hit kasar dalam kurung):

```
"scrub typhus" AND pregnan*                                                     (61)
leptospirosis AND ("pulmonary hemorrhage" OR "pulmonary haemorrhage")
  AND (corticosteroid* OR methylprednisolone OR "plasma exchange")              (54)
leptospirosis AND (corticosteroid* OR methylprednisolone)
  AND ("controversial" OR "no consensus" OR "further studies")                  (53)
"Stevens-Johnson" AND (cyclosporine OR ciclosporin OR etanercept) AND "no consensus"   (44)
melioidosis AND (child* OR pediatric) AND "optimal duration"                    (1)
typhoid AND ("extensively drug-resistant" OR XDR) AND (azithromycin OR meropenem)      (28)
("Bell palsy" OR "Bell's palsy" OR "facial palsy") AND (child* OR pediatric OR paediatric)
  AND (prednisolone OR corticosteroid*)                                         (261)
paraquat AND (cyclophosphamide OR methylprednisolone OR immunosuppress*)        (52)
tetanus AND (intrathecal OR "magnesium sulfate" OR "magnesium sulphate")        (63)
methanol AND poisoning AND (fomepizole OR ethanol) AND (hemodialysis OR haemodialysis) (58)
dengue AND pregnan* AND ("optimal" OR "no consensus" OR "unclear")              (77)
"scrub typhus" AND (azithromycin AND doxycycline) AND (child* OR pregnan*)      (70)
snakebite AND antivenom AND ("optimal dose" OR "no consensus" OR "dose remains")       (10)
neurocysticercosis AND albendazole AND praziquantel
  AND ("no consensus" OR "unclear" OR "controversial")                          (30)
"Kawasaki disease" AND ("IVIG-resistant" OR "IVIG resistant" OR refractory)
  AND (infliximab OR cyclosporine)                                              (101)
```

Dari hasil itu, 20 full text saya unduh dan baca lewat endpoint `fullTextXML` Europe PMC. Saya tidak menilai dari abstrak.

### Pencarian literatur awal (PubMed E-utilities)

Strategi tiap kandidat saya tulis lebih dulu ke file, baru dijalankan. Jumlah per desain diperoleh dengan menambahkan filter berikut ke string utama:

| Label | Filter tambahan |
|---|---|
| RCT | `AND "Randomized Controlled Trial"[pt]` |
| SR/MA | `AND (systematic[sb] OR "Meta-Analysis"[pt])` |
| Observasional | `AND ("Cohort Studies"[MeSH] OR "Case-Control Studies"[MeSH] OR cohort[tiab] OR retrospective[tiab] OR "case-control"[tiab] OR propensity[tiab])` |
| Case report | `AND "Case Reports"[pt]` |

Angka ini kasar. Filter observasional cukup longgar, dan judul RCT/SR baru saya saring sekilas, belum disaring penuh. Case report asal tidak dihitung sebagai bukti.


## Kandidat 1 (paling layak): Kortikosteroid pada leptospirosis berat (Weil's disease)

**Sitasi.** Şahin AM, Atçı-Koç İ, Çetin S. Weil's disease: rapid recovery following corticosteroid treatment: a case report. Rev Inst Med Trop Sao Paulo. 2026;68:e35.
DOI: 10.1590/s1678-9946202668035. PMID: 42154849. PMCID: PMC13183348.
Tautan: https://pmc.ncbi.nlm.nih.gov/articles/PMC13183348/
Status akses: open access (CC BY), full text sudah saya baca.

**Ringkasan kasus.** Laki-laki 41 tahun, tukang kayu, memancing di sungai seminggu sebelumnya, riwayat penasun dan konsumsi alkohol. Datang dengan diare, muntah, mialgia, ikterus, dan oliguria; TD 110/60, nadi 130, suhu 37,8 °C; trombosit 37.000, bilirubin total 11,3 mg/dL, kreatinin 5,5 mg/dL, CRP 327. MAT awal negatif, MAT ulang hari ke-7 positif serovar Pomona (titer 800). Ia mendapat ceftriaxone 7 hari, hemodialisis 3 kali, dan transfusi trombosit. Bilirubin tetap naik sampai 23 mg/dL dan trombosit tetap rendah, lalu pada hari ke-18 diberikan metilprednisolon 1 mg/kg/hari selama 5 hari. Bilirubin turun ke 3,2 dan trombosit naik ke 291.000. Pasien pulang hari ke-23 dan pulih penuh pada kontrol hari ke-29. Tabel laboratorium serial tersedia lengkap.

**Titik ketidakpastian.**
- Abstrak: "The role of adjunctive corticosteroid therapy in severe leptospirosis remains controversial."
- Introduction: "there is currently no clear consensus regarding the efficacy and safety of corticosteroid therapy".
- Discussion: penulis mengutip temuan yang saling bertentangan (studi Sri Lanka positif, satu studi lain tidak efektif dan menaikkan risiko infeksi nosokomial, meta-analisis tanpa bukti jelas).
- Conclusion: "controlled clinical trials are needed to clarify the efficacy and safety of this approach."

**Jenis pertanyaan:** terapi.

**Clinical question.** Pada pasien dewasa dengan leptospirosis berat (sindrom Weil) yang tetap memburuk meski sudah mendapat antibiotik dan terapi suportif, apakah penambahan kortikosteroid sistemik dibanding terapi standar saja menurunkan mortalitas dan mempercepat pemulihan organ?

**PICO**

| Unsur | Isi |
|---|---|
| P | Dewasa dengan leptospirosis berat (ikterus berat, AKI yang perlu dialisis, trombositopenia berat) yang tidak membaik dengan antibiotik dan terapi suportif |
| I | Kortikosteroid sistemik adjuvan (metilprednisolon IV) |
| C | Terapi standar saja (antibiotik + suportif) atau plasebo |
| O | Mortalitas; pemulihan fungsi ginjal atau lepas dialisis; lama rawat; normalisasi bilirubin dan trombosit; efek samping (infeksi nosokomial, perdarahan saluran cerna) |

**Pencarian awal (PubMed)**

```
(leptospirosis[MeSH] OR leptospiros*[tiab] OR "Weil disease"[tiab] OR "Weil's disease"[tiab])
AND (corticosteroid*[tiab] OR glucocorticoid*[tiab] OR methylprednisolone[tiab]
OR dexamethasone[tiab] OR prednisolone[tiab] OR "Adrenal Cortex Hormones"[MeSH])
```

| Total | RCT[pt] | SR/MA | Observasional | Case report |
|---|---|---|---|---|
| 119 | 2 | 3 | 10 | 70 |

Temuan penting dari judul dan abstrak yang saya buka:
- Cochrane Review 2025 (PMID 40704556, DOI 10.1002/14651858.CD014935.pub2): 4 RCT, total 253 peserta, certainty of evidence "very low" untuk semua outcome. Kesimpulannya: "we do not know whether corticosteroids ... reduce all-cause mortality".
- Meta-analisis J Clin Med 2024 (PMID 39124577): 5 studi, 279 peserta, bukti "inconclusive".
- Systematic review Trans R Soc Trop Med Hyg 2014 (PMID 25266477).
- Satu RCT label-terbuka di Thailand, 2010 (PMID 19732091): dexamethasone pulse vs desmopressin vs kontrol pada keterlibatan paru. Satu entri lain berlabel RCT (PMID 21718474) ternyata protokol uji, bukan hasil.

Desain dominan adalah case report. Bukti pembandingnya sedikit, tetapi sudah terkumpul dalam sysrev yang menyimpulkan "belum diketahui".

**Status guideline: belum menjawab.** Saya tidak menemukan PNPK atau juknis Kemenkes yang membahas kortikosteroid untuk leptospirosis; isi Petunjuk Teknis Pengendalian Leptospirosis Kemenkes belum terverifikasi karena dokumennya tidak bisa saya buka. Guidance WHO 2003 untuk leptospirosis juga belum saya buka (belum terverifikasi). Cochrane 2025 sendiri menulis ada "lack of harmonised treatment strategies".

**Risiko**
- Bukti tidak langsung (indirectness): sebagian besar RCT meneliti keterlibatan paru atau perdarahan paru, sedangkan pasien ini tidak punya keterlibatan paru. Masalahnya ikterus menetap dan trombositopenia pada fase lanjut (hari ke-18).
- Bukti sedikit dan certainty sangat rendah. Ini cocok untuk latihan appraisal, tetapi kesimpulan EBCR kemungkinan besar "belum cukup bukti".
- Ada faktor perancu pada kasus: fungsi ginjal sudah mulai membaik sebelum steroid diberikan, dan ada riwayat konsumsi jamur liar.


## Kandidat 2: Metilprednisolon vs IVIG dosis kedua pada Kawasaki disease resisten IVIG

**Sitasi.** Ren Y. An infant with IVIG-resistant Kawasaki disease requiring repeated glucocorticoids therapy: A case report and literature review. Medicine (Baltimore). 2025;104(21):e42572.
DOI: 10.1097/MD.0000000000042572. PMID: 40419879. PMCID: PMC12113926.
Tautan: https://pmc.ncbi.nlm.nih.gov/articles/PMC12113926/
Status akses: open access (CC BY), full text sudah saya baca.

**Ringkasan kasus.** Anak perempuan 14 bulan (9,5 kg) dengan demam 3 hari dan ruam. Pemeriksaan fisik menunjukkan edema dan eritema tangan-kaki, injeksi konjungtiva bilateral, bibir pecah, strawberry tongue, dan limfadenopati servikal 2,5 cm. Laboratorium: CRP 81,8, ALT 375, bilirubin total 40,2 µmol/L, natrium 132,9, albumin 36,3, LED 74,8. Ekokardiografi menunjukkan Z-score arteri koroner kiri 2,06. Setelah IVIG 2 g/kg (disertai clopidogrel, bukan aspirin), demam menetap >36 jam. Pasien diberi metilprednisolon 10 mg/kg tiap 8 jam selama 3 hari lalu tapering cepat; demam kambuh, kemudian steroid IV diulang dan di-tapering pelan sampai total 42 hari. Ekokardiografi dan EKG normal pada follow-up 1 bulan sampai 1 tahun.

**Titik ketidakpastian.**
- Introduction: "Retreatment with IVIG remains the most widely accepted therapy ... largely due to the lack of standardized treatment protocols in this field."
- Discussion: "Clinical practices and local recommendations vary significantly for IVIG-resistant patients", serta "High-quality studies are needed".
- Abstrak (Lessons): perlu riset lebih lanjut tentang peran glukokortikoid.

**Jenis pertanyaan:** terapi.

**Clinical question.** Pada anak di bawah 2 tahun dengan Kawasaki disease yang resisten IVIG, apakah metilprednisolon IV dibanding IVIG dosis kedua menurunkan kejadian aneurisma atau lesi arteri koroner?

**PICO**

| Unsur | Isi |
|---|---|
| P | Anak <2 tahun dengan Kawasaki disease yang tetap demam ≥36 jam setelah IVIG 2 g/kg, dengan dilatasi koroner ringan dan penanda risiko resistensi (CRP tinggi, hiponatremia, hiperbilirubinemia) |
| I | Metilprednisolon IV (pulse atau kursus dengan tapering) |
| C | IVIG dosis kedua 2 g/kg |
| O | Lesi atau aneurisma arteri koroner pada 4–8 minggu; resolusi demam; kebutuhan terapi penyelamatan berikutnya; efek samping (anemia hemolitik akibat IVIG, efek samping steroid) |

**Pencarian awal (PubMed)**

```
("Mucocutaneous Lymph Node Syndrome"[MeSH] OR "Kawasaki disease"[tiab])
AND (resistan*[tiab] OR refractory[tiab] OR nonrespon*[tiab] OR "non-responsive"[tiab]
OR retreatment[tiab] OR "second IVIG"[tiab] OR "second dose"[tiab] OR rescue[tiab])
AND (methylprednisolone[tiab] OR prednisolone[tiab] OR corticosteroid*[tiab]
OR glucocorticoid*[tiab] OR steroid*[tiab])
```

| Total | RCT[pt] | SR/MA | Observasional | Case report |
|---|---|---|---|---|
| 297 | 6 | 14 | 92 | 88 |

Yang langsung relevan untuk pertanyaan terapi penyelamatan (rescue):
- Systematic review Pediatr Rheumatol 2019 (PMID 31775898): 8 studi, 388 pasien. Resolusi demam setara antara IVIG ulang (72%) dan metilprednisolon (73%); "Clinical significance of differences in coronary outcomes remains unclear."
- Meta-analisis perbandingan tidak langsung, BMC Pediatr 2019 (PMID 31101091): 12 studi, 372 pasien. Tidak ada beda bermakna dalam lesi koroner antara IVIG kedua, metilprednisolon, dan infliximab; efek samping lebih sedikit pada metilprednisolon.
- Studi komparatif Pediatr Int 2001 (PMID 11380911) dan RCT Pediatrics 2012 tentang terapi kombinasi pulse steroid untuk KD refrakter (PMID 22144699; isinya belum saya baca).

Sebagian besar RCT yang tertangkap filter adalah steroid sebagai terapi primer, bukan terapi penyelamatan. Desain dominan untuk pertanyaan ini adalah kohort retrospektif kecil, ditambah dua sysrev yang hasilnya belum tegas.

**Status guideline: sebagian.** ACR/Vasculitis Foundation 2021 (PMC12323682, saya cek lewat halaman PMC): "a second course of IVIG is conditionally recommended over use of glucocorticoids" untuk demam menetap setelah IVIG awal. Rekomendasinya conditional dengan certainty "Very Low". AHA Scientific Statement 2024 (PMID 39534969) baru saya baca abstraknya, sehingga isi rekomendasinya untuk KD resisten IVIG belum terverifikasi.

**Risiko**
- Bukti sudah lumayan banyak, dan ACR sudah memberi arah (walau lemah). Pertanyaannya perlu dijaga tetap pada outcome koroner, yang memang belum terjawab, supaya tidak terkesan sudah selesai.
- Kasusnya menyimpang dari standar: memakai clopidogrel, bukan aspirin, dan durasi steroid 42 hari jauh di atas protokol. Ini perlu dibahas sebagai keterbatasan, tetapi tidak menggugurkan PICO.
- Konteks dokter umum: Kawasaki ditangani spesialis anak. Pertanyaannya tetap sah untuk EBCR, tetapi kurang dekat dengan praktik layanan primer.


## Kandidat 3: Imunosupresi (siklofosfamid + glukokortikoid) pada keracunan paraquat

**Sitasi.** Havaldar AA. Successful management of paraquat poisoning: a case report. J Med Case Rep. 2025;19(1):479.
DOI: 10.1186/s13256-025-05546-y. PMID: 41044637. PMCID: PMC12495735.
Tautan: https://pmc.ncbi.nlm.nih.gov/articles/PMC12495735/
Status akses: open access (CC BY-NC-ND), full text sudah saya baca.

**Ringkasan kasus.** Artikel memuat dua pasien. Kasus 1 lebih cocok sebagai "pasien": laki-laki 29 tahun dari India Selatan yang meminum paraquat, sudah dibilas lambung di RS lokal, lalu dirujuk karena fungsi ginjal memburuk. Nadi 92, TD 120/80, RR 24, SpO2 97% udara ruang, PaO2/FiO2 266. Kreatinin naik dari 0,9 ke 2,8 di narasi, sementara tabel menulis 5. Ia mendapat siklofosfamid 15 mg/kg (1 g) selama 3 hari, dexamethasone 8 mg dua kali sehari yang diganti prednisolon tapering 10 hari, dan 5 sesi hemodialisis. Pasien pulang tanpa keterlibatan paru dan fungsi ginjalnya baik pada follow-up 2,5 tahun.

**Titik ketidakpastian.**
- Introduction: imunomodulator "have been used and showed mixed results".
- Discussion: penulis menjajarkan RCT Lin yang positif, RCT Gawarammana yang negatif, Cochrane lama yang positif, dan Cochrane baru yang "showed no difference in short-term mortality"; data infeksi disebut "limited".
- Discussion penutup: "Future studies on establishing a set protocol or guidelines for managing paraquat poisoning will be helpful".

**Jenis pertanyaan:** terapi.

**Clinical question.** Pada dewasa muda dengan keracunan paraquat oral yang disertai AKI tanpa gagal napas saat datang, apakah siklofosfamid ditambah glukokortikoid di samping perawatan standar, dibanding perawatan standar saja, menurunkan mortalitas?

**PICO**

| Unsur | Isi |
|---|---|
| P | Dewasa muda dengan keracunan paraquat oral, AKI progresif, tanpa gagal napas saat datang |
| I | Imunosupresi: siklofosfamid IV + glukokortikoid (dexamethasone atau metilprednisolon) ditambah perawatan standar |
| C | Perawatan standar saja (dekontaminasi, terapi pengganti ginjal, suportif) atau plasebo |
| O | Mortalitas di RS dan pada 3 bulan; gagal napas atau fibrosis paru; infeksi; pemulihan fungsi ginjal |

**Pencarian awal (PubMed)**

```
(Paraquat[MeSH] OR paraquat[tiab]) AND (cyclophosphamide[tiab] OR methylprednisolone[tiab]
OR dexamethasone[tiab] OR glucocorticoid*[tiab] OR corticosteroid*[tiab] OR immunosuppress*[tiab])
```

| Total | RCT[pt] | SR/MA | Observasional | Case report |
|---|---|---|---|---|
| 225 | 6 | 9 | 31 | 51 |

Temuan penting:
- RCT terbesar, Clin Toxicol 2018 (PMID 29098875): 299 pasien di Sri Lanka. Mortalitas di RS 53% vs 62% (p = 0,12), dan tidak ada perbedaan pada 3 bulan.
- RCT lebih kecil: Lin 1999 dan 2006 dari Taiwan, serta Afzali 2008 dari Iran.
- Cochrane 2021 (PMID 34190331): 4 RCT, 463 peserta. Hasilnya "may slightly reduce mortality" di RS dengan certainty rendah, dan "little or no effect" pada 3 bulan.
- Beberapa meta-analisis tambahan (2015, 2019, 2020) dari kelompok berbeda.

Desain dominan: RCT kecil dan meta-analisis yang heterogen.

**Status guideline: belum menjawab.** Di PubMed tidak ada guideline atau konsensus yang tertangkap (0 hasil dengan filter guideline). Pencarian web juga tidak menemukan rekomendasi WHO atau PNPK untuk imunosupresi pada paraquat, sehingga status WHO saya tulis belum terverifikasi. Yang ada hanya protokol lokal, misalnya protokol pusat racun Ramathibodi.

**Risiko**
- Data kasus kurang lengkap: dosis yang diminum dan kadar paraquat plasma tidak tersedia; pemeriksaan fisik hanya tanda vital; angka kreatinin tidak konsisten antara narasi dan tabel; dua pasien digabung dalam satu artikel.
- Bukti relatif banyak dan sudah ada Cochrane. Celahnya ada pada outcome jangka panjang dan subkelompok tanpa keterlibatan paru, jadi pertanyaannya perlu dirumuskan tajam supaya tidak sekadar mengulang Cochrane.
- Populasi pasien yang selamat tanpa gangguan paru kemungkinan menelan dosis kecil. Ini perancu besar bila outcome kasus dipakai sebagai argumen.


## Kandidat 4: Prednisolon pada Bell's palsy bayi

**Sitasi.** Bannout AA, Hussein FH, Haddad LR. Management of Bell's palsy in a 2-month-old following COVID-19 infection: a case report and review of the literature. BMC Neurol. 2026;26(1):475.
DOI: 10.1186/s12883-026-05045-7. PMID: 42251316. PMCID: PMC13390424.
Tautan: https://pmc.ncbi.nlm.nih.gov/articles/PMC13390424/
Status akses: open access (CC BY-NC-ND), full text sudah saya baca.

**Ringkasan kasus.** Bayi perempuan 2 bulan, lahir cukup bulan, COVID-19 positif pada usia 4 minggu. Tiga minggu kemudian muncul asimetri wajah kiri yang progresif selama 3 hari: tidak bisa menutup mata kiri, kerutan dahi berkurang, lipatan nasolabial datar. Tanda vital normal dan tidak ada defisit neurologis lain. Lab darah, panel virus, dan LCS normal; MRI menunjukkan enhancement segmen intratemporal nervus fasialis kiri (neuritis). Setelah diskusi dengan orang tua, pada hari ke-4 onset diberikan prednisolon 1 mg/kg/hari selama 5 hari lalu tapering (total 10 hari) plus proteksi mata. Pasien sembuh sempurna pada follow-up, tanpa efek samping.

**Titik ketidakpastian.**
- Abstrak: "Despite no clear guidelines or recommendations favoring corticosteroid treatment vs conservative management in this age category".
- Case presentation: opsi yang ditimbang adalah observasi vs kortikosteroid, IVIG, atau asiklovir, "especially with the lack of clear evidence-based guidelines".
- Discussion: "Management of Bell's palsy in children, particularly in infants, remains controversial", serta "Given this uncertainty, treatment decisions in infants should be individualized."
- Conclusion: "Further studies are needed ... to further assess the efficacy and safety of oral prednisolone in this age group."

**Jenis pertanyaan:** terapi.

**Clinical question.** Pada bayi dan anak dengan Bell's palsy idiopatik yang datang dalam beberapa hari pertama onset, apakah prednisolon oral dibanding observasi atau plasebo meningkatkan proporsi pemulihan fungsi wajah lengkap?

**PICO**

| Unsur | Isi |
|---|---|
| P | Bayi atau anak dengan Bell's palsy idiopatik (paresis fasialis perifer unilateral, defisit progresif) yang datang dalam beberapa hari pertama onset |
| I | Prednisolon oral sekitar 1 mg/kg/hari selama 10 hari |
| C | Plasebo atau observasi dengan perawatan suportif (proteksi mata) |
| O | Pemulihan lengkap (House-Brackmann I) pada 1, 3, dan 6 bulan; sekuel (sinkinesis); efek samping steroid |

**Pencarian awal (PubMed)**

```
("Bell Palsy"[MeSH] OR "Bell's palsy"[tiab] OR "Bell palsy"[tiab] OR "idiopathic facial palsy"[tiab]
OR "idiopathic facial paralysis"[tiab]) AND (child*[tiab] OR pediatric[tiab] OR paediatric[tiab]
OR infant*[tiab] OR Child[MeSH] OR Infant[MeSH]) AND (prednisolone[tiab] OR prednisone[tiab]
OR corticosteroid*[tiab] OR steroid*[tiab] OR "Adrenal Cortex Hormones"[MeSH])
```

| Total | RCT[pt] | SR/MA | Observasional | Case report |
|---|---|---|---|---|
| 169 | 9 | 8 | 68 | 35 |

Temuan penting:
- RCT BellPIC, Neurology 2022 (PMID 36008143): 187 anak usia 6 bulan sampai <18 tahun. Pemulihan lengkap pada 1 bulan 49% (prednisolon) vs 57% (plasebo); trial underpowered (target 540).
- Analisis lanjutan BellPIC: follow-up 12 bulan dan evaluasi ekonomi.
- RCT Pediatr Neurol 1999 (PMID 10593672).
- Meta-analisis Facial Plast Surg Aesthet Med 2025 (PMID 41218807): 11 studi, 750 anak. Pada follow-up akhir tidak ada perbedaan, tetapi subkelompok steroid monoterapi menunjukkan pemulihan lengkap lebih tinggi setelah 1 bulan.
- Systematic review 2001 dan 2012.

Desain dominan: kohort retrospektif, ditambah satu RCT anak yang underpowered dan satu meta-analisis yang hasilnya bertentangan dengan RCT tersebut.

**Status guideline: belum menjawab untuk anak dan bayi.** CMAJ 2014 (PMC4150706, saya cek lewat halaman PMC) merekomendasikan "corticosteroids for all patients with Bell palsy" tanpa batas usia, tetapi tidak membahas anak secara khusus. Guideline AAN 2012 dan guideline SFORL 2020 ditujukan untuk dewasa (berdasarkan isi case report dan abstrak SFORL). Cakupan usia guideline AAO-HNS 2013 belum terverifikasi karena halamannya tidak bisa saya buka. Guideline Jepang 2023 baru saya baca abstraknya, dan isinya tentang anak belum terverifikasi.

**Risiko**
- Indirectness besar: BellPIC hanya merekrut usia ≥6 bulan, sehingga untuk bayi 2 bulan tidak ada bukti langsung. EBCR akan berupa ekstrapolasi dari data anak yang lebih besar, dan ini harus ditulis terang.
- Pemberian steroid dimulai hari ke-4 onset, sedikit di luar jendela 72 jam yang dipakai BellPIC.
- Diagnosis pasca-COVID dan temuan MRI membuat pasien ini mungkin tidak mewakili Bell's palsy idiopatik pada umumnya.


## Kandidat yang gugur

| Case report | Alasan gugur |
|---|---|
| Caravedo M et al. XDR *Salmonella* Typhi relaps setelah meropenem monoterapi, IDCases 2021 (PMC7820545) | Data kasus tidak lengkap: tanda vital dan pemeriksaan fisik hampir tidak dilaporkan. Penulis tidak menyatakan ketidakpastian secara eksplisit. Bukti pembanding (meropenem + azitromisin vs monoterapi) hanya beberapa studi observasional, misalnya Infect Drug Resist 2022 (PMID 36277244), tanpa RCT atau SR. Relevansi XDR typhoid di Indonesia juga rendah. |
| Kawasaki usia 3 bulan dengan infliximab, Cureus 2026 (PMC12867073) | Data lengkap, tetapi penulis tidak menyatakan ketidakpastian. Pilihan terapi hanya disebut "may be influenced by institutional resources". |
| Infliximab untuk KD resisten IVIG dengan hepatitis kolestatik, Front Pediatr 2026 (PMC13125047) | Layak sebagai cadangan kandidat 2. Ketidakpastiannya eksplisit ("no universally accepted treatment guidelines"; waktu pemberian infliximab yang optimal). Saya mendahulukan kasus glukokortikoid karena perbandingan steroid vs IVIG lebih relevan untuk sumber daya terbatas. |
| Tetanus generalisata pada remaja, Int Med Case Rep J 2026 (PMC12949565) | Tidak ada titik keputusan yang diperdebatkan penulis. |
| Scrub typhus kongenital, Emerg Microbes Infect 2025 (PMC12337731) | Terlalu eksotis: neonatus, dan bukti pembanding pilihan antibiotik pada neonatus praktis tidak ada. |
| Leptospirosis berat di ICU, Cureus 2025 (PMC12166323) | Tumpang tindih dengan kandidat 1, dan ketidakpastian yang dibahas lebih ke antibiotik dan suportif. |
| Paraquat dengan AKI di layanan terbatas, Ann Med Surg 2026 (PMC13561190) | Keputusan utama yang dibahas adalah pulang atas permintaan sendiri karena biaya, bukan pilihan terapi. |

## Rekomendasi

**Kandidat terbaik: Kandidat 1 (kortikosteroid pada leptospirosis berat, Şahin et al. 2026).**

Alasannya:
1. Paling dekat dengan praktik di Indonesia. Leptospirosis endemik dan sering muncul setelah banjir, dan pertanyaan "perlu steroid atau tidak" nyata di RS daerah.
2. Ketidakpastiannya dinyatakan eksplisit oleh penulis kasus, dan dikonfirmasi oleh Cochrane 2025 yang menyimpulkan efeknya belum diketahui (certainty very low). Topiknya jelas belum terjawab tuntas.
3. Bukti pembanding cukup untuk dikerjakan tanpa berlebihan: sekitar 4 RCT ditambah beberapa kohort, sudah terangkum dalam dua sysrev. Jumlah ini realistis untuk dibaca dan di-appraise mahasiswa dalam satu tugas.
4. Data kasusnya paling lengkap: anamnesis paparan, pemeriksaan fisik, tabel laboratorium serial 11 titik waktu, tatalaksana dengan dosis, dan luaran sampai hari ke-29.

Hal yang perlu disiapkan: bahas indirectness secara terbuka, karena hampir semua RCT meneliti leptospirosis dengan keterlibatan paru, sedangkan pasien ini tidak. Bila ingin pertanyaan yang lebih langsung didukung RCT, Kandidat 2 (Kawasaki) adalah alternatif dengan bukti pembanding paling banyak.
