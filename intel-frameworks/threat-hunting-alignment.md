# 🧭 Aligning Threat Intelligence with Threat Hunting

To bridge intelligence and operations, CTI must feed into active threat hunting workflows.

---

## 🛠 1. Intelligence-Driven Hunting

Threat hunting starts with a **hypothesis** derived from:

- TTPs from CTI reports (e.g., MITRE ATT&CK)
- Recent IOC sightings
- Behavior-based analytics

---

## 📚 2. Use Case Mapping (ATT&CK)

| Use Case              | ATT&CK Technique              |
|------------------------|-------------------------------|
| Credential Dumping     | T1003                         |
| Persistence via Service | T1543.003                    |
| C2 via DNS             | T1071.004                     |

---

## 🔄 3. Feedback Loop

After hunts:
- Share findings back to CTI team
- Update IOCs / behavioral rules
- Refine hunting logic

---

## ✅ Best Practices

- Always contextualize IOCs with threat actor motivations
- Use behavior-first detection, not signature-only
