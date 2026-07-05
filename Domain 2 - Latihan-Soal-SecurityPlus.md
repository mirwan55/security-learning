# CompTIA Security+ (SY0-701) — Domain 2: Latihan Soal

---

## Hari 1 — Threat Actors & Motivations

### Soal
1. Sebuah rumah sakit diserang oleh grup yang mengenkripsi seluruh data pasien dan minta tebusan dalam Bitcoin. Grup ini terorganisir dan tampak sudah berpengalaman melakukan ini berkali-kali ke korban lain. Threat actor jenis apa ini?
2. Seorang karyawan gak sengaja mengklik link phishing dan tanpa sadar memberikan kredensialnya ke attacker. Apakah karyawan ini termasuk "insider threat"? Jelaskan alasannya.
3. Sebuah negara diduga menyusup ke jaringan infrastruktur listrik negara lain secara diam-diam selama bertahun-tahun untuk mengumpulkan informasi tanpa terdeteksi. Threat actor jenis apa, dan istilah apa yang biasa dipakai buat jenis serangan jangka panjang seperti ini?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Organized crime** — ransomware minta tebusan Bitcoin, terorganisir, berpengalaman = ciri khas Organized crime yang finansial-motivated.
2. **Ya, termasuk insider threat — tapi jenis unintentional/negligent**, bukan malicious. Insider threat gak selalu disengaja; karena aksesnya legit (orang dalam), kelalaian pun tetap masuk kategori ini.
3. **Nation-state**, tujuan spionase. Istilah untuk serangan jangka panjang & diam-diam seperti ini: **APT (Advanced Persistent Threat)**.

---

## Hari 2 — Threat Vectors & Attack Surfaces

### Soal
1. Sebuah perusahaan software ternama merilis update resmi yang ternyata sudah disusupi malware oleh attacker sebelum dirilis ke pelanggan. Ribuan perusahaan yang pakai software ini pun ikut terinfeksi. Ini contoh threat vector apa?
2. Seorang karyawan menemukan flashdisk tergeletak di tempat parkir kantor, penasaran, lalu colokin ke laptop kerjanya. Ini contoh threat vector apa?
3. Ada kamera CCTV IoT yang dipasang di kantor, tapi tim IT lupa ganti password bawaan pabriknya. Attacker berhasil masuk lewat kamera itu. Ini contoh threat vector apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Supply chain**, bukan vulnerable software. Malware sudah disusupkan ke dalam update resmi **sebelum** sampai ke pelanggan — beda dengan vulnerable software (attacker exploit celah yang memang ada, bisa dicegah dengan patching). Di kasus supply chain, korban tetap kena meski rajin patching, karena yang "resmi"-nya sendiri sudah beracun.
2. **Removable device (baiting)**.
3. **Default credentials**.

---

## Hari 3 — Types of Vulnerabilities

### Soal
1. Form login sebuah website ternyata menerima input `admin' --` di kolom username dan berhasil login tanpa password yang benar. Ini contoh vulnerability apa?
2. Attacker menaruh script jahat di kolom komentar sebuah artikel blog. Setiap pengunjung yang membuka artikel itu otomatis kena script tersebut. Ini contoh vulnerability apa (sebutkan jenis spesifiknya juga)?
3. Sebuah aplikasi banking mengecek saldo user dulu sebelum memproses penarikan — tapi ada jeda beberapa milidetik antara pengecekan dan eksekusi. Attacker mengirim 2 request penarikan bersamaan di jeda itu, dan berhasil menarik uang 2x padahal saldo cuma cukup 1x. Ini contoh vulnerability apa?
4. Sebuah vendor software menemukan ada celah di produknya yang ternyata sudah dieksploitasi attacker di luar sana, padahal vendor sendiri belum pernah tau soal celah itu dan belum sempat bikin patch-nya. Ini contoh vulnerability apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **SQL Injection** — `admin' --` teknik klasik buat "comment out" sisa query password check.
2. **Cross-Site Scripting (XSS)**, jenis **Stored XSS** — script nempel permanen di server (kolom komentar), kena semua pengunjung.
3. **Race Condition (TOC/TOU — Time-of-Check to Time-of-Use)**.
4. **Zero-day**.

---

## Hari 4 — Malware Types

### Soal
1. Sebuah file Excel ber-macro dikirim via email. Kalau user membuka file dan mengaktifkan macro-nya, kode jahat di dalamnya baru akan berjalan dan menyebar ke file lain di komputer yang sama. Malware jenis apa ini?
2. Sebuah worm menyebar sendiri ke ribuan komputer dalam hitungan jam tanpa ada satupun user yang mengklik apa pun. Kenapa ini bisa terjadi tanpa aksi user (beda dari virus)?
3. Seorang mantan admin IT yang dipecat ternyata sudah menanam kode sebelumnya: "kalau username saya dihapus dari sistem HR, maka format semua database perusahaan." Ini contoh malware jenis apa?
4. Ribuan komputer yang terinfeksi malware yang sama tiba-tiba mengirim traffic secara bersamaan ke satu website target, menyebabkan website itu down. Semua komputer itu dikendalikan dari satu server yang sama. Ini contoh apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Virus** — butuh file dijalankan dulu (aksi user) baru aktif.
2. **Worm** — bisa menyebar tanpa aksi user karena worm **tidak butuh host file sama sekali** (beda dari virus yang butuh nebeng di file). Worm langsung mengeksploitasi celah jaringan/sistem secara otomatis, bukan "menggunakan host".
3. **Logic bomb** — kode tidur menunggu kondisi/trigger tertentu (username dihapus), pola klasik terkait insider threat.
4. **Botnet** (dikendalikan lewat C2 server) — traffic bersamaan ke 1 target = serangan DDoS yang dilancarkan lewat botnet.

---

## Hari 5 — Network/Password Attack Indicators + Mitigation Techniques

### Soal
1. Attacker mencoba password `Winter2024!` ke 500 akun karyawan berbeda sekaligus, masing-masing akun cuma dicoba 1x biar gak kena sistem lockout. Ini contoh serangan apa?
2. Attacker punya database bocoran username+password dari kebocoran data situs e-commerce tahun lalu, terus dia coba pakai kombo yang sama itu buat login ke akun email korban. Ini contoh serangan apa?
3. User connect ke WiFi "Kantor_Free_WiFi" yang ternyata bukan AP resmi kantor, tapi buatan attacker yang sengaja menyamar. Ini contoh serangan apa?
4. Sebuah perusahaan memisahkan jaringan untuk device IoT dari jaringan utama karyawan, jadi kalau salah satu device IoT kena malware, gak bisa langsung nyebar ke laptop karyawan. Ini contoh mitigation technique apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Password spraying** — 1 password ke banyak akun, hindari lockout.
2. **Credential stuffing** — kombo bocoran dipakai ulang di situs lain.
3. **Evil twin** — AP palsu yang menyamar jadi AP resmi.
4. **Segmentation** — pisah jaringan biar serangan gak menyebar.

---

## ✅ Domain 2: Threats, Vulnerabilities & Mitigations — SELESAI (22%)
