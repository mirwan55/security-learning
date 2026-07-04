# CompTIA Security+ (SY0-701) — Catatan Materi

---

## Domain 1: General Security Concepts (bobot 12%)

### Hari 1 (2 Juli 2026) — CIA Triad, Non-repudiation, AAA Framework

#### 1. CIA Triad
Inti dari semua definisi "keamanan informasi".

- **Confidentiality** — data hanya bisa diakses pihak yang berhak.
  Implementasi: enkripsi, access control.
  Analogi: mirip `GRANT`/`REVOKE` privilege per user/role di SQL.
- **Integrity** — data tidak berubah tanpa otorisasi, atau perubahannya bisa terdeteksi.
  Implementasi: hashing, digital signature.
  Analogi: hash SHA-256 yang dipakai buat verifikasi integritas file download.
- **Availability** — sistem/data harus bisa diakses saat dibutuhkan oleh yang berhak.
  Implementasi: redundancy, backup, load balancing.
  Musuh utama: DoS/DDoS attack.

🔑 **Mnemonic:** "**C**ewek **I**tu **A**sik" kalau dia gak bisa diintip orang lain (Confidentiality), gak berubah-ubah sifatnya (Integrity), dan selalu ada saat dibutuhin (Availability). *(silakan ganti sama versi kamu sendiri kalau ada yang lebih nempel!)*

Kebalikannya = **DAD Triad** (cara mikir dari sisi attacker): **D**isclosure, **A**lteration, **D**enial — attacker berusaha membongkar (lawan confidentiality), mengubah (lawan integrity), atau meniadakan akses (lawan availability).

#### 2. Non-repudiation
Pihak yang melakukan suatu aksi tidak bisa menyangkal telah melakukannya.
Dicapai lewat digital signature + logging.
Contoh: sign dokumen pakai private key → gak bisa bilang "bukan saya yang kirim", karena signature unik & terverifikasi ke identitas pengirim.

#### 3. AAA Framework
| Elemen | Pertanyaan kunci | Contoh |
|---|---|---|
| **Authentication** | Kamu siapa? | password, biometric, MFA |
| **Authorization** | Kamu boleh ngapain? | permission, role |
| **Accounting** | Apa yang udah kamu lakuin? | audit log |

🔑 **Mnemonic:** "**Siapa** kamu → **Boleh apa** kamu → **Tercatat** ke mana" = Authentication → Authorization → Accounting.

⚠️ **Yang paling sering ketuker:** login ke sistem = **Authentication**. Begitu masuk, sistem cek "role kamu admin atau user biasa" = **Authorization**. Dua hal beda, jangan disamain!

#### 4. Zero Trust (intro, didalami lebih lanjut nanti)
Prinsip **"never trust, always verify"** — gak ada entitas (user/device) yang otomatis dipercaya walau udah berada di dalam jaringan internal.

---

### Hari 2 (2 Juli 2026) — Security Controls: Categories & Types

Soal ujian sering minta identifikasi **kategori + jenis** dari satu contoh kontrol sekaligus. Bayangin ini matriks 2 dimensi: **Category** (gimana cara diimplementasikan) x **Type** (fungsi/tujuannya apa).

#### A. Control Categories (4) — "diimplementasikan lewat apa?"

| Kategori | Penjelasan | Contoh |
|---|---|---|
| **Technical** | Diimplementasikan lewat sistem/teknologi | Firewall, enkripsi, IDS/IPS, access control list |
| **Managerial** | Kebijakan, prosedur, governance — sisi "aturan/paperwork" | Security policy, risk assessment, standar |
| **Operational** | Dijalankan oleh manusia sehari-hari | Prosedur backup manual, patroli satpam |
| **Physical** | Membatasi/melindungi secara fisik | Kunci, pagar, satpam, CCTV, badge, mantrap |

🔑 **Mnemonic:** "**Te**knisi **M**engatur **O**perasional **Pa**gar" → Technical, Managerial, Operational, Physical.

#### B. Control Types (6) — "fungsinya buat apa?"

| Jenis | Penjelasan | Contoh |
|---|---|---|
| **Preventive** | Mencegah insiden sebelum terjadi (aktif menghalangi) | Firewall, MFA, kunci pintu, nonaktifkan akun mantan karyawan |
| **Deterrent** | Membuat attacker urung mencoba (ancaman/psikologis, gak menghalangi secara teknis) | Papan peringatan, kamera yang terlihat jelas, stiker "alarm aktif" (meski alarmnya belum beneran ada) |
| **Detective** | Mendeteksi insiden yang sedang/sudah terjadi | IDS, log monitoring, CCTV rekaman |
| **Corrective** | Memperbaiki/memulihkan setelah insiden | Patching, restore backup, isolasi + bersihkan malware |
| **Compensating** | Alternatif kalau kontrol utama gak bisa diterapkan | Sistem lama gak bisa di-patch → tambah network segmentation & monitoring ekstra |
| **Directive** | Mengarahkan/mewajibkan suatu tindakan (via kebijakan/aturan) | Kebijakan wajib ganti password 90 hari, kebijakan wajib training tahunan, rambu "wajib pakai ID card" |

🔑 **Mnemonic (alur cerita):** "**Cegah dulu** (Preventive) sebelum kejadian → kalau attacker masih nekat, **bikin dia mikir dua kali** (Deterrent) → begitu kejadian, **baru ketauan** (Detective) → langsung **diperbaiki** (Corrective) → kalau gak bisa langsung diperbaiki, **kasih pengganti sementara** (Compensating) → dan semuanya **diatur lewat arahan resmi** (Directive)."

#### Contoh gabungan Category + Type

| Kontrol | Category | Type |
|---|---|---|
| Firewall | Technical | Preventive |
| Satpam yang jaga pintu | Physical | Preventive **dan** Deterrent |
| CCTV yang kelihatan jelas (kameranya) | Physical | Deterrent **dan** Detective |
| Rambu "Area diawasi CCTV 24 jam" (tulisannya doang) | Physical | Deterrent saja |
| Rambu "Wajib pakai ID card" | Physical/Managerial | **Directive** (bukan deterrent — ini instruksi wajib, bukan ancaman) |
| Kebijakan wajib ganti password 90 hari | Managerial | Directive |
| Kebijakan wajib training tahunan (syarat akses) | Managerial | Directive |
| Nonaktifkan akun begitu karyawan resign | Technical | Preventive |
| Isolasi + bersihkan komputer kena malware | Technical/Operational | Corrective |
| Network segmentation ekstra utk sistem lama yg gak bisa di-patch | Technical | Compensating |

⚠️ **Poin krusial (sering jadi jebakan soal):**
- **Deterrent vs Directive**: kalau kalimatnya "ancaman konsekuensi" (*"Anda diawasi", "pelanggaran dikenakan sanksi"*) → **Deterrent**. Kalau kalimatnya "instruksi wajib" (*"wajib pakai X", "harus melakukan Y"*) → **Directive**.
- **Directive vs Preventive**: kalau yang dideskripsikan soal adalah **kebijakan/aturannya** ("kebijakan mewajibkan...") → **Directive** (Managerial). Kalau yang dideskripsikan adalah **mekanisme teknis yang aktif menghalangi** (sistem otomatis blokir/enkripsi) → **Preventive** (Technical). Baca fokus kalimat soal baik-baik: aturan vs aksi teknis.
- Satu kontrol bisa punya lebih dari satu *type* sekaligus (misal satpam & CCTV kamera) — tapi kalau soal minta 1 jawaban, pilih yang paling spesifik/utama sesuai definisi.

### Hari 3 (2 Juli 2026) — Zero Trust (mendalam), Gap Analysis, Change Management

#### A. Zero Trust — mendalam
Arsitektur Zero Trust dibagi jadi 2 "plane":

**1. Control Plane** — yang "mikir" dan memutuskan
- **Adaptive identity** — identitas dinilai berdasarkan konteks (lokasi, device, jam akses, perilaku), bukan cuma username/password statis
- **Policy-driven access control** — keputusan akses berdasarkan kebijakan/atribut (role, attribute)
- **Threat scope reduction** — perkecil attack surface, batasi jumlah entry point yang mungkin
- **Policy Engine (PE)** — "otaknya", memutuskan apakah akses diizinkan berdasarkan kebijakan

**2. Data Plane** — yang "mengeksekusi" keputusan
- **Policy Administrator (PA)** — menyampaikan/mengeksekusi keputusan dari Policy Engine ke sistem
- **Policy Enforcement Point (PEP)** — "gerbangnya", titik yang benar-benar allow/block akses sesuai keputusan
- **Implicit trust zones** — zona yang dipercaya begitu saja (tujuan Zero Trust: perkecil zona ini sebanyak mungkin)

🔑 **Mnemonic:** "**PE mikir**, **PA ngomong**, **PEP jaga pintu**" — Policy Engine memutuskan → Policy Administrator menyampaikan keputusan → Policy Enforcement Point yang benar-benar buka/tutup akses.

#### B. Gap Analysis
Proses membandingkan **kondisi keamanan saat ini** (current state) vs **kondisi yang seharusnya/standar yang dituju** (desired state), untuk menemukan "gap" yang perlu ditutup.

- **Business gap analysis** — fokus ke proses bisnis
- **Technical gap analysis** — fokus ke kontrol teknis

Biasa dipakai sebelum audit compliance (misal ISO 27001) atau sebagai bagian dari risk assessment — hasil akhirnya berupa roadmap/rekomendasi buat menutup gap.

🔑 **Cara gampang inget:** kayak GPS — "posisi sekarang" (current state) vs "tujuan" (desired state) = jaraknya itu **gap** yang harus ditempuh.

#### C. Change Management
Proses formal mengelola perubahan sistem/infrastruktur biar terkontrol — banyak insiden keamanan justru terjadi gara-gara perubahan yang gak terdokumentasi/gak direncanakan matang.

| Elemen | Maksudnya |
|---|---|
| **Approval process** | Perubahan harus disetujui dulu (via Change Advisory Board/CAB) sebelum dieksekusi |
| **Ownership** | Siapa yang bertanggung jawab atas perubahan ini |
| **Stakeholders** | Pihak yang terdampak, perlu dikonsultasikan/diberi tahu |
| **Impact analysis** | Menilai dampak perubahan sebelum dilakukan |
| **Test results** | Hasil pengujian di lingkungan non-production sebelum ke production |
| **Backout plan** | Rencana rollback kalau perubahan gagal |
| **Maintenance window** | Waktu terjadwal buat eksekusi perubahan (biasanya di luar jam sibuk) |

🔑 **Mnemonic (alur cerita):** "**Setuju dulu** (Approval) → tentukan **siapa penanggung jawab & siapa kena dampak** (Ownership & Stakeholders) → **hitung risikonya** (Impact analysis) → **coba dulu di tempat aman** (Test) → siapkan **jalan mundur** (Backout plan) → pilih **waktu yang sepi** (Maintenance window)."

Bonus koneksi ke coding: **version control** (git) juga bagian dari change management — tiap perubahan config/kode tercatat, bisa di-rollback. Sama persis konsepnya kayak `git revert` kalau ada commit yang bermasalah.

---

## ✅ Domain 1: General Security Concepts — SELESAI (12%)
Ringkasan yang udah dikuasai: CIA Triad, Non-repudiation, AAA Framework, Security Controls (categories & types), Zero Trust, Gap Analysis, Change Management.
