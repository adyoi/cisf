# Computer and Internet Security Framework for SMEs (UKM)

**Penulis:** Adi Apriyanto  
**Lokasi:** Bogor, Indonesia  
**Draf Awal:** 14 April 2025 | **Rilis Open Source:** 15 Mei 2025  

---

## 📌 Prolog

Framework ini dirancang sebagai panduan praktis, terukur, dan terjangkau bagi **Usaha Kecil dan Menengah (UKM)** dalam memahami serta menerapkan kepatuhan dasar keamanan siber. Kerangka kerja ini dibangun di atas **5 Pilar Utama**:

1. **Information** (Intelijen & Informasi Ancaman)
2. **Organization** (Tata Kelola, Regulasi & SDM)
3. **Sustenance** (Infrastruktur, Sistem & Mesin)
4. **Maintenance** (Pemeliharaan & Pemulihan Operasional)
5. **Protection** (Proteksi Defensif & Respon Insiden)

---

## 🚀 Matriks Prioritas Eksekusi (Panduan Bertahap UKM)

Guna membantu UKM dengan keterbatasan anggaran dan SDM, alokasi eksekusi framework dibagi menjadi 3 fase:

| Fase / Prioritas | Pilar Terkait | Fokus Tindakan Utama |
| :--- | :--- | :--- |
| **Fase 1: Fondasi (Must-Have)** | Protection & Maintenance | Menerapkan MFA, Backup 3-2-1 terenkripsi, Firewall/WAF dasar, serta isolasi akses. |
| **Fase 2: Tata Kelola (Should-Have)** | Organization & Information | Kepatuhan UU PDP dasar, inventarisasi aset, pemantauan CVE, dan *security awareness* karyawan. |
| **Fase 3: Lanjutan (Nice-to-Have)** | Sustenance & Defense | Penerapan Zero Trust Architecture (ZTA), XDR/SIEM terpusat, serta Tata Kelola AI/MCP. |

---

## 🏛️ Detail Operasional 5 Pilar

### 1. INFORMATION (Intelijen & Informasi Ancaman)

Pilar ini berfokus pada pengumpulan dan pemrosesan informasi terkait ancaman keamanan agar organisasi dapat bertindak proaktif sebelum serangan terjadi.

* **1.1 Advisories (Imbauan Keamanan Resmi):**
  * **CVE (Common Vulnerabilities and Exposures):** Sistem identifikasi standar untuk kerentanan keamanan terpublikasi. UKM wajib mengawasi entri CVE pada *stack* teknologi utama (PHP, MySQL, Linux, WordPress, dll).
  * **CWE (Common Weakness Enumeration):** Kategori kelemahan pada kode/arsitektur (misal: CWE-89 untuk SQL Injection). Digunakan sebagai standar edukasi tim pengembang saat *code review*.
  * **CVSS (Common Vulnerability Scoring System) & EPSS:** Skala skor kerentanan (0.0 – 10.0).  
    > **Aturan Patching UKM:** Kerentanan dengan skor CVSS ≥ 7.0 yang telah memiliki eksploit aktif di publik (*Proof of Concept/PoC*) wajib diprioritaskan untuk di-patch dalam waktu 2x24 jam.
* **1.2 From News (Berita & Informasi Industri):**
  * **New Products & Tech:** Evaluasi alat keamanan baru yang efisien dari segi biaya untuk UKM.
  * **Incident Reports:** Pelajari studi kasus kebocoran data (*data breach*) industri serupa untuk menutup celah internal.
  * **Platform Update & Patch:** Pantau rilis pembaruan rutin dari vendor software (Microsoft, Google, vendor router, dll).
  * **Vulnerable Bugs & Exploits:** Memantau tren eksploitasi aktif yang beredar di komunitas keamanan lokal (seperti BSSN/Id-SIRTII) dan global.
* **1.3 From CTI (Cyber Threat Intelligence):**
  * **Attacking Info:** Pengumpulan data terkait IP terindikasi jahat, domain *phishing*, dan pola serangan khas yang menargetkan UKM.
  * **Zero-Day:** Informasi kerentanan yang belum memiliki *patch* resmi dari vendor. UKM perlu menerapkan mitigasi sementara (*virtual patching* via WAF atau aturan khusus pada Firewall).

---

### 2. ORGANIZATION (Tata Kelola, Regulasi & Manajemen SDM)

Pilar ini mengatur aspek manusia, kebijakan, regulasi, dan struktur organisasi yang mendukung keamanan informasi.

* **2.1 Business & Application Logic:**
  * **Business Logic (Risk Management):** Identifikasi aset paling kritis (database transaksi, data pelanggan) serta analisis dampak bisnis jika terjadi kegagalan sistem (*Business Impact Analysis*).
  * **Application Logic (Secure by Design):** Memastikan alur kerja aplikasi tidak dapat dimanipulasi (misal: memotong alur pembayaran e-commerce) dan menerapkan prinsip *Secure by Design* sejak awal pembuatan aplikasi.
* **2.2 Supply Chain & CRM:**
  * **Supply Chain Management (SCM):** Memastikan vendor pihak ketiga (hosting, payment gateway, jasa pengiriman) memiliki standar keamanan memadai agar tidak menjadi pintu masuk serangan (*third-party risk*).
  * **Customer Relationship Management (CRM):** Menjaga kerahasiaan data dalam CRM dan membatasi akses data sensitif pelanggan hanya kepada staf yang berwenang.
* **2.3 Compliance & Human Resources:**
  * **Data Regulation (UU PDP, GDPR, PSE):** Kepatuhan terhadap UU Pelindungan Data Pribadi (Indonesia), registrasi PSE Kominfo, serta pemenuhan hak subjek data (persetujuan pemrosesan dan hak penghapusan data).
  * **Human Resources:**
    * *Bug Bounty:* Program pelaporan celah keamanan internal/eksternal secara etis.
    * *Sertifikasi:* Mendorong peningkatan kompetensi staf IT (misal: CompTIA Security+, CEH, ISO 27001 Auditor).
    * *Security Awareness:* Pelatihan rutin anti-phishing dan rekayasa sosial (*social engineering*) untuk seluruh karyawan non-IT.
* **2.4 Management Standards & IT Operations:**
  * **Framework Adopsi:** Penyesuaian kontrol dari ISO/IEC 27001, CIS Controls, atau NIST CSF sesuai skala UKM.
  * **IT Development & Operations:** Penerapan akses minimum (*Principle of Least Privilege*) pada database/API, operasional SOC/SOAR untuk pemantauan log, konfigurasi aman router/server (SysAdmin baselining), serta amannya penggunaan perangkat produktivitas (Google Workspace/M365, NAS/AD, Zoom/Teams).

---

### 3. SUSTENANCE (Infrastruktur & Ekosistem Sistem)

Pilar ini mencakup fondasi teknis, infrastruktur keras/lunak, serta arsitektur tempat aplikasi dan data berjalan.

* **3.1 System Layer (Teknologi Informasi):**
  * **OS & Virtualisasi:** Hardening OS server produksi (Windows Server, Ubuntu, AlmaLinux) serta isolasi lingkungan menggunakan virtualisasi (KVM, Proxmox).
  * **Containerization:** Pengelolaan lingkungan kontainer terisolasi (Docker, Kubernetes) dengan manajemen *secret/key* yang aman.
  * **Application & API:** Keamanan REST API/GraphQL menggunakan validasi input, sanitasi, dan otentikasi berbasis token (JWT/OAuth2).
  * **Server & Hosting:** Pemilihan infrastruktur yang diisolasi dengan baik (VPS, Dedicated Server, PaaS, atau Shared Hosting berisolasi ketat).
  * **Networking:** Penggunaan IP Statis/Dedicated untuk server publik, segmentasi jaringan menggunakan *Switch Manageable* (VLAN) dan *Router Firewall*, serta koneksi administratif via Encrypted VPN (WireGuard/OpenVPN).
  * **Development Life Cycle:** Integrasi tes keamanan otomatis (SAST) pada alur CI/CD, penerapan SDLC aman, serta uji penetrasi (*Penetration Testing*) berkala.
  * **Artificial Intelligence (AI):** Penggunaan AI untuk deteksi anomali serta penerapan **Model Context Protocol (MCP)** untuk mengamankan konteks data saat menghubungkan model AI/Agent (Gemini, Copilot, Grok) dengan sistem internal.
* **3.2 Machine Layer (OT & IoT - Operational Technology):**
  * **OT (ICS / DCS / SCADA / PLC):** Isolasi jaringan fisik/mesin industri dari jaringan internet publik untuk UKM di sektor manufaktur/produksi.
  * **IoT:** Mengubah *password default* pada perangkat IoT (CCTV, sensor) dan menempatkannya pada segmen jaringan terpisah (Guest/IoT VLAN).

---

### 4. MAINTENANCE (Pemeliharaan & Preservasi Operasional)

Pilar ini berfokus pada kegiatan pemeliharaan rutin untuk memastikan ketersediaan sistem (*availability*) dan kesiapan menghadapi bencana (*Disaster Recovery*).

* **4.1 Backup Management (Aturan 3-2-1):**
  * Menyimpan minimal **3** salinan data, pada **2** media berbeda, dengan **1** salinan berada di lokasi terpisah (*offsite/cloud*).
  * **Cloud Backup:** Penyimpanan cadangan terenkripsi ke layanan cloud (Google Workspace, AWS S3, OneDrive).
  * **Local Backup:** Backup lokal terjadwal pada media yang terisolasi (*air-gapped*) dengan enkripsi standar AES-256.
* **4.2 Patch & Change Management:**
  * **Firmware Updates:** Pembaruan rutin firmware pada perangkat keras jaringan (Router, Switch, Access Point).
  * **System Upgrades:** Pembaruan versi utama OS/framework sebelum mencapai status *End of Life* (EOL).
* **4.3 Restoration & Configuration:**
  * **Restoration Test:** Simulasi pemulihan data (*restore test*) berkala untuk memastikan berkas backup tidak korup dan dapat digunakan saat krisis.
  * **Configuration Baseline:** Pencatatan dan pencadangan file konfigurasi perangkat/server agar proses rekonstruksi infrastruktur pasca-insiden berjalan cepat.

---

### 5. PROTECTION (Proteksi Defensif & Respon Insiden)

Pilar ini adalah lapisan pertahanan aktif dan reaktif untuk menangkal, mendeteksi, dan merespon serangan siber.

* **5.1 Endpoint & Perimeter Security:**
  * **Endpoint Defense (SIEM / XDR / IPS / IDS):** Deteksi dini infiltrasi jaringan dan pengumpulan log terpusat untuk memantau perilaku abnormal pada server dan komputer kerja.
  * **Proxy Services:** Penggunaan *Reverse Proxy* (misal: Cloudflare) untuk menyembunyikan IP publik server dan memfilter lalu lintas masuk, serta *Forward Proxy* (misal: Squid) untuk memfilter lalu lintas keluar dari kantor.
* **5.2 Network & Application Defense:**
  * **Topology Isolation:** Memisahkan jaringan antar divisi (misal: jaringan keuangan terpisah dari Wi-Fi tamu).
  * **DDoS & WAF Protection:** Mitigasi serangan banjir lalu lintas serta penggunaan Web Application Firewall (WAF) untuk memblokir serangan populer (SQLi, XSS, LFI).
  * **Zero Trust Architecture (ZTA) & MFA:** Menerapkan prinsip "tidak pernah percaya, selalu verifikasi" dan mewajibkan autentikasi ganda (MFA) pada seluruh akun operasional bisnis.
* **5.3 Strike Conditions (Incident Response Plan):**
  * Ketika insiden terjadi, tim wajib mengikuti 5 alur taktis:
    1. **Mitigation:** Mengisolasi sistem yang terdampak (memutus koneksi jaringan) untuk menghentikan penyebaran serangan.
    2. **Reaction:** Mematikan vektor serangan dan mengidentifikasi asal celah keamanan.
    3. **Recovery:** Memulihkan sistem dan data dari salinan cadangan (*backup*) yang terverifikasi bersih.
    4. **Response:** Melakukan komunikasi insiden kepada pemangku kepentingan dan pihak berwenang sesuai regulasi (misal: pemberitahuan kebocoran data pribadi sesuai UU PDP).
    5. **Reports:** Menyusun laporan pasca-insiden (*Post-Incident Report*) guna evaluasi dan penutupan celah secara permanen.
