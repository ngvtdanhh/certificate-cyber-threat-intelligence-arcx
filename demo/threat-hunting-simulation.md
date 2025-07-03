# ⚔️ Threat Hunting Simulation (APT Scenario)

This simulation demonstrates how to use CTI + logs to identify suspicious activity linked to APT behavior.

---

## 📘 Scenario

Red team emulates APT29 (Cozy Bear) using:

- C2 via `onecloud-storage.com`
- Credential dumping (via procdump.exe)
- Exfil via HTTPS at odd hours

---

## 🔍 Steps

### 1. IOC Enrichment

From CTI feed:

```yaml
Domain: onecloud-storage.com

SHA256: 66ab...d9d2

Check DNS, passive DNS, and host logs.
```

---

### 2. Log Hunting (SIEM Query)

```sql
index=windows_logs
| where process_name="procdump.exe"
| stats count by host, user, timestamp
```
→ Unexpected use on DC01 by user svc-backup.

## 3. Network Detection

```sql
index=proxy_logs
| where dest_domain="onecloud-storage.com" AND bytes_out > 1MB
```

→ Shows large HTTPS outbound traffic at 03:14 UTC.

## 🧠 Result

- Confirmed lateral movement and data exfiltration.

- IOCs matched CTI and triggered alert escalation.

## 💡 Lessons

- CTI gives starting point

- Logs + detection rules = validation

- Enrich → Hunt → Triage → Report

