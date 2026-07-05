# CompTIA Security+ (SY0-701) — Domain 4: Security Operations (28%)

File lanjutan dari Domain 1-3. Simbol 🔑 = mnemonic/jembatan keledai.

---

### Hardening, Mobile Device Security, Application Security

#### A. Secure Baseline & Hardening
**Secure baseline** — konfigurasi standar yang sudah diuji, jadi fondasi sebelum sistem dipakai (bukan default pabrik).
**Hardening**: disable service/port gak perlu, ganti password default, patching rutin, host-based firewall/IPS, endpoint protection.
Target: workstation, server, mobile device, switch/router, cloud infra, IoT/embedded, ICS/SCADA.

#### B. Mobile Device Deployment Models
| Model | Siapa yang punya device | Kontrol perusahaan |
|---|---|---|
| **BYOD** | Karyawan (pribadi) | Paling rendah |
| **COPE** | Perusahaan | Tinggi, boleh dipakai personal |
| **CYOD** | Perusahaan | Tinggi, karyawan pilih dari daftar approved |

🔑 Urutan kontrol (rendah→tinggi): **BYOD < CYOD < COPE**.

MDM biasanya sediakan: remote wipe, full-device encryption, containerization, geofencing.

#### C. Application Security Testing
| | SAST (Static) | DAST (Dynamic) |
|---|---|---|
| Cara kerja | Analisis source code, tanpa dijalankan | Tes aplikasi yang sedang berjalan |
| Kapan | Awal SDLC | Setelah aplikasi jalan |

🔑 **SAST** = cek **S**ourcecode. **DAST** = **D**ijalanin dulu baru dites.

#### D. Sandboxing
Jalankan kode/aplikasi di lingkungan terisolasi buat observasi aman (analisis malware, uji aplikasi belum dipercaya).

---

### Asset Management & Vulnerability Management

#### A. Asset Management Lifecycle
Acquisition/Procurement → Assignment/Accounting → Monitoring → Disposal/Decommissioning

**Disposal — 3 istilah:**
| Istilah | Penjelasan |
|---|---|
| **Sanitization** | Data dihapus, hardware masih bisa dipakai lagi |
| **Destruction** | Media dihancurkan fisik, gak bisa dipakai lagi |
| **Certification** | Dokumen bukti data sudah disanitasi/dihancurkan benar |

🔑 Sanitization = "cuci bersih, barang masih ada". Destruction = "barangnya ikut hancur".

#### B. Vulnerability Management — Identification
| Metode | Penjelasan |
|---|---|
| **Vulnerability scan** | Tool otomatis, cari vulnerability yang sudah diketahui |
| **Penetration testing** | Simulasi serangan manual/mendalam |
| **Bug bounty** | Bayar researcher yang temukan & lapor |
| **Responsible disclosure** | Lapor privat ke vendor dulu, kasih waktu patch sebelum publikasi |

#### C. Analysis
- **False positive** — dilaporkan vulnerable padahal sebenarnya aman (alarm palsu)
- **False negative** — gagal deteksi vulnerability yang sebenarnya ada (lebih berbahaya)

**CVE vs CVSS:**
| | CVE | CVSS |
|---|---|---|
| Fungsi | Identifier/nama standar vulnerability | Skor keparahan (0-10) |

🔑 CVE = "apa nama/ID-nya". CVSS = "seberapa parah dia".

#### D. Response & Remediation
Patching, segmentation, compensating controls, cyber insurance, exception/exemption (terima risiko formal). Setelah remediasi, **validasi** (rescan, audit) buat mastiin celah tertutup.

---

### Alerting/Monitoring Tools & Enterprise Security Capabilities

#### A. Monitoring Tools
**SIEM** — kumpulkan log dari seluruh sumber, korelasikan, beri alert. 🔑 "Pusat komando".

**Agent-based vs Agentless:** Agent-based = software terpasang di endpoint (detail, berat). Agentless = pakai protokol/API yang ada (ringan, kurang detail).

**NetFlow** — metadata traffic jaringan (siapa-ke-siapa), bukan isi paket penuh.
**SCAP** — standar otomasi pengecekan compliance/vulnerability, dipakai bareng **benchmark** (CIS Benchmark).

#### B. Enterprise Security Capabilities
**Deteksi IDS/IPS:**
| Metode | Cara kerja |
|---|---|
| **Signature-based** | Cocokkan pola yang sudah dikenal — cepat, tapi gak bisa deteksi ancaman baru |
| **Anomaly/Behavior-based** | Deteksi penyimpangan dari baseline normal — bisa nangkep ancaman baru, tapi rawan false positive |

**NAC** — device harus patuh kebijakan (antivirus update, patch) sebelum diizinkan masuk jaringan.

**EDR vs XDR:**
| | EDR | XDR |
|---|---|---|
| Cakupan | Cuma endpoint | Diperluas: endpoint + jaringan + cloud + email |

🔑 XDR = EDR yang "di-extend".

**UBA (User Behavior Analytics)** — analisis pola perilaku user buat deteksi anomali.

---

### Identity & Access Management (IAM)

#### A. Siklus Hidup Identitas
Provisioning (buat akun) → De-provisioning (cabut akses saat offboarding). **Identity proofing** — verifikasi identitas sebelum dikasih kredensial. **Attestation** — review berkala memastikan akses masih sesuai kebutuhan.

#### B. SSO vs Federation
| | SSO | Federation |
|---|---|---|
| Cakupan | 1 login, banyak sistem **dalam 1 organisasi** | Identitas 1 organisasi dipercaya **organisasi lain** |

🔑 SSO = 1 kunci buka banyak pintu di rumah sendiri. Federation = kuncimu dipercaya buka pintu rumah tetangga.

#### C. Access Control Models
| Model | Siapa yang nentuin | Contoh |
|---|---|---|
| **MAC** (Mandatory) | Sistem, via label/klasifikasi — user gak bisa ubah | Sistem militer (Top Secret) |
| **DAC** (Discretionary) | Pemilik resource | User atur sendiri share folder |
| **RBAC** (Role-Based) | Peran/jabatan | Role HR dapat akses sistem HR |
| **Rule-Based** | Aturan spesifik admin | Akses cuma jam kerja |
| **ABAC** (Attribute-Based) | Kombinasi banyak atribut | Role + device + waktu sekaligus |

⚠️ Sinyal "label/klasifikasi yang gak bisa diubah pemilik data sendiri" → **MAC**, bukan RBAC (meski nama label kedengaran seperti peran).

#### D. MFA — 5 kategori faktor
Something you know (password), have (token/HP), are (biometric), somewhere you are (lokasi), something you do (perilaku).

🔑 MFA sejati = minimal 2 faktor dari **kategori berbeda**. Password + PIN = bukan MFA (sama-sama "know").

---

### Incident Response, Automation/Orchestration, Data Sources

#### A. Incident Response Process (7 tahap, urutan penting!)
Preparation → Detection → Analysis → Containment → Eradication → Recovery → Lessons learned

🔑 **Mnemonic:** "Pak Dedi Anak Cerdas Emang Rajin Lho" (P-D-A-C-E-R-L)

⚠️ Urutan gak boleh dibolak-balik — isolasi = Containment, hapus ancamannya = Eradication (beda tahap).

**Root Cause Analysis** — cari akar masalah, bukan cuma gejala. **Threat hunting** — proaktif cari ancaman yang lolos deteksi otomatis.

#### B. Automation & Orchestration
**Automation** = 1 tugas otomatis. **Orchestration** = koordinasi banyak automation jadi 1 alur kerja. **SOAR** = platform yang gabungkan automation + orchestration + response.

#### C. Data Sources for Investigation
Log data: firewall, application, endpoint, OS security log, IDS/IPS log.

| | PCAP | NetFlow |
|---|---|---|
| Detail | Isi penuh paket | Metadata koneksi saja |
| Beban | Berat | Ringan |

---

## ✅ Domain 4: Security Operations — SELESAI (28%)

Lanjut ke **Domain 5: Security Program Management and Oversight (20%)** — domain terakhir!