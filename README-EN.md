
# ⚡ VEKO GO X - Anonymous Load Testing Engine + VEKO DOME

**VEKO GO X** is the world's first hybrid CLI tool that combines powerful load testing with complete network anonymity. With its integrated anonymization system — **VEKO DOME** — this tool lets you perform high-concurrency HTTP/HTTPS stress tests **without exposing your real IP**, DNS, or fingerprint.

---

## 🌍 What is VEKO GO X?

VEKO GO X is a modern, modular HTTP/HTTPS load testing engine designed for developers, researchers, and cybersecurity professionals. It can simulate tens to thousands of virtual users (VUs) and routes traffic through anonymizing layers like proxy rotators, the Tor network, and DNS-over-HTTPS (DoH).

---

## 🕵️ What is VEKO DOME?

**VEKO DOME** is the anonymization layer of VEKO GO X, designed to ensure full user anonymity during network testing or scraping. It includes:

- ✅ Dynamic Proxy Rotation (HTTP, SOCKS5)
- ✅ Integration with local Tor network (127.0.0.1:9050)
- ✅ DNS-over-HTTPS resolver (bypass ISP DNS)
- ✅ IP rotation & spoofing (in development)
- ✅ Passive fingerprint hiding (planned)

---

## 🎯 Why VEKO GO X Exists

- To provide a portable, anonymous load testing alternative
- To help users stress test services or APIs without exposing identity
- To offer JSON/CSV output for monitoring, logs, or dashboards
- To serve as a free, self-hosted alternative to tools like `k6`, `wrk`, or `locust`

---

## 🚀 Core Features

| Feature             | Description |
|---------------------|-------------|
| 🔁 Multi-Virtual Users (VU) | Simulate high concurrent load |
| 🌐 Proxy & Tor Support      | Route traffic anonymously |
| 🔐 DNS-over-HTTPS (DoH)     | Prevent DNS leak |
| 📦 Build as `.exe` Portable | Can be built into a standalone binary |
| 📈 JSON/CSV Logging         | Real-time result output |
| 🧩 Modular Design           | CLI, engine, output, and anonymity layers are decoupled |
| ✅ Cross-Platform CLI       | Works on Node.js or as native executable |

---

## 📁 Project Structure

```
veko-go-x/
├── src/
│   ├── cli.js          # CLI interface
│   ├── engine.js       # Load test engine
│   ├── output.js       # Logger/output writer
│   ├── utils.js        # Argument parsing
│   └── veko-dome.js    # Anonymity layer (proxy, Tor, DoH)
│
├── test/
│   └── test-veko.js    # Example test script
│
├── results/            # Output folder
├── rotate.txt          # Proxy list file
├── build.bat           # Script to build .exe
├── package.json        # Metadata and dependencies
└── README.md           # Documentation
```

---

## ⚙️ Usage Examples

### Run via Node:
```bash
node src/cli.js --url https://target.com --vus 50 --duration 15s --output json
```

### Build `.exe` (on Windows):
```bash
npm install -g pkg
npm install
build.bat
```

### Run compiled binary:
```bash
bin\veko-go-x.exe --url https://example.com --vus 20 --duration 10s --output csv
```

### Use proxy list:
```bash
veko-go-x.exe --url https://api.example.com --vus 25 --duration 30s --proxy rotate.txt
```

### Use Tor:
Make sure Tor is running at port 9050:
```bash
veko-go-x.exe --url https://target.com --vus 10 --duration 10s --tor true
```

---

## 📊 Sample Output (JSON)

```json
{
  "success": 198,
  "failure": 2,
  "avgTime": 430.56,
  "times": [420, 431, 438, 432, ...]
}
```

---

## 🧪 How is VEKO Different?

| Tool          | Load Testing | Proxy Support | Tor | DoH | JSON Output | .EXE Portability |
|---------------|--------------|----------------|-----|-----|--------------|-------------------|
| VEKO GO X     | ✅           | ✅             | ✅  | ✅  | ✅           | ✅                |
| k6            | ✅           | ❌             | ❌  | ❌  | ✅           | ❌                |
| wrk           | ✅           | ❌             | ❌  | ❌  | ❌           | ✅ (Linux only)   |
| locust        | ✅           | ❌             | ❌  | ❌  | ✅           | ❌                |
| proxychains+ab| ✅           | ✅             | ✅  | ❌  | ❌           | ✅                |
| torify+curl   | ❌           | ❌             | ✅  | ❌  | ❌           | ✅                |

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
