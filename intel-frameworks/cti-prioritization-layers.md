# 🎯 CTI Prioritization Layers

CTI should prioritize threat data based on operational relevance, risk, and confidence.

---

## 🏗 1. Three Layers of Prioritization

### a. **Strategic**  
- Long-term trends, geo-political events, APT campaigns

### b. **Operational**  
- Actor TTPs, malware campaigns, sector targeting

### c. **Tactical**  
- IOCs, IPs, file hashes, YARA rules

---

## 🧠 2. Prioritization Criteria

| Factor         | Description                            |
|----------------|----------------------------------------|
| Relevance      | Is this threat applicable to your org? |
| Confidence     | Source reliability & data confidence   |
| Timeliness     | How current is this intel?             |
| Impact         | Potential effect if threat succeeds    |

---

## 🔗 3. Integrating Into SOC Workflow

- Tag threats with `impact`, `actor`, and `priority_level`
- Route to SOC for alert correlation
- Suppress stale IOCs automatically

---

## 📘 Reference

- ENISA Threat Intelligence Handbook
- Mandiant Threat Prioritization Matrix

