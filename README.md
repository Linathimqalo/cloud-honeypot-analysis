# cloud-honeypot-analysis
A comparative cloud honeypot project that utilises google cloud platform and microsoft azure. 

# Comparative Cloud Honeypot Threat Analysis: GCP vs Azure

This project investigates the behavior of real-world cyber threats using identical **T-Pot Community Edition honeypots** deployed on **Google Cloud Platform (GCP)** and **Microsoft Azure**. It compares attacker behavior, cloud performance, stability, and cost.

## 📅 Date

May 17, 2025

## 👤 Author

Linathi Mqalo

---

## 📚 Table of Contents

- [Introduction & Purpose](#introduction--purpose)
- [Environment Setup: GCP vs Azure](#environment-setup-gcp-vs-azure)
- [T-Pot Architecture & Components](#t-pot-architecture--components)
- [Attack Metrics & Threat Intelligence](#attack-metrics--threat-intelligence)
- [Azure Honeypot Insights](#azure--honeypot)
- [GCP Honeypot Insights](#google-cloud-platform)
- [Performance, Cost & Stability Comparison](#performance-cost--stability-comparison)
- [Conclusion & Insights](#conclusion--insights)
- [Appendix](#appendix)
- [Executive Summary](#executive-summary)

---

## 📌 Introduction & Purpose

Honeypots provide visibility into attacker behavior in controlled environments. This project aims to:

- Compare the attack volume and nature on GCP vs Azure
- Evaluate performance and stability across platforms
- Assess the cost implications
- Extract threat intelligence from behavior and payloads

---

## 🛠️ Environment Setup: GCP vs Azure

| Configuration Area | Google Cloud Platform (GCP) | Microsoft Azure |
|--------------------|------------------------------|------------------|
| VM Name            | `tpot-honeypot`              | `tpot-azure-vm`  |
| VM Type            | e2-standard-2 (2 vCPU, 8GB)  | D2s_v3 (2 vCPU, 8GB) |
| OS                 | Ubuntu Server 24.04 LTS      | Ubuntu Server 24.04 LTS |
| Disk               | 128GB SSD                    | 128GB SSD (LRS) |
| T-Pot Version      | CE 2023 Hive Mode            | CE 2023 Hive Mode |
| Ports Open         | 22, 80, 443, 64297, 1–65535  | 22, 80, 443, 64297, 1–65535 |
| SSH Auth           | RSA (.pem) via PuTTY/OpenSSH | RSA (.pem/.ppk) via PuTTY |
| Startup Date       | April 30, 2025               | April 02, 2025 |
| Monitoring Tools   | Kibana, Suricata, Portainer  | Kibana, Suricata, Portainer |
| Credits Used       | $7.10 / $300                 | $2.12 / $200 |

Azure Configuration
![image](https://github.com/user-attachments/assets/53088f3f-21f3-4ce3-8019-e2cf07592af7)

Google Cloud Configuration
![image](https://github.com/user-attachments/assets/180646da-fd75-428b-9b1e-cc47b94a22d7)

---

## 🧰 T-Pot Architecture & Components

Both environments used **T-Pot CE (Hive Mode)** with:

- **Suricata**: IDS/IPS engine for CVE detection
- **Cowrie**: SSH/Telnet honeypot (brute force logs)
- **Dionaea**: Malware collection (SMB, FTP, HTTP)
- **ElasticPot**: Elasticsearch honeypot
- **Honeytrap**: TCP/UDP port listener
- **Portainer**: Docker management UI
- **Kibana**: Dashboard visualization (Elasticsearch backend)

Azure Honeypots
![image](https://github.com/user-attachments/assets/3132bbe0-9592-497d-a4aa-4ca77f26c3f1)

Google Cloud Honeypots
![image](https://github.com/user-attachments/assets/bf54d899-b1a3-42ee-ae51-e81f0cd95271)

---

## 📊 Attack Metrics & Threat Intelligence

### Total Attacks Over ~14 Days
- **GCP**: 285,000+
- **Azure**: 156,000+

Both platforms showed high attacker interest, with distinct patterns per region.

---

## 🔐 Azure – Honeypot

### Top Targeted Ports:
- SSH (22), SMB (445), HTTP (80/443), Redis (6379), SOCKS (1080)

![image](https://github.com/user-attachments/assets/3f4cf669-f49f-431c-92f8-926fe37948c3)

### Common Attack Types:
- SSH brute-force
- CVE-based exploit attempts
- Malware transfer logs via Dionaea

### Frequent CVEs:
`CVE-2002-0013`, `CVE-2006-2369`, `CVE-2023-46604`, `CVE-2021-3449`, etc.

### Top Attacker Countries:
USA, China, UK, Netherlands, Russia, Germany, Iran, Canada, Turkiye, Seychelles

![image](https://github.com/user-attachments/assets/1ba2a576-8846-49ad-ac1c-353ed22e3b33)

---

## 🔐 Google Cloud Platform

### Top Targeted Ports:
- SSH (22), HTTP/HTTPS (443), VoIP (5060), SOCKS (1080), SMB (445)

![image](https://github.com/user-attachments/assets/619e0ddd-5475-4560-97b7-9b257e249c7d)

### Common Attack Types:
- Brute-force, scanning, CVE exploits, malware attempts

### Frequent CVEs:
`CVE-1999-0265`, `CVE-2019-11500`, `CVE-2021-35394`, etc.

### Top Attacker Countries:
USA, Romania, China, France, UK, Germany, Russia, Netherlands, Canada, Vietnam

![image](https://github.com/user-attachments/assets/eba6403e-0dfd-47c4-bcdb-389bb49d6a99)

---

## ⚙️ Performance, Cost & Stability Comparison

| Metric                 | GCP                            | Azure                          |
|------------------------|--------------------------------|--------------------------------|
| Uptime                 | Consistent, 1–2 restarts/day   | Stable early, issues over time |
| Kibana Stability       | Minor lags                     | Frequent 502/504 errors        |
| Memory Usage           | Required +RAM (9.75GB suggested) | Functional on 8GB w/ restarts  |
| Cost Burn Rate         | ~$1.78/day                     | ~$2.67/day                     |
| Credit Duration        | ~2+ months (est.)              | ~2–3 weeks (est.)              |
| Crash Recovery         | Mostly stable                  | VM agent errors, manual reboot |

---

## 💡 Conclusion & Insights

- **GCP** offered **better cost-efficiency** and more **stable uptime**, though with minor Kibana lags.
- **Azure** showed **stronger raw performance** but **less stability** and faster credit usage.
- Honeypots revealed persistent brute-force, malware, and CVE-targeted activity from global sources.
- Threat intelligence from Suricata and Cowrie offered insights into attacker tactics and priorities.

---

## 📎 Appendix

Additional figures and visuals were used to support findings (not included in this README):

- Attack maps, IOC dashboards
- Country-based attacker heatmaps
- Port scan visuals per platform

---

## 📝 Executive Summary

This study deployed identical T-Pot honeypots on **Google Cloud Platform** and **Microsoft Azure** to capture, compare, and analyze real-world cyberattacks. The platforms were exposed to the internet, logging events for 14 days.

Key takeaways:
- GCP received **more attack volume**, was **more cost-effective**, and easier to monitor.
- Azure had **higher initial performance** but became **less stable** during continuous uptime.
- Logs included thousands of **SSH brute-force attempts**, **known CVEs**, and **malware probes**.

### This project demonstrates:
- The **power of honeypots** in threat research
- A practical **comparison of cloud infrastructure behavior**
- Valuable training for **blue-team practitioners and students**

---

> 📡 For future work:
> - Automate threat log exports
> - Integrate alerts (e.g., Slack/email)
> - Expand to AWS or hybrid environments
> - Simulate segmented enterprise services

---
