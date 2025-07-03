# 🧪 IOC Parsing Demo

This demo shows how to extract and normalize Indicators of Compromise (IOCs) from raw threat feeds using Python.

---

## 🧠 Goal

Transform unstructured data into structured indicators (IPs, hashes, URLs) for use in SIEMs or threat platforms.

---

## 📂 Sample Feed

malicious domain: hxxp://evil[.]site
file hash (sha256): b19a3d...e25f1a
attacker IP: 45.155.204.234


---

## ⚙️ Python Script (ioc_parser.py)

```python
import re

text = open('raw_feed.txt').read()

ips = re.findall(r"\b(?:\d{1,3}\.){3}\d{1,3}\b", text)
domains = re.findall(r"h..p://[^\s\[]+", text)
hashes = re.findall(r"[a-fA-F0-9]{64}", text)

print("[+] IPs:", ips)
print("[+] Domains:", domains)
print("[+] Hashes:", hashes)
```

## Output

```less
[+] IPs: ['45.155.204.234']
[+] Domains: ['hxxp://evil.site']
[+] Hashes: ['b19a3d...e25f1a']
```

## 📌 Usage

- Convert hxxp → http before ingesting

- Feed into MISP or SIEM for correlation
