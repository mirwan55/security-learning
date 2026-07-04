# CompTIA Security+ (SY0-701) — Domain 3: Security Architecture (18%)

File lanjutan dari Domain 1 & 2. Simbol 🔑 = mnemonic/jembatan keledai.

---

### Architecture Models

#### A. Cloud Service Models & Shared Responsibility
| Model | Yang dikelola provider | Yang dikelola kamu (customer) |
|---|---|---|
| **IaaS** | Hardware, jaringan, virtualisasi | OS, aplikasi, data, konfigurasi |
| **PaaS** | Hardware s/d runtime/OS | Aplikasi & data saja |
| **SaaS** | Hampir semuanya | Data & manajemen akses user saja |

🔑 Makin ke kanan (IaaS → PaaS → SaaS), makin sedikit yang perlu diurus, makin banyak diurus provider. Tapi **data & akses user SELALU jadi tanggung jawab customer**, di model apa pun.

- **Hybrid cloud** — kombinasi on-premises + cloud
- **Multi-cloud** — pakai lebih dari 1 provider cloud (hindari vendor lock-in)

#### B. Virtualization vs Containerization
| | Virtualization (VM) | Containerization |
|---|---|---|
| Isolasi | Tiap VM punya OS sendiri (hypervisor) | Semua container berbagi 1 kernel OS host |
| Risiko | **VM escape** — kabur ke hypervisor | **Container escape** — kabur ke kernel host (dampak lebih luas) |

#### C. Infrastructure as Code (IaC)
Infrastruktur didefinisikan lewat kode/config (Terraform), bisa di-version-control. ⚠️ Risiko: kesalahan template ter-replikasi ke semua tempat sekaligus.

#### D. Serverless
Provider yang handle semua provisioning (AWS Lambda), bayar cuma pas kode dieksekusi.

#### E. Microservices vs Monolithic
Microservices = dipecah jadi service kecil independen via API — lebih tahan banting, tapi attack surface lebih besar.

#### F. Network Architecture Concepts
- **Physical isolation/Air-gapped** — terputus fisik dari jaringan lain, paling aman
- **Logical segmentation** (VLAN) — dipisah virtual walau infra fisik sama
- **SDN (Software-Defined Networking)** — pisahkan control plane dari data plane, manajemen terpusat via software

---

### Infrastructure Security: Device Placement, Network Appliances, Firewall

#### A. Security Zones
**Screened subnet (DMZ)** — zona penyangga antara internet dan jaringan internal, tempat naruh server publik (web/mail server). Kalau kena hack, internal tetap aman.

#### B. Network Appliances
- **Jump server** — server hardened, satu-satunya pintu masuk terkontrol buat **admin** akses ke server di zona aman
- **Forward proxy** vs **Reverse proxy**:
  | | Melindungi siapa | Fungsi |
  |---|---|---|
  | Forward proxy | Client internal | Filter traffic **keluar** ke internet |
  | Reverse proxy | Server backend | Filter traffic **masuk** dari internet, sering sekalian load balancing |
- **Load balancer** — bagi traffic ke banyak server (availability & performance)
- **IDS vs IPS**:
  | | IDS | IPS |
  |---|---|---|
  | Aksi | Deteksi & alert saja | Deteksi + blokir langsung |
  | Posisi | Out-of-band | Inline |

🔑 **DMZ** = soal penempatan/isolasi server publik. **Jump server** = soal kontrol akses admin. Jangan ketuker.
🔑 **Forward proxy** = lindungi yang di dalam pas **keluar**. **Reverse proxy** = lindungi yang di dalam pas ada yang **masuk**.
🔑 **IDS** = detektif (cuma lapor). **IPS** = satpam (langsung bertindak).

#### C. Firewall Types (makin canggih ke bawah)
Packet-filtering (Layer 3/4, cek header) → Stateful (ingat konteks koneksi) → NGFW (Layer 7, app-aware) → WAF (khusus lindungi web app dari SQLi/XSS)

#### D. Port Security
- **802.1X** — NAC berbasis port, device harus autentikasi dulu sebelum dapat akses jaringan
- **EAP** — framework metode autentikasi yang dipakai bareng 802.1X

#### E. Secure Communication/Access
- **VPN**: Site-to-site (2 kantor) vs Remote-access (1 user)
- **SD-WAN** — kelola WAN pakai software, rute traffic pintar
- **SASE** — gabungan SD-WAN + layanan security jadi 1 layanan cloud

---

### Data Protection Concepts

#### A. Data States
At rest (disk/DB, lindungi: encryption) → In transit (jaringan, lindungi: TLS/VPN) → In use (memory, lindungi: secure enclave). Data paling rentan saat **in use** karena harus plaintext buat diproses.

#### B. Data Classifications
Public → Private/Internal → Sensitive → Confidential → Critical/Restricted

#### C. Metode Melindungi Data

**Encryption vs Hashing:**
| | Encryption | Hashing |
|---|---|---|
| Reversible? | Ya, pakai key | Tidak, one-way |
| Tujuan | Confidentiality | Integrity |

🔑 Encryption = amplop tersegel (bisa dibuka lagi). Hashing = sidik jari (cuma buat verifikasi, gak bisa balik ke orangnya).

**Masking vs Tokenization:**
| | Masking | Tokenization |
|---|---|---|
| Cara kerja | Sebagian data disembunyikan permanen dari tampilan | Data diganti token, bisa dipetakan balik lewat token vault |
| Contoh | Tampilan nomor kartu di struk | Sistem pembayaran (PCI DSS) |

🔑 Masking = coret sebagian biar gak kelihatan. Tokenization = tuker jadi "kupon", aslinya aman di tempat lain.

- **Obfuscation** — bikin data/kode susah dipahami manusia
- **DLP (Data Loss Prevention)** — deteksi & cegah data sensitif keluar organisasi tanpa izin

#### D. Data Sovereignty & Geolocation
**Data sovereignty** — data tunduk hukum negara asalnya meski disimpan di negara lain (misal data EU tetap kena GDPR meski diproses perusahaan Indonesia).

---

### Resilience & Recovery

#### A. Site Considerations
| Site | Kesiapan | Kecepatan | Biaya |
|---|---|---|---|
| **Hot site** | Duplikat penuh, siap langsung | Tercepat | Termahal |
| **Warm site** | Sebagian disiapkan | Sedang | Sedang |
| **Cold site** | Cuma infra dasar | Terlambat | Termurah |

🔑 Analogi suhu = kecepatan siap pakai.

#### B. Konsep Pendukung
High Availability (HA), Platform diversity (hindari 1 titik kegagalan), Multi-cloud, Continuity of Operations (COOP), Capacity planning

#### C. Testing Exercises
Tabletop exercise (diskusi doang, paling "aman") → Failover test (beneran switch ke backup) → Simulation → Parallel processing test (backup jalan bareng primary tanpa ganggu)

#### D. Backup Concepts
- **Snapshot** — foto kondisi di 1 titik waktu
- **Replication** — data terus disalin real-time ke lokasi lain
- **Journaling** — catat tiap transaksi berurutan, recovery presisi ke waktu tertentu
- Onsite vs Offsite backup

#### E. Power Resilience
**UPS** — backup listrik jangka pendek (jembatani sampai shutdown aman/generator nyala). **Generator** — backup jangka panjang.

---

## ✅ Domain 3: Security Architecture — SELESAI (18%)
Ringkasan: Architecture Models (cloud, virtualization, IaC), Infrastructure Security (DMZ, proxy, IDS/IPS, firewall), Data Protection (encryption/hashing, masking/tokenization), Resilience & Recovery (site types, backup, power).
