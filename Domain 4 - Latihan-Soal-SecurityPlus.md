# CompTIA Security+ (SY0-701) — Domain 4: Latihan Soal

Cara pakai: jawab dulu semua soal SEBELUM scroll ke bagian "Jawaban & Pembahasan".

---

## Hardening, Mobile Device Security, Application Security

### Soal
1. Perusahaan membelikan laptop untuk karyawan, tapi karyawan boleh juga pakai laptop itu buat keperluan pribadi di luar jam kerja. Ini model deployment apa?
2. Tim security menganalisis source code aplikasi sebelum di-deploy ke production, mencari pola kode yang berpotensi vulnerable, tanpa menjalankan aplikasinya sama sekali. Ini teknik apa?
3. Analis malware menjalankan file mencurigakan di lingkungan terisolasi khusus untuk mengamati perilakunya tanpa risiko menginfeksi sistem asli. Ini teknik apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **COPE** (Corporate-Owned, Personally Enabled).
2. **SAST** (Static Application Security Testing).
3. **Sandboxing**.

---

## Asset Management & Vulnerability Management

### Soal
1. Sebuah scanner otomatis melaporkan bahwa server X punya vulnerability kritis, tapi setelah dicek manual ternyata itu keliru. Ini contoh apa?
2. Laptop lama mau didonasikan ke sekolah — datanya dihapus menyeluruh, tapi laptopnya sendiri tetap utuh. Ini contoh apa?
3. Sebutkan istilah untuk "nama/ID resmi vulnerability" dan "skor 0-10 keparahannya".
4. Peneliti keamanan melaporkan celah secara privat ke perusahaan, kasih waktu 90 hari sebelum publikasi. Ini contoh apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **False positive**.
2. **Sanitization**.
3. **CVE** (nama/ID), **CVSS** (skor keparahan).
4. **Responsible disclosure**.

---

## Alerting/Monitoring Tools & Enterprise Security Capabilities

### Soal
1. Sistem keamanan mendeteksi serangan berdasarkan pola yang sudah tercatat sebelumnya — serangan baru dengan pola belum tercatat kemungkinan besar lolos. Ini metode deteksi apa?
2. Karyawan yang biasanya login jam 8 pagi dari Jakarta, tiba-tiba login jam 2 pagi dari luar negeri dan akses banyak file sensitif gak biasa. Sistem apa yang mendeteksi ini?
3. Alat keamanan mengkorelasikan data dari jaringan, cloud, dan email sekaligus, bukan cuma endpoint. EDR atau XDR?
4. Sebelum laptop baru boleh konek ke jaringan kantor, sistem cek dulu antivirus & patch OS-nya. Kalau belum, ditolak. Ini contoh apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Signature-based**.
2. **UBA** (User Behavior Analytics).
3. **XDR**.
4. **NAC** (Network Access Control).

---

## Identity & Access Management (IAM)

### Soal
1. Website e-commerce punya tombol "Login pakai akun Google" — user langsung masuk pakai identitas Google tanpa bikin akun baru. SSO atau Federation?
2. Rumah sakit menetapkan rekam medis pasien hanya bisa diakses sistem berlabel "Medical Staff" yang ditentukan administrator — user gak bisa ubah label itu sendiri. Access control model apa?
3. Karyawan cuma boleh login ke sistem finance jam 8 pagi - 5 sore. Access control model apa?
4. User login pakai password + fingerprint scan. Apakah ini MFA yang valid? Jelaskan.

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Federation**.
2. **MAC** (Mandatory) — sinyal kuncinya: label ditentukan admin/sistem, user gak bisa ubah sendiri.
3. **Rule-based** (time-of-day restriction).
4. **Valid** — password (something you know) + fingerprint (something you are) = 2 kategori faktor berbeda.

---

## Incident Response, Automation/Orchestration, Data Sources

### Soal
1. Tim IT baru saja mengisolasi server terinfeksi ransomware dari jaringan, tapi ransomware-nya belum dihapus. Tahap IR apa?
2. Setelah insiden phishing ditangani, tim menyelidiki kenapa email phishing bisa lolos filter spam. Ini contoh aktivitas apa?
3. Platform otomatis menjalankan isolasi device + notifikasi tim + buka tiket begitu terdeteksi malware, tanpa dikerjakan manual 1-1. Konsep apa?
4. Investigator butuh melihat isi lengkap paket data saat serangan, bukan cuma metadata koneksi. Data source apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Containment** (belum Eradication).
2. **Root Cause Analysis**.
3. **SOAR** (Security Orchestration, Automation, and Response).
4. **Packet Capture (PCAP)**.

---

## ✅ Domain 4: Security Operations — SELESAI (28%)

Lanjut ke **Domain 5: Security Program Management and Oversight (20%)** — domain terakhir!