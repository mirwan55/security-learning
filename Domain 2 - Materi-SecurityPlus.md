# CompTIA Security+ (SY0-701) — Domain 2: Threats, Vulnerabilities & Mitigations (22%)

File lanjutan dari `Materi-SecurityPlus.md` (Domain 1). Simbol 🔑 = mnemonic/jembatan keledai.

---

### Hari 1 (2 Juli 2026) — Threat Actors & Motivations

#### Jenis-jenis Threat Actor

| Actor | Motivasi utama | Sophistication/Resource |
|---|---|---|
| **Nation-state** | Espionase, keuntungan politik/militer, sabotase | Sangat tinggi — didanai negara, sering disebut **APT** (Advanced Persistent Threat) |
| **Organized crime** | Uang (finansial) | Tinggi — beroperasi kayak bisnis, contoh: gang ransomware |
| **Hacktivist** | Isu politik/sosial, ideologi | Sedang — targetnya organisasi yang "melawan" keyakinan mereka |
| **Insider threat** | Balas dendam, keuntungan pribadi, atau **gak sengaja** (kelalaian) | Bervariasi — tapi punya akses legit, jadi berbahaya meski skill rendah |
| **Unskilled attacker** (script kiddie) | Sensasi, pengakuan/eksistensi | Rendah — pakai tools/script yang udah jadi |
| **Shadow IT** | Bukan niat jahat — cuma cari kepraktisan (pakai app/sistem gak resmi) | N/A — tapi jadi celah keamanan besar karena di luar pantauan IT |

🔑 **Mnemonic urutan sophistication (rendah → tinggi):** Script kiddie < Hacktivist ≈ Insider < Organized crime < Nation-state.

⚠️ **Poin penting:**
- **Insider threat** ada 2 jenis: **malicious** (sengaja — revenge/uang) dan **unintentional/negligent** (gak sengaja, misal kena phishing). Keduanya tetap disebut insider threat karena aksesnya legit/orang dalam.
- **Nation-state** identik dengan istilah **APT (Advanced Persistent Threat)** — serangan sabar, jangka panjang, susah dideteksi, biasanya untuk espionase.
- **Shadow IT** bukan "penyerang", tapi jadi **attack surface** tambahan yang gak diawasi tim security.

#### Atribut Threat Actor
- **Internal vs External** — orang dalam vs luar organisasi
- **Resources/funding** — level pendanaan
- **Level of sophistication/capability** — kemampuan teknis

---

### Hari 2 (2 Juli 2026) — Threat Vectors & Attack Surfaces

**Definisi:**
- **Threat vector** — jalur/cara spesifik yang dipakai attacker buat masuk
- **Attack surface** — keseluruhan titik yang berpotensi bisa dieksploitasi (gabungan semua vector)

🔑 Analogi: attack surface = semua pintu+jendela rumah, threat vector = jalur spesifik yang dipakai maling masuk.

**1. Berbasis pesan/komunikasi:** Email (phishing), SMS (smishing), Voice call (vishing), IM, Image-based (steganography), File-based (attachment berbahaya)

**2. Berbasis device & jaringan:** Removable device (baiting via USB), Unsecure network (wireless/Bluetooth lemah), Open service ports, Default credentials

**3. Berbasis software:** Vulnerable software (belum di-patch), Unsupported systems/applications (EOL)

**4. Supply chain (sering muncul di soal!):** Vendor/partner/third-party yang punya akses ke sistem kita — kalau mereka dikompromis, attacker masuk lewat "pintu belakang". Contoh nyata: kasus SolarWinds (malware disusupkan ke update resmi sebelum dirilis ke pelanggan).

🔑 **Mnemonic kelompok:** Message → Device/Network → Software → Supply chain.

⚠️ **Poin penting — Supply chain vs Vulnerable software (sering ketuker):**
- **Vulnerable software** = attacker exploit celah/bug yang memang ada di software (bisa dicegah dengan rajin patching)
- **Supply chain** = malware **sudah disusupkan ke dalam update/produk resmi itu sendiri, sebelum sampai ke korban** — korban tetap kena meskipun rajin patching, karena yang "resmi"-nya sendiri sudah beracun

⚠️ **Default credentials** kelihatan sepele tapi penyebab breach paling umum di real world (router/IoT yang gak pernah diganti password default).

---

### Hari 3 (2 Juli 2026) — Types of Vulnerabilities

#### A. Web/Application-based (paling nyambung ke background SQL/coding)

**SQL Injection (SQLi)** — menyisipkan perintah SQL ke input yang gak divalidasi buat memanipulasi query.
Contoh: `' OR '1'='1` atau `admin' --` di form login → bypass authentication.
Mitigasi: **parameterized queries/prepared statements**, input validation.

**Cross-Site Scripting (XSS)** — menyisipkan script (biasanya JS) yang dieksekusi di browser user lain.
| Jenis | Penjelasan |
|---|---|
| **Stored XSS** | Script tersimpan permanen di server (misal kolom komentar), kena semua pengunjung |
| **Reflected XSS** | Script dikirim lewat URL/request, dipantulkan balik ke response — gak tersimpan |
| **DOM-based XSS** | Manipulasi terjadi di sisi client (browser), gak perlu ke server |

Mitigasi: output encoding, input sanitization, Content Security Policy (CSP).

🔑 **SQLi** menyerang **database** lewat query. **XSS** menyerang **browser user lain** lewat script.

**Buffer Overflow** — data melebihi kapasitas buffer, overwrite memory di sebelahnya, berpotensi eksekusi kode arbitrary.
Mitigasi: bounds checking, bahasa memory-safe, ASLR.

**Race Condition (TOC/TOU — Time-of-Check to Time-of-Use)** — jeda waktu antara sistem **mengecek** kondisi dan **memakai** hasil cek; attacker menyisip di jeda itu buat mengubah kondisi.
Contoh: cek saldo cukup → sebelum transaksi diproses, attacker kirim transaksi lain di jeda itu → dua-duanya lolos padahal saldo cuma cukup 1x.

🔑 **Buffer overflow** = soal **ukuran/kapasitas**. **Race condition** = soal **waktu/timing**.

#### B. Misconfiguration
Pengaturan default/salah konfigurasi — permission kebuka lebar, port gak perlu aktif, fitur default lupa di-disable.

#### C. Zero-day
Vulnerability yang **belum diketahui vendor** atau **belum ada patch resmi**, meski sudah dieksploitasi di luar sana. Mitigasi sementara: workaround, deteksi anomali perilaku.

#### D. Sekilas: Hardware, Legacy/EOL, Virtualization
- **Hardware vulnerability** — kerentanan di level firmware
- **Legacy/EOL** — sistem gak didukung vendor lagi, gak dapat patch
- **Virtualization (VM escape)** — attacker "kabur" dari VM terisolasi, dapat akses ke hypervisor/VM lain

---

### Hari 4 (2 Juli 2026) — Malware Types (Indicators of Malicious Activity)

| Malware | Ciri khas | Butuh host file? | Butuh aksi user? |
|---|---|---|---|
| **Virus** | Menempel ke program/file legit, aktif kalau file-nya dijalankan | ✅ Ya | ✅ Ya |
| **Worm** | Menyebar sendiri lewat jaringan, gak butuh host file maupun aksi user | ❌ Tidak | ❌ Tidak |
| **Trojan** | Menyamar jadi software legit, gak self-replicate, andalkan tipu daya user buat diinstall | ❌ Tidak | ✅ Ya (install) |
| **Ransomware** | Mengenkripsi data, minta tebusan | — | — |
| **Spyware** | Diam-diam memantau/mengumpulkan info user | — | — |
| **Keylogger** | Merekam ketikan keyboard (subset dari spyware) | — | — |
| **Logic bomb** | Kode jahat yang "tidur" sampai kondisi/trigger tertentu terpenuhi | — | — |
| **Rootkit** | Fokus menyembunyikan diri & mempertahankan akses level tinggi (root/admin), susah dideteksi | — | — |
| **Bot/Botnet** | Komputer dikuasai attacker dari jarak jauh, dikendalikan lewat **C2 (Command and Control) server**, dipakai buat DDoS/spam massal | — | — |

🔑 **Virus vs Worm (paling sering ketuker):** Virus = "penumpang gelap", nebeng di file dan baru jalan kalau **file-nya dibuka user**. Worm = "jalan sendiri", nyebar otomatis lewat jaringan **tanpa butuh host file maupun aksi user** — ini pembeda kuncinya, bukan sekadar "tanpa aksi user" tapi juga **tanpa nebeng ke file apa pun**.

🔑 **Trojan** = "menyamar" (Kuda Troya) — menipu user buat install, bukan self-replicate.
🔑 **Rootkit** = "root" level akses + "kit" alat buat sembunyi.

⚠️ **Logic bomb** klasik dikaitkan sama **insider threat** (misal karyawan IT yang mau dipecat nanam kode trigger). **Botnet** selalu dikaitkan sama istilah **C2 (Command and Control)**.

---

### Hari 5 (2 Juli 2026) — Network/Password Attack Indicators + Mitigation Techniques

#### A. Network Attack Indicators
| Serangan | Penjelasan |
|---|---|
| **DNS poisoning/spoofing** | Merusak/memalsukan record DNS supaya user diarahkan ke situs palsu |
| **On-path attack** (dulu MITM) | Attacker menyusup di tengah komunikasi 2 pihak |
| **Evil twin** | AP WiFi palsu yang meniru nama AP asli |
| **Credential replay** | Menangkap token/kredensial sah, dipakai ulang seolah user asli |

#### B. Password Attacks (paling sering ketuker!)
| Serangan | Target | Cara kerja |
|---|---|---|
| **Brute force** | 1 akun | Coba **semua kemungkinan kombinasi** |
| **Dictionary attack** | 1 akun | Coba password dari **daftar kata umum** |
| **Password spraying** | **Banyak akun** | Coba **1 password umum** ke banyak akun sekaligus (hindari lockout) |
| **Credential stuffing** | Banyak akun, situs lain | Pakai kombo username/password **bocoran dari breach situs lain** |

🔑 **Kunci pembeda:** target 1 akun vs banyak akun, dan generate sendiri vs pakai data bocoran.

#### C. Physical Attack Indicators (singkat)
- **Brute force (fisik)** — merusak paksa kunci/pintu
- **RFID cloning** — menduplikasi kartu akses/badge

#### D. Mitigation Techniques
| Teknik | Penjelasan |
|---|---|
| **Segmentation** | Pisah jaringan jadi beberapa bagian, biar serangan gak menyebar |
| **Access control** | Least privilege — akses seminimal mungkin sesuai kebutuhan |
| **Application allow list/deny list** | Cuma app yang di-approve boleh jalan / blokir yang diketahui jahat |
| **Isolation** | Pisahkan sistem yang kena infeksi dari jaringan |
| **Patching** | Update rutin buat nutup vulnerability |
| **Encryption** | Lindungi data biar gak berguna kalau kecuri |
| **Monitoring** | Pantau aktivitas buat deteksi dini |
| **Hardening** | Disable port/protokol gak perlu, ganti password default, uninstall software gak perlu, pasang host-based firewall/IPS |
| **Decommissioning** | Pensiunkan sistem lama dengan benar (data dihapus aman) |

🔑 Hampir semua mitigation adalah **kebalikan langsung** dari vulnerability/vector yang sudah dibahas — kalau paham vulnerability-nya, mitigasinya biasanya masuk akal secara logis.

---

## ✅ Domain 2: Threats, Vulnerabilities & Mitigations — SELESAI (22%)
Ringkasan: Threat Actors, Threat Vectors & Attack Surfaces, Types of Vulnerabilities, Malware Types, Network/Password/Physical Attack Indicators, Mitigation Techniques.

Lanjut ke **Domain 3: Security Architecture (18%)** di file terpisah.
