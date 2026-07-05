# CompTIA Security+ (SY0-701) — Domain 5: Security Program Management and Oversight (20%)

File lanjutan dari Domain 1-4. Domain terakhir! Simbol 🔑 = mnemonic/jembatan keledai.

---

### Hari 1 — Security Governance

#### A. Hirarki Dokumen Governance (umum → spesifik)
| Level | Penjelasan | Sifat |
|---|---|---|
| **Policy** | Pernyataan tujuan/arah tingkat tinggi | Wajib, broad |
| **Standard** | Persyaratan spesifik & wajib | Wajib, spesifik |
| **Procedure** | Instruksi langkah demi langkah | Wajib, detail |
| **Guideline** | Rekomendasi best practice | **Tidak wajib** |

🔑 "Policy nentuin arah, Standard nentuin angka pastinya, Procedure nentuin langkah-langkahnya, Guideline cuma saran."
⚠️ **Guideline** satu-satunya yang opsional di antara 4 ini.

Contoh policy: AUP, Change management policy, Onboarding/Offboarding policy, BCP, Incident Response Plan, SDLC policy.

#### B. Peran dalam Data Governance
| Peran | Tanggung jawab |
|---|---|
| **Data owner** | Accountable atas data, tentukan klasifikasi & akses |
| **Data controller** | Tentukan tujuan & cara data pribadi diproses (istilah GDPR) |
| **Data processor** | Memproses data atas nama controller |
| **Data custodian/steward** | Jaga data sehari-hari secara teknis |

🔑 Owner = "yang punya & tanggung jawab". Custodian = "yang jaga sehari-hari". Controller = "yang nentuin TUJUAN". Processor = "yang ngerjain PROSESNYA atas nama controller".

---

### Hari 2 — Risk Management

#### A. Qualitative vs Quantitative Risk Assessment
Qualitative = subjektif (High/Medium/Low). Quantitative = angka/nilai uang konkret.

#### B. Rumus Kuantitatif
| Istilah | Rumus | Arti |
|---|---|---|
| **SLE** | AV × EF | Kerugian per 1 kali kejadian |
| **ARO** | — | Frekuensi kejadian per tahun |
| **ALE** | SLE × ARO | Kerugian per tahun |

**Contoh:** AV $50.000, EF 20%, ARO 2 → SLE = $10.000, ALE = $20.000. ALE dipakai buat justifikasi budget mitigasi.

#### C. Risk Treatment (4 strategi)
| Strategi | Penjelasan |
|---|---|
| **Accept** | Terima risiko, gak ambil tindakan |
| **Avoid** | Hilangkan risiko sepenuhnya |
| **Transfer** | Pindahkan ke pihak lain (asuransi) |
| **Mitigate** | Kurangi lewat kontrol keamanan |

🔑 "Ada Apa Terjadi Malam ini" → Accept, Avoid, Transfer, Mitigate.

#### D. Metrik Penting
| Istilah | Arti |
|---|---|
| **RTO** | Berapa lama maksimal sistem boleh down |
| **RPO** | Berapa banyak data (waktu) boleh hilang — nentuin frekuensi backup |
| **MTTR** | Rata-rata waktu memperbaiki |
| **MTBF** | Rata-rata waktu antar kegagalan |

🔑 RTO = "berapa lama boleh mati". RPO = "berapa banyak data boleh hilang".

---

### Hari 3 — Third-Party Risk Management

#### Jenis Perjanjian (hafalan penting!)
| Perjanjian | Fokus | Sifat |
|---|---|---|
| **SLA** | Jaminan tingkat layanan (uptime) | Mengikat |
| **NDA** | Lindungi info rahasia | Mengikat |
| **MOU** | Kesepahaman bersama, informal | **Biasanya TIDAK mengikat** |
| **BPA** | Ketentuan kemitraan bisnis | Mengikat |
| **MSA** | Kontrak payung jangka panjang + SOW per proyek | Mengikat |

⚠️ **MOU** satu-satunya yang biasanya gak mengikat hukum.

Vendor assessment (kuesioner, right-to-audit clause) dan vendor monitoring (berkelanjutan, bukan cuma sekali di awal).

---

### Hari 4 — Compliance & Audits/Assessments

#### A. Due Diligence vs Due Care
| | Due diligence | Due care |
|---|---|---|
| Kapan | Sebelum keputusan | Setelah, berkelanjutan |

🔑 Due diligence = "riset dulu sebelum". Due care = "jaga terus setelah".

Konsekuensi non-compliance: denda, sanksi, kerusakan reputasi, pencabutan lisensi. **Right to be forgotten** (GDPR) — individu berhak minta data pribadinya dihapus.

#### B. Jenis Audit
Internal audit (tim sendiri) vs External audit (pihak ketiga, lebih objektif) vs Regulatory audit vs Attestation (sertifikasi resmi).

#### C. Penetration Testing — Tingkat Pengetahuan Tester
| Istilah lama | Istilah baru | Pengetahuan tester |
|---|---|---|
| White box | Known environment | Full info |
| Black box | Unknown environment | Gak ada info (simulasi attacker asli) |
| Gray box | Partially known environment | Sebagian info |

---

### Hari 5 — Security Awareness Practices

#### A. Phishing Campaign & Simulasi
Simulasi phishing rutin buat ukur kerentanan & sekaligus jadi sarana edukasi langsung.

#### B. Kategori Perilaku
Risky behavior (install software gak resmi), Unexpected behavior (menyimpang dari pola normal), Unintentional behavior (gak sengaja, kaitannya ke insider threat unintentional Domain 2).

#### C. Reporting Mechanism
Karyawan perlu tau cara & ke mana melaporkan aktivitas mencurigakan (tombol "Report Phishing").

#### D. Pengembangan & Eksekusi Program
Disesuaikan per role/level risiko (misal training BEC khusus tim finance).

#### E. Mengukur Efektivitas
Click-through rate simulasi phishing (harus turun dari waktu ke waktu), reporting rate, completion rate training. Program yang bagus = berulang & terukur, bukan training 1x setahun lalu selesai.

---

## ✅ Domain 5: Security Program Management — SELESAI (20%)

## 🎉 SELURUH 5 DOMAIN SECURITY+ SY0-701 SUDAH LENGKAP! (100%)

| Domain | Bobot | Status |
|---|---|---|
| Domain 1: General Security Concepts | 12% | ✅ Selesai |
| Domain 2: Threats, Vulnerabilities & Mitigations | 22% | ✅ Selesai |
| Domain 3: Security Architecture | 18% | ✅ Selesai |
| Domain 4: Security Operations | 28% | ✅ Selesai |
| Domain 5: Security Program Management | 20% | ✅ Selesai |

Selanjutnya: review menyeluruh + practice exam lengkap sebelum ujian sungguhan.
