# 📡 MISP Integration Walkthrough

This walkthrough outlines how to ingest, enrich, and export threat intelligence using [MISP (Malware Information Sharing Platform)](https://www.misp-project.org/).

---

## 🎯 Objective

- Ingest IOCs from CTI feeds
- Create structured MISP events
- Automate enrichment with modules
- Export data to other tools (e.g., SIEM, TIP)

---

## 🛠️ Step-by-Step Setup

### 1. 🔐 Install MISP (local or dockerized)

```bash
git clone https://github.com/MISP/MISP.git /var/www/MISP
cd /var/www/MISP
bash INSTALL.sh
```
Or use docker-compose:

→ https://github.com/MISP/misp-docker

## 2. 🧾 Add API Key

- Login as admin

- Go to Automation > Auth keys

- Generate API key

Set it in your Python script:

```python
misp_key = "your_api_key"
misp_url = "https://localhost"
```

## 3. 📥 Create Event from IOC Feed

Example using PyMISP:

```python
from pymisp import ExpandedPyMISP, MISPEvent, MISPAttribute

misp = ExpandedPyMISP(misp_url, misp_key, False)

event = MISPEvent()
event.info = "CTI Feed – Ransomware X"
event.distribution = 1
event.analysis = 1
event.threat_level_id = 2
misp_event = misp.add_event(event)

# Add attributes
misp.add_named_attribute(misp_event['Event']['uuid'], 'ip-dst', '185.62.189.194')
misp.add_named_attribute(misp_event['Event']['uuid'], 'domain', 'malicious-c2.site')
```

## 4. 🔍 Enrichment

- Go to the web UI → Event → Actions → Enrichment

Common modules:

- whois – domain registration

 -passivetotal – passive DNS

- hashlookup – check hash against known malware DB

## 5. 📤 Export

- Export as STIX 2.0 / OpenIOC / CSV / Suricata rules

Sync with another MISP instance or SIEM using feed connectors

```bash
curl -H "Authorization: $misp_key" -X GET $misp_url/events/stix/download
```

## 🧠 Best Practices

- Tag all indicators with TLP and threat actor (if known)

- Enable taxonomy support for mapping ATT&CK

- Use correlation graph to visualize shared indicators

## 📚 References

- MISP Official Documentation

 -PyMISP Library

- MITRE ATT&CK Taxonomy in MISP

## 📝 Notes

- MISP supports SIGHTINGS for community collaboration

- Can integrate with tools like TheHive, Splunk, Graylog, Cortex

- Supports automatic feed ingestion (URL, JSON, CSV)




