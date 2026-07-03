# CompTIA Security+ (SY0-701) — Latihan Soal

Cara pakai: jawab dulu semua soal di satu minggu SEBELUM scroll ke bagian "Jawaban & Pembahasan" di bawahnya. Kalau ada yang salah/ragu, tandai buat direview lagi pas H-3 sebelum ujian.

---

## Minggu 1 — Domain 1: General Security Concepts

### Soal
1. Ada sistem login dengan password + OTP via SMS. Itu contoh implementasi dari elemen AAA yang mana?
2. Perusahaan kena ransomware sampai datanya gak bisa diakses sama sekali. Itu paling utama melanggar prinsip CIA yang mana?
3. Coba kasih 1 contoh dari pengalaman kamu pakai SQL/Python yang menurutmu berhubungan ke Confidentiality atau Integrity.

<br><br><br><br><br>

### Jawaban & Pembahasan — Minggu 1

1. **Authentication.** Password + OTP adalah 2 faktor yang dipakai buat verifikasi "kamu siapa" (multi-factor authentication) — bukan Authorization (itu soal "boleh ngapain setelah login") atau Accounting (itu soal pencatatan aktivitas).
2. **Availability.** Ransomware biasanya meng-enkripsi data korban sehingga pemilik sah gak bisa akses datanya sendiri — walaupun kadang ransomware modern juga mencuri data (melanggar Confidentiality) sebagai "double extortion", tapi dampak utama & langsung yang dirasakan adalah hilangnya akses (Availability).
3. *(jawaban personal — didiskusikan langsung pas sesi belajar, gak ada jawaban baku)*

---

## Minggu 1 — Domain 1: Security Controls (Categories & Types)

### Soal
1. Ada perusahaan pasang rambu besar "Area ini diawasi CCTV 24 jam" di pintu masuk gudang. Ini termasuk *type* kontrol apa?
2. Sistem lama gak bisa di-update ke versi terbaru karena software vendor discontinued, jadi tim IT nambahin network segmentation & monitoring ekstra buat sistem itu. Ini contoh *type* kontrol apa?
3. Kategorikan (category + type): kebijakan perusahaan yang mewajibkan semua karyawan ganti password tiap 90 hari.
4. Perusahaan mewajibkan semua karyawan menyelesaikan security awareness training tiap tahun sebagai syarat mempertahankan akses ke sistem — kalau gak selesai, akses otomatis di-suspend. Ini termasuk *type* apa?
5. Di pintu masuk ruang server ada rambu: "Wajib pakai ID card. Dilarang masuk tanpa pendamping." Ini termasuk *type* apa, dan kenapa beda dari soal nomor 1?
6. Setiap login ke sistem HR muncul banner: "Sistem ini hanya untuk penggunaan resmi. Aktivitas dipantau dan pelanggaran dapat dikenakan sanksi hukum." Ini termasuk *type* apa?
7. Perusahaan punya kebijakan: semua laptop kerja wajib dienkripsi full-disk sebelum boleh dibawa keluar kantor. Ini termasuk *type* apa?
8. Toko retail memasang stiker "Toko ini dilengkapi sistem alarm keamanan" padahal alarmnya belum benar-benar terpasang. Ini termasuk *type* apa?
9. Begitu proses offboarding karyawan resign selesai, tim IT langsung menonaktifkan akunnya. Ini termasuk *type* apa?
10. Setelah ditemukan malware di komputer, tim IT langsung mengisolasi komputer itu dari jaringan dan menjalankan pembersihan malware. Ini termasuk *type* apa?

<br><br><br><br><br>

### Jawaban & Pembahasan

1. **Deterrent saja.** Rambu/tulisan gak fisik menghalangi (bukan Preventive) dan gak punya kemampuan mendeteksi (bukan Detective — itu tugas kameranya, bukan tulisannya). Fungsinya murni bikin calon pelaku mikir dua kali.
2. **Compensating.** Technical category. Alternatif kontrol karena patching (kontrol utama) gak bisa dilakukan.
3. **Managerial + Directive.** Ini kebijakan/paperwork (Managerial), dan sifatnya mewajibkan tindakan spesifik (Directive) — bukan Operational (itu prosedur rutin yang dijalankan orang) dan bukan murni Preventive/Deterrent.
4. **Directive.** Sama pola dengan soal 3 — "diwajibkan sebagai syarat" = arahan/mandat.
5. **Directive**, bukan Deterrent. Kata kunci "wajib" = instruksi positif tentang apa yang HARUS dilakukan. Beda dari rambu CCTV (soal 1) yang isinya cuma ancaman/peringatan tanpa menyuruh tindakan spesifik.
6. **Deterrent**, bukan Preventive. Kalimat itu ancaman konsekuensi, bukan mekanisme yang secara teknis menghalangi apa pun — banner cuma teks, gak benar-benar mencegah aksi (yang beneran mencegah = Authorization/access control).
7. **Directive** (Managerial) — konsisten dengan pola "kebijakan mewajibkan X" (soal 3 & 4). Kalau soal ditulis "laptop otomatis terenkripsi lewat sistem" (fokus ke mekanisme, bukan kebijakan), baru itu Preventive (Technical). Baca fokus kalimat: aturan vs aksi teknis.
8. **Deterrent.** Bahkan stiker "alarm" palsu tetap deterrent murni — efeknya psikologis, gak peduli sistemnya beneran ada atau enggak.
9. **Preventive** (Technical) — tindakan konkret yang benar-benar memblokir akses, bukan sekadar aturan/ancaman.
10. **Corrective** — tindakan setelah insiden ketemu untuk remediasi.

---

## Minggu 1 — Domain 1: Zero Trust, Gap Analysis, Change Management

### Soal
1. Dalam Zero Trust, komponen mana yang bertugas **memutuskan** apakah akses diizinkan, dan komponen mana yang bertugas **benar-benar membuka/menutup gerbang** akses?
2. Sebuah perusahaan mau ikut sertifikasi ISO 27001, jadi mereka bandingkan kontrol keamanan yang ada sekarang dengan requirement standar ISO 27001 buat tau apa aja yang kurang. Ini contoh aktivitas apa?
3. Tim IT mau upgrade versi database production. Sebelum eksekusi, mereka: (a) minta approval ke CAB, (b) uji coba dulu di staging environment, (c) siapkan rencana kalau upgrade gagal harus balik ke versi lama. Poin (c) itu disebut apa dalam Change Management?

<br><br><br><br><br>

### Jawaban & Pembahasan

1. **Policy Engine (PE)** yang memutuskan (otaknya), **Policy Enforcement Point (PEP)** yang jadi gerbang eksekusi (allow/block). Policy Administrator (PA) di tengah, menyampaikan keputusan PE ke PEP.
2. **Gap Analysis** (technical/compliance gap analysis) — membandingkan kondisi sekarang (current state) vs standar yang dituju (desired state/ISO 27001).
3. **Backout plan** — rencana rollback kalau perubahan gagal/bermasalah.

---

## ✅ Domain 1: General Security Concepts — SELESAI (12%)

Lanjut ke **Domain 2: Threats, Vulnerabilities & Mitigations (22%)** di file terpisah: `Latihan-Soal-Domain2.md`.
