# 🛡️ Week 2 Penetration Testing Project

## 🔎 Reconnaissance & Footprinting

### 📌 Project Overview

As part of my cybersecurity training and practical penetration-testing exercises, I completed a reconnaissance and footprinting assessment using **Kali Linux**.

The assessment focused on gathering publicly observable information from an authorized target and performing network discovery within my authorized local network environment.

The objective was to understand how security professionals collect information about a target before moving into deeper security assessment activities.

---

## 🎯 Assessment Scope

| Category            | Details                         |
| ------------------- | ------------------------------- |
| 🔎 Primary Focus    | Reconnaissance & Footprinting   |
| 🐉 Operating System | Kali Linux                      |
| 🌐 Web Target       | networkwalks.com                |
| 🖥️ Network Target  | My authorized local LAN         |
| 🔐 Authorization    | Authorized security testing     |
| 🧪 Assessment Type  | Educational penetration testing |

---

## 🛡️ Authorization & Ethical Use

All activities documented in this project were performed within an authorized educational environment and against systems for which appropriate permission was available.

This project is intended strictly for cybersecurity education, ethical hacking practice, research, and professional development.

> ⚠️ Security testing, scanning, enumeration, or exploitation must never be performed against systems without explicit authorization.

---

# 🧰 Tools Used

The following tools were used during the reconnaissance and footprinting phase:

| Tool              | Purpose                                   |
| ----------------- | ----------------------------------------- |
| 🐉 Kali Linux     | Cybersecurity testing environment         |
| 🔍 WHOIS          | Domain and registration information       |
| 🌐 WhatWeb        | Web technology fingerprinting             |
| 📡 Nslookup       | DNS and IP resolution                     |
| 📥 cURL           | HTTP header inspection                    |
| 🛡️ Wafw00f       | WAF identification                        |
| 🗂️ DNSRecon      | DNS enumeration                           |
| 🛰️ Zenmap / Nmap | Network discovery and host identification |
| 💻 Windows CMD    | Local network information                 |

---

# 🔎 Activities Performed

## 1. WHOIS Reconnaissance

WHOIS was used to collect publicly available information about the target domain and identify relevant domain infrastructure, including name-server information.

### Security Relevance

WHOIS information can provide an initial understanding of how a domain is registered and what infrastructure may be associated with it.

---

## 2. WhatWeb Technology Fingerprinting

WhatWeb was used to identify technologies exposed by the target website.

The assessment identified technologies including:

* WordPress 7.0.4
* WP Download Manager 3.3.58

### Security Relevance

Technology fingerprinting can help security professionals identify software and components that may require additional security review.

> **Important:** Identifying a technology or version does not automatically mean that a vulnerability exists.

---

## 3. DNS & IP Resolution

`nslookup` was used to resolve the target domain and identify its associated IP address.

### Observed Result

```text
192.232.216.135
```

### Security Relevance

IP resolution provides information about the network location associated with a web service and can support further authorized infrastructure analysis.

---

## 4. HTTP Header Analysis

cURL was used to inspect the HTTP response headers:

```bash
curl -I networkwalks.com
```

The response also exposed the following WordPress REST API endpoint:

```text
/wp-json/
```

### Security Relevance

HTTP response information can assist with technology fingerprinting and further authorized enumeration.

---

## 5. Web Application Firewall Detection

Wafw00f was used to determine whether a Web Application Firewall was protecting the target.

### Observed Result

```text
ModSecurity (SpiderLabs)
```

### Security Relevance

Identifying defensive technologies helps security professionals understand the security architecture protecting a web application.

---

## 6. DNS Enumeration

DNSRecon was used to enumerate publicly accessible DNS information.

The assessment provided information relating to:

* Name servers
* Mail servers
* SPF/TXT records
* Service records
* DNS-related information

### Security Relevance

DNS information can help security professionals build a broader understanding of an organization's publicly exposed infrastructure.

---

# 🛰️ Network Discovery

In addition to web reconnaissance, I performed network discovery within my **authorized local LAN environment**.

Zenmap/Nmap was used to identify active hosts and examine available network information such as:

* IP addresses
* MAC addresses
* Active hosts
* Network topology

This exercise helped me understand how network discovery can be used during the initial stages of an authorized security assessment.

---

# 📊 Risk Analysis

| # | Finding                                | Observation                                  | Potential Impact                      | Risk      |
| - | -------------------------------------- | -------------------------------------------- | ------------------------------------- | --------- |
| 1 | Web technology information exposed     | WordPress and WP Download Manager identified | May assist technology fingerprinting  | 🟠 Medium |
| 2 | Server IP identifiable                 | Domain resolved to `192.232.216.135`         | Provides network-location information | 🟢 Low    |
| 3 | HTTP technical information exposed     | HTTP headers and `/wp-json/` identified      | May assist further enumeration        | 🟢 Low    |
| 4 | WAF technology identifiable            | ModSecurity identified                       | Reveals defensive architecture        | 🟢 Low    |
| 5 | DNS infrastructure information exposed | DNS, mail and service records identified     | May assist infrastructure profiling   | 🟠 Medium |

### ⚠️ Assessment Note

These observations represent information identified during reconnaissance and network discovery.

They **do not by themselves confirm vulnerabilities**.

No exploitation or vulnerability validation was performed during these activities.

---

# 🛡️ Recommendations

Based on the observations, the following security recommendations were identified:

### 1. Review Publicly Exposed Technology

Organizations should regularly review publicly exposed CMS platforms, plugins, frameworks, and web technologies.

### 2. Keep Software Updated

CMS platforms, plugins, frameworks, and other technologies should be regularly updated and monitored against current security advisories.

### 3. Review HTTP Headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 4. Review DNS Records

DNS records should be periodically reviewed to ensure that only required information and services are publicly exposed.

### 5. Properly Configure the WAF

The Web Application Firewall should remain enabled, properly configured, monitored, and regularly tuned.

### 6. Perform Regular Internal Network Discovery

Organizations should periodically scan their authorized internal networks to identify active devices and maintain infrastructure visibility.

---

# 📚 Key Learning Outcomes

Through this project, I gained practical experience with:

* 🔎 Reconnaissance methodology
* 🌐 Domain footprinting
* 🧩 Web technology fingerprinting
* 📡 DNS enumeration
* 🛡️ WAF identification
* 🛰️ Network discovery
* 🖥️ Host identification
* 📝 Professional security documentation

One of the most important lessons I learned is that **effective security testing begins with understanding the environment**.

---

# 📈 Assessment Progress

```text
PHASE 1 — RECONNAISSANCE & FOOTPRINTING

Reconnaissance       ████████████████████ 100% ✅
Footprinting         ████████████████████ 100% ✅
Network Discovery    ████████████████████ 100% ✅
Host Identification  ████████████████████ 100% ✅

Exploitation         ⏳ Not Performed
Vulnerability Test   ⏳ Not Performed
```

---

# 🧠 What This Project Taught Me

This project helped me understand that penetration testing is not simply about running tools or commands.

A professional security assessment requires me to understand:

```text
What was performed
        ↓
What was discovered
        ↓
Why it matters
        ↓
What risk it may create
        ↓
How the risk can be reduced
```

I also learned the importance of working within an authorized scope and documenting every stage of a security assessment professionally.

---

# 🏁 Conclusion

This Week 2 practical exercise strengthened my understanding of **reconnaissance, footprinting, DNS enumeration, web technology identification, WAF detection, and network discovery**.

Using Kali Linux and several security tools, I was able to gather and analyze publicly observable information about an authorized target and perform network discovery within my authorized local environment.

The experience has helped me develop a stronger foundation in ethical hacking and penetration testing while reinforcing the importance of authorization, documentation, and responsible security testing.

---

# 📸 Evidence

Screenshots and supporting evidence from the practical exercises are included in this repository.

### Evidence Categories

* WhatWeb Results
* Nslookup Results
* cURL Results
* Wafw00f Results
* DNSRecon Results
* WHOIS Results
* Zenmap/Nmap Network Discovery

---

## 🚀 Future Learning

For my next cybersecurity projects, I plan to continue developing my skills in:

* Network security
* Vulnerability assessment
* Web application security
* Penetration testing
* Security reporting
* Linux administration
* Threat detection and analysis

---

## 👤 Author

**Daraobong Ufot**

Cybersecurity Learner | Ethical Hacking | Network Security

---

### 🛡️ CYBERSECURITY • ETHICAL HACKING • NETWORK SECURITY

**Learn → Practice → Analyze → Secure**
