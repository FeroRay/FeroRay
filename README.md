<div align="center">
<pre>
 _____               _____             
  |  ___|             |  __ \            
  | |__ ___ _ __ ___  | |__) |__ _ _   _ 
  |  __/ _ \ '__/ _ \ |  _  // _` | | | |
  | | |  __/ | | (_) || | \ \ (_| | |_| |
  \_|  \___|_|  \___/ |_|  \_\__,_|\__, |
                                    __/ |
                                   |___/
</pre>
</div>

# [ ❖ F E R O : R A Y ❖ ] 
## Enterprise Network & DPI Analysis Engine

**FeroRay** is an ultra-advanced, intelligent platform designed for deep network topology analysis, Deep Packet Inspection (DPI) monitoring, and the optimization of secure communication tunnels. By combining powerful multi-threaded scanners with an AI evaluation engine (FeroRay Predictive Intelligence), this tool empowers network engineers to ensure the stability and health of their connections under the most complex and restrictive filtering conditions.

### ⚡ Core Engine Capabilities Overview

* **AI Threat Heuristics:** An intelligent analyzer capable of accurately identifying network anomalies such as TCP RST injection, TLS Handshake blocking, DNS spoofing, and routing blackholes, delivering thoroughly categorized diagnostic reports.
* **Hybrid Path Analyzer:** Simultaneous evaluation of connection quality across both the physical layer (Underlay MTR / Traceroute) and encrypted tunnels (Overlay Xray Core) to pinpoint bottlenecks and precisely calculate Jitter and Bufferbloat.
* **Scoring System & Traffic Profiles:** Automated, parallel validation of hundreds of configs and IPs based on specialized performance profiles (Gaming, Speed, Stability), assigning quality scores using advanced latency and stability weighting algorithms.
* **CDN Scanner & Auto-Generator:** A high-speed, highly accurate asynchronous probe for scanning vast IP ranges, validating headers and SNIs, and intelligently auto-generating stable, ready-to-use V2Ray/Xray configurations.
* **Cyber Dashboard & Interactive Radars:** Real-time visualization of complex data through live visual charts. This includes ping fluctuation monitoring (Cyber Heartbeat), threat detection radars, and predictive estimations of tunnel lifespan and stability (Predictive Lifespan).

---

## 🎛️ Panel 1: 🛡️ Ferodo Ultimate Network IP CF Scanner

![🛡️ Ferodo Ultimate Network IP CF Scanner](https://github.com/user-attachments/assets/932bdc56-d29c-490c-a08c-36c2e853af59)

This project is an ultra-advanced, multi-threaded network scanner and traffic analysis tool built with Go (Golang) and the Fyne UI toolkit. It is specifically designed for Deep Packet Inspection (DPI) analysis, scanning CDN IPs (such as Cloudflare, AWS, Fastly, etc.), and automatically generating V2Ray configurations.

### 🌟 Key Features
* **Asynchronous Scanner Engine:** Scans thousands of IPs per second utilizing concurrent processing and optimized execution threads.
* **Advanced CF-RAY Analyzer:** Capable of extracting the `CF-RAY` header to identify and discover Non-Cloudflare IPs with high tunneling potential, which are highly useful for creating dedicated and stable V2Ray configs.
* **SNI & Reverse Proxy Search Engine:** Equipped with a powerful `Reverse Proxy SNI Finder` to check the reverse proxy status on specific domains and bypass filtering restrictions.
* **Smart DPI Detection:** Identifies blocking mechanisms, including Connection Timeouts and TCP RST blocks.
* **V2Ray Config Generator:** Automatically converts healthy and active IPs into ready-to-use Vless/Trojan configs.
* **Subnet Converter:** Advanced tools to break down large CIDR blocks into smaller subnets.
* **Multi-Protocol Support:** Dynamic testing via HTTP Web (Layer 7), TCP Socket (Layer 4), and UDP Ping.

### 🖥️ UI Components and Operational Buttons Guide

#### 1. Subnet Converter
Designed for managing and processing IP ranges (CIDR):
* **`Split & Send ➔`**: Takes large CIDR ranges (e.g., `/15` or `/20`), splits them into smaller, targeted subnets (like `/24`), and sends them directly to the custom IP pool.
* **`Fast Scan Filter ➔`**: Applies a smart, structural filter to test only one representative from each range; this technique prevents redundant scans and significantly increases scanning speed.
* **`Paste / Copy / Clear`**: Quick clipboard management for the subnet input box.

#### 2. Custom Subnets / Target IPs and CDN Pools
* **`Load File`**: Imports a `.txt` file containing your target IPs.
* **`Cloudflare Pool` tab**: An internal database of Cloudflare, AWS CloudFront, Fastly, Gcore, and Akamai IP ranges. Simply check their boxes to add them to the scan queue.
* **`V2Ray Config` tab - Convert Grid & Custom IPs**: Paste a base V2Ray link (e.g., `vless://UUID@IP:443...`). The scanner engine replaces the base IP with all healthy IPs found in the table, generating multiple fresh configs.
* **`V2Ray Config` tab - Extract All IP**: Analyzes your current V2Ray configs and extracts only the raw IPs or domains from them.

#### 3. SNI Finder and Hardware Performance Profile
* **`SNI Finder Mode`**: When enabled, checks the Reverse Proxy status for a specific domain (e.g., `neal.fun`).
* **`ALPN, WebSocket, gRPC, QUIC` Checkboxes**: Determine whether these specific protocols should be validated during the HTTP request.
* **`Workers`**: The number of concurrent connections and parallel processes to execute the scan (Default: 150).
* **`Timeout`**: The maximum wait time to receive a response, in milliseconds.
* **`Ports`**: Target ports for scanning (supports multiple ports separated by commas).

#### 4. Filters and Live Search
* **`Search Bar`**: A live, global search across all columns in the results table.
* **`Target COLO` filters**: Select specific datacenters (like FRA, AMS, LHR) to filter the table and display IPs routed exclusively through those paths.
* **`Show ONLY Active (CF) in Table` filter**: Filters the table to display only IPs that return a valid Cloudflare server header.
* **`Keep Previous Results` option**: Prevents the table from being cleared when starting a new scan.

#### 5. Advanced Strategy and Range Optimization
* **`Full Random Shuffle` option**: Completely shuffles all target IPs prior to scanning to ensure a random distribution of traffic.
* **`Pick X per /24` option**: Limits the scan to a specific number of IPs per `/24` subnet to prevent redundant and repetitive scanning.
* **`Auto switch range after 5 working IPs` option**: Immediately jumps to the next subnet as soon as 5 healthy IPs are found in the current one.
* **`Auto-Skip High Latency Nodes` option**: Automatically removes nodes with a ping higher than 800ms.
* **`Strict Loss Filter` option**: Immediately drops IPs experiencing any Packet Loss.

#### 6. Dynamic Active Protocols Engine
* **`HTTP Web (Default)` mode**: Sends full Layer 7 requests to read headers, SSL certificates, and CDN routing status.
* **`TCP Socket Ping` mode**: Performs a Layer 4 (TCP) ping, which is ideal for checking open ports.
* **`UDP Ping` mode**: Designed for testing UDP connectivity.

#### 7. Main Operation Controls
* **`FERODO SCAN` button**: Starts the main scanner engine with all selected parameters.
* **`Stop` button**: Stops the current scan immediately.
* **`Copy Selected / All` button**: Copies the selected rows (or all rows) to the clipboard.
* **`Save To File` button**: Exports valid IPs into a `.txt` file.
* **`Change Dir` button**: Changes the destination folder for saving files.
* **`Dark / Light` button**: Toggles the UI theme.
* **`Send to V2Ray` button**: Sends all valid IPs from the table directly to the V2Ray Config tab for config generation.

### 📊 Report Table Data Guide
The output table provides comprehensive metrics regarding network status. Here is the meaning of each column:

| Column | Description |
| :--- | :--- |
| **Valid IP Address** | The scanned IP that successfully responded. |
| **Port** | The scanned port (e.g., `443`). |
| **Ping (ms)** | Connection latency in milliseconds. |
| **Jitter** | Calculated ping fluctuation to determine connection stability. |
| **Loss (%)** | Percentage of Packet Loss during the test. |
| **TLS Engine** | Transport layer engine type (e.g., TLS 1.3 / HTTPS, Reverse Proxy, L4 TCP). |
| **COLO / SNI** | Cloudflare datacenter tag (e.g., `FRA` for Frankfurt) or the captured SNI domain. |
| **ALPN** | Negotiated Application-Layer Protocol (e.g., `h2` or `http/1.1`). |
| **WebSocket** | WebSocket support status (Supported / -). |
| **gRPC** | gRPC communication support status. |
| **QUIC** | QUIC / HTTP3 protocol support status. |
| **DPI Status** | Deep Packet Inspection filtering status. Includes: `Active (CF)` (Healthy), `Timeout`, `RST Blocked`, or `Clean`. |
| **TLS Cert Name** | Common Name (CN) of the server's SSL certificate issuer. |
| **TTL** | Time To Live value of the packets. |
| **CF-RAY** | Unique Cloudflare connection header ID for precise tracking. By analyzing the structure of these headers, the scanner engine discovers and validates Non-Cloudflare IPs that possess tunneling potential. |

---

## 🎛️ Panel 2: 🌩️ FeroRay Multipath V2ray Config Target Analyzer (Enterprise Edition)

![FeroRay Multipath Target Analyzer](https://github.com/user-attachments/assets/d05dd0c1-c72e-4fab-9a28-ac5b7106a005)

An ultra-high-performance, multi-threaded network scanning and configuration validation engine. This panel is engineered for bulk testing of IPs, CIDR blocks, URLs, and complex Proxy Configurations (VLESS, VMESS, Trojan). By integrating a highly concurrent execution architecture with the **Xray-core**, it provides surgical telemetry on network paths, dynamically scoring targets based on customizable heuristic profiles.

### ✨ Core Engineering & Capabilities

* **High-Throughput Concurrency:** Utilizes a highly scalable asynchronous execution engine to handle extensive lists of IPs, URLs, and Configs simultaneously without UI bottlenecking.
* **Smart Payload Processing:** Automatically analyzes and normalizes complex network ranges into actionable targets, streamlining raw inputs for flawless testing.
* **Dual Routing Architectures - Underlay (Direct to Edge/CDN):** Tests direct physical network routes, executing deep Layer-4 and Layer-7 diagnostics directly against edge nodes.
* **Dual Routing Architectures - Overlay (Through Xray Tunnel):** Dynamically orchestrates the Xray core to establish isolated testing environments, measuring "Real Ping" and performance metrics through the encrypted tunnel.
* **Xray Multi-Config Validation:** Paste multiple `vless://`, `vmess://`, or `trojan://` links. The engine interprets the routing structures, provisions isolated connection states for each node, and batch-tests them simultaneously.
* **Forced IP & Host Routing:** Seamlessly binds target URLs to specific custom IPs, allowing you to test Anycast routing by forcing specific routing headers over designated physical endpoints.

### 🧮 Intelligent Scoring & Profiling System

The engine does not rely on a simple ping. It utilizes a highly granular, weighted mathematical scoring system (0-100) to grade every target. 

#### Pre-Built Heuristic Profiles

| Profile | Target Metric Focus | Best Use Case |
| :--- | :--- | :--- |
| 🔵 **Speed Profile** | High weight on TTFB (Time to First Byte), TLS Handshake, and Real Ping. | Web browsing, downloading, CDN streaming. |
| 🟢 **Stability Profile** | Strict penalty for Packet Loss and Range/Jitter. Ignores TCP Min. | SSH, Database connections, uninterrupted tunnels. |
| 🟠 **Balanced Profile** | Even distribution across TCP Avg, Loss, Jitter, and URL Load Time. | General purpose proxying. |
| 🟣 **Gaming Mode** | Massive weight on "Real Ping" and "Ping Fail Rate". Strict Jitter control. | Competitive gaming, VoIP, real-time UDP applications. |

#### Advanced Metric Telemetry

* **TCP Metrics:** Min, Avg, Worst, and **Range** (Worst - Min, revealing route volatility).
* **Jitter & Loss:** Sub-millisecond tracking of ping fluctuation and packet drop percentages.
* **Layer 7 Diagnostics:** TLS Handshake Time, TTFB, and Full URL Load Time.
* **Target Colo Tracking:** Analyzes Edge node routing responses to extract and display the specific data center colocation (e.g., `FRA`, `VIE`, `AMS`) and active TLS Version.
* **Colo Bonus Scoring:** Assigns a customizable point bonus to targets that successfully route through your preferred regional datacenters.

### 📊 Dynamic UI & Data Management

* **Smart Auto-Sorting:** The data table features a context-aware sorting engine capable of interpreting different data types (networking formats vs. standard numerics) for precise organization.
* **Color-Coded Visual Indicators:** 🟩 **Green (Score > 80):** Premium | 🟨 **Yellow (Score > 50):** Degraded | 🟥 **Red (Score < 50):** Failing.
* **Live Progress Engine:** A real-time ETA calculator, progress bar, and active target counter update asynchronously alongside live chart integrations.

### 🛠 Actionable Controls & Exports

* **Copy ALL Passed:** Instantly extracts and copies all configurations or IPs that scored above your defined threshold.
* **CSV Export:** Dumps the entire telemetry matrix into a standardized `.csv` file for external analysis.
* **Clipboard Integration:** Built-in `Load`, `Paste`, `Copy`, and `Clear` macro buttons for rapid target manipulation.
* **Emergency Halt:** A hard `🛑 STOP` execution signal that safely interrupts all active operations immediately.

### 🚀 Quick Execution Guide

1. **Input Targets:** Paste IPs, CIDRs, URLs, or URI links into the input areas.
2. **Select Routing Mode:** Choose between Underlay (Raw TCP/HTTP) or Overlay (Xray Core). 
3. **Select Profile:** Click a Scoring Profile to automatically adjust the mathematical weights.
4. **Define Filters:** Set your preferred target Colos and your minimum score threshold.
5. **Execute:** Click `START LIVE ENGINE`. Watch the asynchronous engine populate the matrix in real-time.
6. **Export:** Sort by **Score ▼**, and click `Copy ALL Passed` to grab your stable configs!

---

<div align="center">

# 🛡️ Ferodo Deep Route Analyzer

<img src="https://img.shields.io/badge/Go-1.21+-00ADD8?style=for-the-badge&logo=go&logoColor=white"/>
<img src="https://img.shields.io/badge/Fyne-v2-informational?style=for-the-badge&logo=go"/>
<img src="https://img.shields.io/badge/Engine-v2.6.0--Enterprise-blueviolet?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey?style=for-the-badge"/>
<img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>

**An enterprise-grade, AI-powered network diagnostic suite for detecting DPI interference,
firewall censorship signatures, and overlay tunnel instability in real time.**

</div>

---
![FeroRay Deep Route Analyzer](https://github.com/user-attachments/assets/571a4a6f-a160-490e-8489-8dc3345ba8a1)
## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Architecture](#-architecture)
- [Visual Components](#-visual-components)
- [Ferodo AI Engine](#-ferodo-ai-engine-v260-enterprise)
- [DPI Signature Detection](#-dpi-signature-detection)
- [Supported Protocols](#-supported-protocols)
- [Installation](#-installation)
- [Usage](#-usage)
- [Configuration Options](#-configuration-options)
- [Grading System](#-grading-system)
- [Export & Reporting](#-export--reporting)

---

## 🌐 Overview

**Ferodo Deep Route Analyzer** is a professional-grade, cross-platform desktop application built in Go with the Fyne UI framework. It operates on two simultaneous layers — **Overlay** (your VPN/proxy tunnel) and **Underlay** (the raw physical network path) — to give you a complete picture of network health, censorship presence, and tunnel viability.

The application parses VLESS, VMESS, and Trojan configurations, establishes a local Xray-Core tunnel, and performs high-frequency probing against configurable Anycast endpoints while concurrently running a native OS traceroute. All collected telemetry is fed into the **FerodoAI Heuristics Engine**, which generates a structured threat report with an actionable intelligence brief.

---

## ✨ Key Features

### 🔬 Dual-Layer Probing

| Layer | Method | Target | Samples |
|---|---|---|---|
| **Overlay** | HTTP/TLS via SOCKS5 | Configurable Anycast URLs | Up to 200 probes |
| **Underlay** | ICMP/UDP Traceroute (OS-native) | `8.8.8.8` | Up to 15 hops |

### 🤖 AI-Powered Analysis
- Statistical matrix computation (Min/Max/Mean/Median/IQR/StdDev/Variance)
- 7-signature DPI threat detection engine
- Heuristic scoring with S → DEAD grading scale
- Actionable tactical intelligence generation
- Typewriter-animated diagnostic console log

### ⚡ Real-Time Visualization
- Live latency waterfall chart with cosine interpolation and color-coded direction
- Anomaly radar chart across 5 threat dimensions
- Hop-by-hop loss heatmap
- Traffic entropy profiler
- Predictive ban-risk estimator with EWMA smoothing
- TCP anomaly signal interceptor
- Latency distribution histogram

### 🛠️ Operational Tools
- **Quick Ping** — Instant multi-endpoint parallel latency test with golden route detection
- **Auto Self-Healing** — Detects tunnel failure and hot-reloads a new config from clipboard
- **uTLS Fingerprinting** — ClientHello impersonation (Chrome / Firefox / Safari / iOS / Random)
- **ISP Detection** — Live underlay network operator identification via `ip-api.com`
- **BufferBloat Measurement** — Real-time bloat score with severity labeling
- **Screenshot Capture** — Saves full UI as PNG
- **Full Report Export** — Saves a structured diagnostic report as a text file
- **Log Copy** — One-click copy of the diagnostics console to clipboard

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                  Fyne GUI Application                   │
│                                                         │
│  ┌───────────────────┐    ┌──────────────────────────┐  │
│  │  Input & Controls │    │  Real-Time Widget Layer  │  │
│  │  - Config Parser  │    │  - Jitter Chart          │  │
│  │  - Probe URLs     │    │  - Anomaly Radar         │  │
│  │  - uTLS Select    │    │  - Entropy Profiler      │  │
│  │  - Auto Failover  │    │  - Stability Gauge       │  │
│  └────────┬──────────┘    │  - Ban Risk Estimator    │  │
│           │               │  - TCP Interceptor       │  │
│           ▼               │  - Hop Heatmap           │  │
│  ┌────────────────────┐   │  - Latency Histogram     │  │
│  │   Xray-Core SOCKS5 │   └──────────────────────────┘  │
│  │   Local Tunnel     │                                  │
│  └────────┬───────────┘   ┌──────────────────────────┐  │
│           │               │  FerodoAI Heuristics     │  │
│   ┌───────┴────────┐      │  Engine v2.6.0           │  │
│   │                │      │  - Statistical Matrix    │  │
│   ▼                ▼      │  - Topology Analysis     │  │
│ Overlay          Underlay │  - DPI Signature Scan    │  │
│ HTTP Probing     OS trace │  - Score & Grade         │  │
│ (150 rounds)     (15 hops)│  - Tactical Intel        │  │
│                           └──────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 🎨 Visual Components

### Live Overlay Waterfall Chart
A scrollable, high-resolution latency chart plotting up to 200 probe samples. Each segment is rendered using **cosine interpolation** for smooth curves. Line color changes dynamically:
- 🟢 **Cyan** — Latency improving (decreasing)
- 🔴 **Red** — Latency degrading (increasing)
- 🔴 **Spike Red** — Values exceeding moving average threshold by 150ms+
- 🟡 **Yellow Baseline** — Rolling 20-sample average

### Anomaly Radar Chart
A pentagon radar chart scoring 5 independent threat axes in real time:

| Axis | Signal | Max Score |
|---|---|---|
| TCP RST | Reset-by-peer / Refused counts | 100 |
| TLS EOF | TLS/EOF/Timeout error counts | 100 |
| PKT LOSS | Packet loss percentage | 100 |
| JITTER | Normalized jitter value | 100 |
| ENTROPY | Traffic delta entropy score | 100 |

### Hop Loss Heatmap
A compact block heatmap showing each traceroute hop as a color-coded tile:
- 🟢 **Green** — 0% loss
- 🟡 **Orange** — 1–50% loss
- 🔴 **Red** — >50% loss
- ⬛ **Grey** — 100% loss (ICMP blocked)

### Tunnel Stability Index
Displays a computed stability score (0–100%) derived from jitter volatility ratio and inferred packet drops:
- 🟢 ≥75%: Stable
- 🟡 45–74%: Degraded
- 🔴 <45%: Critical

### Predictive Ban Risk Estimator
Uses an **Exponential Weighted Moving Average (EWMA)** with 85/15 momentum weighting to compute ban risk from packet loss, traffic entropy, TCP RST counts, and TLS EOF counts. The estimate smooths out transient ping spikes and tracks only sustained degradation trends.

Output states:
- 🟢 `Highly Stable (Safe)` — Risk < 40%
- 🟡 `Degrading (Hours)` — Risk 40–74%
- 🔴 `Imminent Block (< 30 Mins)` — Risk ≥ 75%

### TCP Anomaly Interceptor
Parses tunnel error strings in real time and classifies them into:
- **TCP RST (DPI Drop)** — Score 90/100
- **TLS Handshake Block** — Score 75/100
- **Generic Blackhole** — Score 45/100

### Latency Distribution Histogram
Buckets all probe samples into 5 frequency bins:

| Bin | Range | Interpretation |
|---|---|---|
| `<50ms` | Premium Stealth | Excellent |
| `51–120ms` | Good | Acceptable |
| `121–250ms` | Mid Latency | Marginal |
| `250ms+` | Heavy Jitter | Poor |
| `Drops` | ≥2000ms sentinel | Critical |

### Real-Time Traffic Entropy Profiler
Computes the **delta pattern entropy** of the latency stream — the mean absolute difference between consecutive valid samples, normalized to 0–100%. High entropy indicates chaotic, unpredictable traffic patterns consistent with active DPI throttling.

### Diagnostics Console
A monospace, timestamped, color-coded log stream with four severity levels:
- `[⚙️ INFO]` — Normal operational events
- `[⚠️ WARN]` — Degradation or anomaly detected
- `[🚨 EROR]` — Critical errors and failures
- `[✅ SUCC]` — Successful operations

---

## 🤖 Ferodo AI Engine v2.6.0-Enterprise

The `FerodoAI` engine runs a **6-stage deep analysis pipeline** after probing is complete:

```
Pings + Traces + Hops
         │
         ▼
 1. computeStatisticalMatrix()
    └─ Min, Max, Mean, Median, StdDev, IQR, BurstLossRate, OverallLoss
         │
         ▼
 2. analyzeTopology()
    └─ HiddenHops, IngressBottleneck, EgressBottleneck, UnderlayHealth
         │
         ▼
 3. detectDPISignatures()
    └─ Match against 7 known GFW/firewall attack patterns
         │
         ▼
 4. calculateHeuristicScore()
    └─ Weighted penalty model → Score 0–100 → Grade S/A/B/C/DEAD
         │
         ▼
 5. generateTacticalAdvice()
    └─ Contextual, data-driven mitigation commands
         │
         ▼
 6. compileConsoleReport()
    └─ Structured ASCII log dump with full telemetry
```

---

## 🔍 DPI Signature Detection

The engine scans all trace data against 7 documented attack signatures:

| Code | Name | Severity | Detection Logic |
|---|---|---|---|
| `SIG-DNS-POISON` | DNS Spoofing & Hijacking | 🔴 CRITICAL | Ultra-fast DNS + no TCP reach → GFW query hijacking |
| `SIG-SNI-RST` | SNI Inspection & RST Injection | 🔴 CRITICAL | TCP connects, TLS stalls → ClientHello interception |
| `SIG-DPI-THROTTLE` | Algorithmic Handshake Throttling | 🟠 HIGH | TLS time >> TCP×4 + base latency < 200ms |
| `SIG-TCP-BHOLE` | Targeted IP/Port Blackholing | 🔴 CRITICAL | >50% TCP SYN failure rate (no DNS spoofing) |
| `SIG-MTU-BHOLE` | Path MTU Discovery Failure | 🟠 HIGH | Handshakes succeed, large payloads silently dropped |
| `SIG-QOS-SHAPE` | Aggressive Traffic Shaping | 🟡 MEDIUM | Burst loss rate >40% + overall loss >10% |
| `SIG-SRV-OVERLOAD` | Server CPU Exhaustion | 🟡 MEDIUM | TLS >> TCP×4 + high base latency (VPS-side) |

---

## 📡 Supported Protocols

The config parser accepts single-URI format for:

- `vless://` — VLESS with any transport (TCP, WS, gRPC, XTLS, Reality)
- `vmess://` — VMess (Base64 encoded JSON)
- `trojan://` — Trojan-GFW

The application passes the parsed configuration to the **Xray-Core** binary for tunnel establishment on a dynamically selected local SOCKS5 port.

---

## 🚀 Usage

### Step 1 — Paste Config
Paste a single VLESS, VMESS, or Trojan URI into the top input box, or click **📋 Paste** to pull from clipboard.

### Step 2 — Configure (Optional)
Expand **Advanced Prober Settings** to customize:
- **Host:Port** — Target for MTR/traceroute
- **Anycast Nodes** — Comma-separated probe URLs (defaults to Cloudflare + Google)
- **Interval** — Probe interval in milliseconds (minimum 10ms, default 100ms)
- **uTLS Fingerprint** — TLS impersonation profile
- **Auto Self-Healing** — Enable clipboard-based hot-failover

### Step 3 — Scan
Click **▶ Ferodo DPI Scan Start**. The application will:
1. Parse and validate the config
2. Bind Xray-Core to a local SOCKS5 port
3. Begin concurrent overlay probing + OS traceroute
4. Update all visual widgets in real time
5. Auto-stop at 200 samples or on tunnel death

### Step 4 — Review
After the scan, the **Ferodo AI** panel displays:
- Numerical score and letter grade
- Network topology statistics
- Detected DPI threat signatures
- Actionable mitigation commands
- Full console log dump (copyable)

---

## ⚙️ Configuration Options

| Setting | Default | Description |
|---|---|---|
| Anycast Nodes | Cloudflare + Google `/generate_204` | HTTP probe target URLs |
| Host:Port | `cloudflare.com:443` | MTR / traceroute destination |
| Interval | `100` ms | Delay between overlay probes |
| uTLS | `chrome` | TLS ClientHello impersonation |
| Auto Self-Healing | Off | Auto-reload config from clipboard on failure |

---

## 🏆 Grading System

| Grade | Score Range | Status | Meaning |
|---|---|---|---|
| **S-TIER** | 95–100 | 👻 Ghost Mode | Undetectable. Perfect stealth routing. |
| **A-TIER** | 75–94 | 🟢 Stealth Active | Stable tunnel. Minimal GFW attention. |
| **B-TIER** | 50–74 | 🟡 Degraded | Anomalies detected. Active QoS shaping. |
| **C-TIER** | 25–49 | 🟠 Compromised | High DPI interference. Unstable. |
| **DEAD** | 0–24 | 🔴 Terminated | Route annihilated / null-routed by firewall. |

Score penalties are applied for:
- Mean latency above 150ms (`−0.05 × excess`)
- Jitter above 20ms (`−0.2 × excess StdDev`)
- Packet loss (`−loss^1.2`)
- Each CRITICAL signature (`−30 pts`)
- Each HIGH signature (`−15 pts`)
- Each MEDIUM signature (`−7 pts`)
- Each LOW signature (`−2 pts`)

---

## 📥 Export & Reporting

### 📸 Screenshot
Captures the entire Fyne window canvas as a PNG file via the native file-save dialog.

### 📄 Full Diagnostic Report (TXT)
Exports a structured text report containing:
- Timestamp and ISP information
- Full AI console log dump (statistical topology, DPI threats, actionable intel)
- Hop-by-hop route matrix table (Hop ID, IP, Loss%, Status)

### 📋 Log Copy
Both the Diagnostics Console and the AI Log Dump support one-click copy to system clipboard.

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---

<div align="center">

Built with ❤️ using **Go** + **Fyne** + **FerodoAI**

</div>


---

## 🎛️ Panel 4: 🌍 Ferodo IP Intelligence & Geo-Extractor (Enterprise Edition)

![Ferodo IP Intelligence & Geo-Extractor](https://github.com/user-attachments/assets/9dc6210e-c5d4-4fa5-8b31-8778444a7a9c)

An industrial-grade, highly concurrent IP and CIDR reconnaissance suite built in Go. This command center is engineered to ingest massive lists of raw targets or subnets and perform ultra-fast geolocation, ASN, and ISP intelligence gathering. Featuring a resilient multi-node API engine with automated key management and an ultra-fast offline data processing core, it acts as the ultimate intelligence hub for network administrators, security researchers, and proxy engineers.

### ✨ Core Engineering & Architecture

* **Multi-Node API Engine with Auto-Fallback:** Intelligently routes requests through primary intelligence providers (`IPGeolocation.io` or `IPWHO.IS`). If upstream limits are reached or a node fails, the engine automatically pivots to secondary pathways to guarantee continuous data extraction.
* **Dynamic API Key Management:** Prevents upstream rate-limiting by automatically distributing concurrent requests across a pool of up to 6 distinct, user-configurable authorization keys.
* **High-Speed Offline Engine:** Bypass external APIs entirely. Load massive offline datasets (like `geolite2-city-ipv4`). The engine utilizes a highly optimized, proprietary parsing algorithm to rapidly traverse millions of records, filtering by geographical parameters and extracting valid targets directly into your testing matrix.
* **Deep CIDR Intelligence:** Toggle the "Deep Scan" feature to let the engine's architecture seamlessly analyze broad subnets (e.g., `/24`, `/16`), resolving them into granular, actionable endpoint data prior to extraction.

### 📊 Scanner Intelligence Hub & Analytics

The right-side panel acts as a centralized command center, divided into three specialized tabs:

| Intelligence Tab | Features & Capabilities |
| :--- | :--- |
| 💻 **Terminal Log** | Real-time, asynchronous diagnostic console tracking upstream responses, limit thresholds, and successful data acquisitions. Includes local database filtering controls. |
| 📈 **Live Analytics** | Dynamically aggregates network intelligence. Displays a live Success Rate bar, Unique Target counts, and auto-calculates the **Top 5 Countries, ASNs, and ISPs** from the active dataset. |
| ⚙️ **Integrations** | Bridges the gap between reconnaissance and deployment. Includes automated notification pipelines, routing matrix exports, and targeted CDN isolation toggles. |

### 🧠 Smart Filtering & Auto-Sorting

* **Pro Table Filter:** A real-time, multi-parameter search engine. Input an IP, ASN (e.g., `AS13335`), Country, or ISP. The interface instantly isolates matches, utilizing a color-coded status indicator for rapid visual triage (🟨 **Gold** for matches, 🟩 **Green** for success, 🟥 **Red** for failures).
* **Targeted CDN Filter:** A unified toggle to instantly isolate specific CDN infrastructures (e.g., Cloudflare) within your massive dataset.
* **Intelligent Auto-Sort:** The sorting engine utilizes context-aware data typing to ensure flawlessly ordered datasets on the fly, regardless of whether the column contains strings, network addresses, or numerical IDs.

### 🚀 Integrations & Export Pipelines

* **Telegram Bot Integration:** Input your Bot credentials to fire off automated markdown telemetry to your device. The report summarizes extraction yields, success metrics, and top-level network topologies discovered during the session.
* **Routing Export:** With one click, extract successfully resolved targets and copy them directly to your clipboard, perfectly formatted for custom proxy and routing rulesets.
* **Dynamic Export Modes - Full Matrix:** Exports the entire parsed data grid as a readable TSV (Tab-Separated Values) format.
* **Dynamic Export Modes - Raw Targets:** Strips all metadata to output a clean, minimalist target list.
* **Dynamic Export Modes - Subnet Normalization:** Automatically normalizes singular target extractions into standardized `/24` subnets—perfect for feeding directly into secondary network scanners or deployment pipelines.

### 📖 Quick Start Guide

1. **Populate the Matrix:** Paste your raw targets or subnets into the left input box. Use the `Load CSV` feature in the Terminal tab to extract targets directly from offline databases.
2. **Configure the Engine:** Select your API mode (Auto-Fallback is recommended). Allocate your worker threads for concurrency and ensure your authorization keys are configured.
3. **Execute Extraction:** Click `START EXTRACTION`. The asynchronous worker pool will take over, dynamically updating the matrix and Live Analytics in real-time.
4. **Filter & Refine:** Use the Smart Filter to isolate specific ASNs, ISPs, or regions.
5. **Export:** Choose your export mode from the bottom control bar and hit `Save Selected Format`, or send a telemetry summary via the Telegram integration.

> *Disclaimer: This software is built for advanced network intelligence and routing optimization. Please ensure you comply with the rate limits and terms of service of the respective IP geolocation providers.*

## 🔑 License & Activation

This software operates on a strict online verification system, offering both **Free** and **Pro** access tiers. To obtain your unique license key and activate the application, please join our official Telegram community.

<div align="center">
  <img width="501" height="377" alt="License Verification System" src="https://github.com/user-attachments/assets/f7ecf0bc-53a0-4713-8b40-0fe08611f4c7" />
</div>

### 🚀 How to Get Your License Key:

1. **Join the Community:** Join our official [Telegram Channel](https://t.me/FeroRay).
2. **Request Access:** Follow the instructions in the channel to receive your personal **Free** or **Pro** license code.
3. **Activate:** Enter the provided code into the application's verification prompt to authenticate your access.

> **Note:** Each license is securely verified against our online database. Please do not share your personal key with others.