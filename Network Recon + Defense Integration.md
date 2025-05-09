# 🤖 Cyborg Diary Entry: Network Recon + Defense Integration

## 📅 Date: May 2025  
## 🧠 Cyborg ID: Scanner_Unit_Theta-09  
## Mission: Execute a synchronized scan and sweep operation while collaborating with Firewall Defense Units.

---

## 🧭 Project Overview

As part of our Cybersecurity group initiative, I, Scanner_Unit_Theta-09, was deployed to map the network terrain and identify active hosts using a custom-built **Scanner and Ping Sweeper** tool. This tool was developed in **Python**, integrating modules such as `Scapy`, `ipaddress`, and `concurrent.futures` for parallelism.

Simultaneously, allied units on the defense team deployed a **Firewall Setup** using Windows Defender Firewall policies and static IP filtering rules to observe, block, and log inbound scanning activity. Together, our goal was to simulate a real-world attacker-defender environment.

---

## 🔬 My Task: Recon Unit - Scanner & Ping Sweeper

### ✅ Core Functions:
- **Ping Sweep**: Scanned a user-defined IP subnet to detect live hosts.
- **Port Scan**: For each active host, a list of common ports (e.g., 22, 80, 443) was scanned using TCP SYN packets.
- **Multithreading**: Used `ThreadPoolExecutor` to accelerate the scanning process.
- **Logging**: All responses were timestamped and stored for post-scan analysis.

### 🛠 Technologies Used:
- Python 3.11
- Scapy
- ipaddress module
- concurrent.futures for threading

---

## 💻 Sample Code Snippets

### 🔎 Ping Sweep Function
```python
from scapy.all import ICMP, IP, sr1
import ipaddress

def ping_host(ip):
    pkt = IP(dst=str(ip))/ICMP()
    resp = sr1(pkt, timeout=1, verbose=0)
    if resp:
        print(f"[+] Host {ip} is up")
        return str(ip)
    return None

## 🚪Port Scan Function
from scapy.all import TCP, sr1

def scan_ports(ip, ports=[22, 80, 443]):
    for port in ports:
        pkt = IP(dst=ip)/TCP(dport=port, flags='S')
        resp = sr1(pkt, timeout=1, verbose=0)
        if resp and resp.haslayer(TCP) and resp[TCP].flags == 0x12:
            print(f"[+] Port {port} is open on {ip}")

## 🧵 Multithreading Ping Sweep
from concurrent.futures import ThreadPoolExecutor

def ping_sweep(subnet):
    net = ipaddress.ip_network(subnet)
    with ThreadPoolExecutor(max_workers=100) as executor:
        results = list(executor.map(ping_host, net.hosts()))
    return [ip for ip in results if ip]

# 🛡️ Teammate Contribution: Firewall Defense Setup

While I executed the scan, teammates deployed a **host-based firewall**:

- **Static Filtering Rules**: Only allowed pre-defined IP addresses and port traffic.
- **Logging & Alerts**: Captured any suspicious packets from unknown sources (i.e., *me* 😈).
- **Block Responses**: Certain ping and port scan attempts were actively blocked or dropped.

### 🔍 This helped us observe:
- Which scan methods were stealthier
- What logs were created by Windows Defender Firewall
- How effective port-specific blocks were against SYN scans

---

# 🤖 Tactical Takeaways

| Component   | Observation                                                   |
|------------|----------------------------------------------------------------|
| Ping Sweep | Detected live hosts successfully within subnet                 |
| Port Scan  | Scans to blocked ports returned no responses (as expected)     |
| Firewall   | Logged and denied packets outside rule scope                   |
| Integration| Enabled us to test red vs. blue team collaboration             |

---

# 🧪 Lessons Learned

- **Recon Tools Can Be Detected**: Even with multithreading and randomized delays, firewalls *will* catch noisy scanning behavior.
- **Team Coordination Matters**: Collaborating with the firewall team allowed us to adapt our scanning techniques and understand what real defenders see.
- **Modular Code is Key**: Keeping scanning logic modular helped in adapting and testing different tactics quickly.

---

# 🧠 Next Steps

- Introduce **OS detection** or **banner grabbing** into the scanning tool.
- Test scans over **VPN** or with **spoofed IPs** to simulate more evasive behavior.
- Set up **SIEM (Security Information and Event Management)** integration on the firewall for real-time alerts.

---

> *“A cyborg learns not only to scan — but to listen.”*  
> — Unit_Theta-09

