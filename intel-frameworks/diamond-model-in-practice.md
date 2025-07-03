# 💠 Diamond Model in Practice

The Diamond Model provides a structured analytic framework for understanding intrusions through four core features: Adversary, Capability, Infrastructure, and Victim.

---

## 🔹 1. Overview

- **Adversary**: The threat actor or group (e.g., APT29)
- **Capability**: Tools, malware, or techniques used (e.g., Cobalt Strike, Mimikatz)
- **Infrastructure**: C2 servers, domains, IPs
- **Victim**: The targeted organization, sector, or geography

---

## 🔄 2. Pivoting Between Features

By correlating elements (e.g., shared infrastructure or reused tools), defenders can uncover:
- Related incidents
- Attribution patterns
- Attack timelines

Example:

```plaintext
Victim → Capability → Infrastructure → Adversary
```

## 🎯 3. Applications in CTI

- Threat grouping and clustering

- Attribution support

- Hunting unknown victims or infrastructure

## 📌 Reference

Diamond Model Whitepaper - https://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf



