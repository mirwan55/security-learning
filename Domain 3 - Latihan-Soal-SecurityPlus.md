# CompTIA Security+ (SY0-701) — Domain 3: Latihan Soal

Cara pakai: jawab dulu semua soal SEBELUM scroll ke bagian "Jawaban & Pembahasan".

---

## Hari 1 — Architecture Models

### Soal
1. Perusahaan pakai layanan email berbasis cloud (misal Google Workspace) dan gak perlu ngurus server/OS sama sekali, tinggal pakai aplikasinya. Ini model cloud apa, dan siapa yang tetap bertanggung jawab atas keamanan datanya?
2. Sebuah sistem kontrol SCADA di pabrik sengaja tidak disambungkan ke jaringan internet maupun jaringan kantor sama sekali demi keamanan maksimal. Ini contoh konsep apa?
3. Tim DevOps mendefinisikan seluruh konfigurasi server lewat file Terraform yang di-commit ke git, bukan diklik manual. Suatu hari ada kesalahan kecil di template tersebut dan ter-deploy ke 200 server sekaligus. Ini menggambarkan keuntungan sekaligus risiko dari konsep apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **SaaS** — data & keamanan tetap tanggung jawab customer walau infrastruktur 100% dikelola provider.
2. **Air-gapped / Physical isolation**.
3. **Infrastructure as Code (IaC)** — konsisten & cepat deploy (untung), tapi kesalahan ter-replikasi ke skala besar (risiko).

---

## Hari 2 — Infrastructure Security

### Soal
1. Sebuah sistem mendeteksi ada traffic mencurigakan dan otomatis memblokirnya seketika itu juga sebelum sempat masuk ke jaringan. Ini IDS atau IPS, dan kenapa?
2. Perusahaan naruh web server yang bisa diakses publik di zona terpisah dari jaringan internal karyawan, supaya kalau web server itu kena hack, jaringan internal tetap aman. Ini contoh konsep apa?
3. Semua traffic dari internet yang mau masuk ke beberapa server backend, disaring dan didistribusikan dulu lewat satu appliance di depan. Appliance ini juga bikin server backend gak keliatan langsung dari luar. Ini contoh forward proxy atau reverse proxy?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **IPS** — blocking otomatis seketika = ciri khas IPS (inline, langsung bertindak).
2. **Screened subnet (DMZ)**, bukan Jump server. DMZ = soal penempatan/isolasi server publik. Jump server = soal kontrol akses admin ke zona aman — dua konsep beda.
3. **Reverse proxy** — melindungi server backend dari traffic masuk, sekaligus load balancing.

---

## Hari 3 — Data Protection Concepts

### Soal
1. Sebuah e-commerce menyimpan nomor kartu kredit pelanggan, tapi yang beredar di sistem mereka sehari-hari cuma "kode referensi" yang gak ada artinya sendiri — nomor kartu asli disimpan terpisah di vault yang sangat aman dan cuma dipetakan balik kalau benar-benar diperlukan. Ini contoh metode apa?
2. Sebuah sistem menyimpan password user dalam bentuk yang gak bisa dibalikin ke password asli, cuma bisa dicocokkan saat user login. Ini pakai metode apa, dan kenapa bukan encryption?
3. Data pelanggan asal Uni Eropa yang disimpan oleh perusahaan Indonesia tetap harus tunduk ke aturan GDPR. Ini contoh konsep apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Tokenization** — data asli aman di vault, yang beredar cuma token.
2. **Hashing** — one-way, gak bisa dibalikin; beda dari encryption yang reversible pakai key (kalau pakai encryption buat password, berbahaya kalau key bocor).
3. **Data sovereignty** — data tunduk hukum negara asalnya meski diproses di negara lain.

---

## Hari 4 — Resilience & Recovery

### Soal
1. Perusahaan menyiapkan lokasi backup yang cuma punya ruangan kosong + listrik, tanpa server/data apa pun tersiapkan. Ini jenis site apa?
2. Tim security cuma duduk di ruang meeting, mendiskusikan "kalau ransomware menyerang server utama, siapa yang harus melakukan apa" tanpa menyentuh sistem beneran. Ini jenis testing exercise apa?
3. Sebuah bank punya sistem yang mencatat SETIAP transaksi secara berurutan, sehingga kalau ada masalah, mereka bisa memulihkan data sampai ke detik tertentu sebelum masalah terjadi. Ini metode backup apa?
4. Saat listrik PLN mati mendadak, server kantor tetap menyala selama beberapa menit lewat baterai cadangan, cukup sampai proses shutdown aman selesai. Ini contoh apa?

<br><br><br><br><br>

### Jawaban & Pembahasan
1. **Cold site**.
2. **Tabletop exercise**.
3. **Journaling**.
4. **UPS (Uninterruptible Power Supply)**.
