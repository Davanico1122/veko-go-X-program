#  VEKO GO X - Anonymous Load Testing System + VEKO DOME

**VEKO GO X** adalah sistem uji beban jaringan (load testing) canggih yang **pertama di dunia** menggabungkan performa tinggi, anonimitas koneksi, dan portabilitas dalam satu alat tunggal berbasis CLI. Tool ini dirancang khusus untuk developer, peneliti jaringan, ethical hacker, dan profesional QA yang ingin melakukan pengujian secara intensif namun tetap terlindungi secara privasi.

---

##  Apa Itu VEKO GO X?

VEKO GO X adalah engine uji beban (load test engine) berbasis HTTP/HTTPS yang mampu mensimulasikan puluhan hingga ribuan Virtual Users (VU) secara paralel. Tidak seperti tool lainnya, VEKO GO X terintegrasi langsung dengan sistem **anonimitas** dan **lapisan keamanan koneksi** bernama VEKO DOME — sebuah sistem yang memungkinkan pengguna menyamarkan IP melalui rotasi proxy, jaringan Tor, dan DNS-over-HTTPS.

---

##  Apa Itu VEKO DOME?

**VEKO DOME** adalah modul keamanan jaringan tambahan untuk VEKO GO X. Tujuannya adalah melindungi identitas dan lokasi pengguna selama melakukan pengujian beban.

### Fitur VEKO DOME:
-  **Proxy rotator otomatis** (HTTP, SOCKS5)
-  **Koneksi via Tor** (port 9050 lokal)
-  **DNS-over-HTTPS resolver** untuk menghindari DNS leak
-  **Spoofing dan masking fingerprint (dalam pengembangan)**
-  **Deteksi & rotasi IP publik**

---

##  Tujuan VEKO GO X

- Memberikan alat pengujian beban yang **ringan, kuat, dan portabel**
- Melindungi identitas pengguna dalam pengujian sistem jaringan
- Memungkinkan pengujian API, endpoint, atau server secara anonim
- Menghasilkan log dan data output siap analisis (JSON/CSV)
- Menjadi alternatif open-source terhadap alat komersial seperti **k6**, **Locust**, **Wrk**, dll

---

##  Fitur Unggulan

| Fitur | Deskripsi |
|-------|-----------|
|  Virtual Users (VU) | Menjalankan banyak pengguna virtual bersamaan untuk menguji kestabilan server |
|  Anonimitas Jaringan | Koneksi melalui proxy, Tor, dan DoH |
|  Logging Otomatis | Output disimpan otomatis dalam format `.json` atau `.csv` |
|  CLI Modular | Parameter lengkap: `--url`, `--vus`, `--duration`, `--output`, `--proxy`, `--tor` |
|  Modular Coding | Semua modul terpisah: engine, CLI, output, anonimitas |
|  Build `.exe` | Bisa dibuild jadi executable portabel untuk Windows |
|  Testable | Mendukung file skrip pengujian manual via folder `/test` |
|  Kompatibel | Bisa dijalankan via Node.js atau dibuild ke `.exe` dengan `pkg` |

---

##  Struktur Proyek VEKO GO X

```
veko-go-x/
├── src/
│   ├── cli.js          # Entry point CLI
│   ├── engine.js       # Mesin pengujian beban
│   ├── output.js       # Logging dan output writer
│   ├── utils.js        # Argument parser
│   └── veko-dome.js    # Lapisan anonimitas koneksi
│
├── test/
│   └── test-veko.js    # Contoh skrip pengujian
│
├── results/            # Hasil output JSON / CSV
├── rotate.txt          # Daftar proxy acak
├── build.bat           # Script build .exe
├── package.json        # Dependensi & metadata
└── README.md           # Dokumentasi
```

---

## 🛠️ Cara Menjalankan

### 📦 1. Jalankan langsung dengan Node.js
```bash
node src/cli.js --url https://target.com --vus 50 --duration 10s --output json
```

### 🏗️ 2. Build menjadi `.exe`
```bash
npm install -g pkg
npm install
build.bat
```

### 🖥️ 3. Jalankan `.exe` portabel
```bash
bin\veko-go-x.exe --url https://target.com --vus 50 --duration 15s --output json
```

### 🌐 4. Menggunakan Proxy
```bash
veko-go-x.exe --url https://site.com --vus 20 --duration 10s --proxy rotate.txt
```

### 🕸️ 5. Koneksi via Tor
Pastikan Tor Browser atau service aktif di `127.0.0.1:9050`, lalu:
```bash
veko-go-x.exe --url https://site.com --vus 10 --duration 5s --proxy rotate.txt --tor true
```

---

## 📊 Contoh Output

```json
{
  "success": 198,
  "failure": 2,
  "avgTime": 430.56,
  "times": [420, 431, 438, 432, 441, ...]
}
```

---

## 📈 Perbandingan Dengan Tool Lain

| Tool | Load Test | Proxy | Tor | DoH | JSON Output | CLI | .exe |
|------|-----------|-------|-----|-----|-------------|-----|------|
| VEKO GO X | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| k6 | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| wrk | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ (Linux only) |
| locust | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ |
| proxychains + ab | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ | ✅ |
| torify + curl | ❌ | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ |

---

## 📜 Lisensi

MIT License — Bebas digunakan, dimodifikasi, dan dikembangkan.

---

## 📢 Catatan Tambahan

- Tool ini ditujukan untuk **pengujian legal dan edukatif**.
- Tidak disarankan untuk digunakan terhadap sistem yang bukan milik sendiri tanpa izin.
- Developer tidak bertanggung jawab atas penyalahgunaan.

---

## 🧠 Tentang Proyek Ini

VEKO GO X adalah proyek terbuka (open project) yang dirancang oleh developer independen. Ini adalah alat pertama yang secara eksplisit menyatukan **anonimitas dan uji beban dalam satu CLI**, sesuatu yang bahkan belum dicapai oleh tool besar seperti `k6`, `locust`, atau `wrk`.

Jika kamu tertarik untuk ikut mengembangkan — atau hanya ingin memberi bintang — silakan fork repo ini, beri kontribusi, dan bantu jadikan VEKO GO X sebagai standar baru uji jaringan.


---

## ⚠️ Legal Disclaimer & Usage Boundaries

**VEKO GO X** and its anonymizing engine **VEKO DOME** are powerful tools designed for ethical load testing, research, and educational purposes only. Due to their unique combination of anonymity (proxy, Tor, DoH) and stress-testing capabilities, they must be used **with strict responsibility**.

### ❗ Danger & Capabilities

VEKO GO X can:
- Simulate large-scale parallel HTTP(S) requests
- Evade detection via proxy rotation or Tor
- Obfuscate network identities through DNS-over-HTTPS

🚨 This makes it potentially capable of:
- Bypassing IP-based throttling
- Overloading systems without detection
- Masking source of heavy traffic

**If abused**, it could severely disrupt public or private servers — making it a **cybersecurity risk if in the wrong hands**.

---

## 🔐 Intellectual Property & Forking Rules

This project is open-source for collaboration, transparency, and security development — **but the core idea and system integration design are original intellectual property**.

You may:
- Use and study the code under the MIT license
- Contribute to improve or extend the tool

You may **not**:
- Republish it under a different name as if it's your invention
- Commercialize it without permission
- Remove credit or claim authorship of the core system design

**Original System by: Dava / VEKO Development Initiative**

---

## ✅ Use Responsibly

- Use it only on systems **you own or have explicit permission to test**
- Use it to stress test APIs, load infrastructure, or anonymized data routing
- Do **not** use it for DDoS, unauthorized scanning, or attacks

> Misuse of this tool may violate computer abuse laws in your country.

---

## 📌 You Are Responsible

By using this software, you accept full responsibility for your actions and any consequences that may result. The creator(s) are **not liable** for any damage, legal issues, or misuse.
