
# 🛡️ PENETRATION TESTING REPORT

### Footprinting & Network Scanning Phases

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

| **Field**                                       | **Details**                                                                                                           |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Pentester Name (Cybersecurity Professional)** | **Daraobong Ufot**                                                                                                    |
| **Program/Batch**                               | **Networkwalks Cybersecurity Program**                                                                                |
| **Date**                                        | **August 2026**                                                                                                       |
| **Modules completed**                           | **W2-PM1 (Multiple Kali Tools)**<br>**W2-PM5 (Zenmap Scanning)**                                                      |
| **Client/Target**                               | **1. Networkwalks — authorized target**<br>**2. My own local LAN Network**                                            |
| **Permission secured from client?**             | **Yes**                                                                                                               |
| **Phases covered**                              | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery<br>**Phase 3–5:** In Progress |

# 1. Liability Disclaimer

I performed these activities only on systems and devices where I had appropriate authorization or on devices and systems that I own myself.

All materials in this project are intended for educational, cybersecurity research, ethical hacking, and professional development purposes only.

Unauthorized access, scanning, enumeration, exploitation, or interference with computer systems may violate applicable laws and regulations.

Do not use the techniques, commands, or information contained in this repository against systems without explicit authorization.

The author, instructor, and Networkwalks are not responsible for misuse of the information contained within this project. Every action taken with this knowledge is the responsibility of the individual performing it.

**Security principle:** Always define and respect the authorized scope before performing reconnaissance or security testing.

# 2. Introduction

This report covers the footprinting of the `networkwalks.com` domain using multiple Kali Linux tools and the scanning of my own local network using Zenmap.

The footprinting activity focused on collecting publicly available information about the authorized target, while the network-scanning activity focused on identifying live hosts and understanding the structure of my authorized local network.

Together, these activities demonstrate how a cybersecurity professional can progress from gathering publicly available information to mapping hosts within an authorized network environment.

The activities were performed using Kali Linux for reconnaissance and a Windows environment with Zenmap for network discovery.

Each activity was documented with the tool or command used, the observed result, the security relevance of the finding, and supporting evidence where available.

# 3. Tools Used

The table below lists the tools used during the practical activities and their purposes.

| **Tool**          | **Purpose**                                                                |
| ----------------- | -------------------------------------------------------------------------- |
| **Kali Linux**    | Security testing and reconnaissance environment                            |
| **Windows**       | Local network identification and Zenmap environment                        |
| **WHOIS**         | Collect publicly available domain registration and name-server information |
| **WhatWeb**       | Fingerprint web technologies and identify CMS information                  |
| **Nslookup**      | Resolve the domain name to its associated IP address                       |
| **cURL -I**       | Inspect HTTP response headers                                              |
| **Wafw00f**       | Identify whether a Web Application Firewall is protecting the website      |
| **DNSRecon**      | Enumerate publicly accessible DNS information                              |
| **Zenmap / Nmap** | Discover active hosts within the authorized local network                  |
| **Windows CMD**   | Identify local IP and network configuration                                |

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

I performed authorized reconnaissance against the `networkwalks.com` domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, cURL, Wafw00f, and DNSRecon**.

Each tool was used to collect a different type of information about the target.

First, I used **WHOIS** to obtain publicly available domain registration information and identify relevant domain infrastructure, including name-server information.

I then used **WhatWeb** to identify technologies used by the website. The observed results identified:

* **WordPress 7.0.4**
* **WP Download Manager 3.3.58**

Technology identification can help security professionals understand what software components may require additional security review.

Using **Nslookup**, I resolved the domain name to its associated IP address.

The observed result was:

```text
192.232.216.135
```

I then used **cURL** with the `-I` option to inspect the HTTP response headers:

```bash
curl -I networkwalks.com
```

The response provided additional information about the web application and exposed the WordPress REST API endpoint:

```text
/wp-json/
```

Next, I used **Wafw00f** to determine whether a Web Application Firewall was protecting the website.

The observed result identified:

```text
ModSecurity (SpiderLabs)
```

Finally, I used **DNSRecon** to enumerate publicly accessible DNS information.

The results provided information relating to:

* Name servers
* Mail servers
* SPF/TXT records
* Service records
* DNS-related information

These activities provided different perspectives of the publicly observable infrastructure associated with the target.

---

## 4.2 Network Scanning With Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my authorized local network.

The objective was to identify my local IP address and subnet, discover active hosts, identify available IP and MAC address information, and examine the network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet.

I then entered my authorized network range into Zenmap and performed host discovery.

### My Network Details

```text
Local IP Address: [192.162.1.14]
Subnet: [255.255.255.0]
Gateway: [192.168.1.1]
```

### Hosts Identified

```text
[10.0.0.1]
[10.0.0.4]
[10.0.0.19]
[10.0.0.5]
```

### MAC Addresses

```text
[00:1A:2B:3C:4D:5E]
[00:1A:2B:3C:4D:5E]
[00:1A:2B:3C:4D:5E]
[00:1A:2B:3C:4D:5E]
```

After completing the scan, I reviewed the **Topology** section in Zenmap to understand how the identified hosts were connected within the network.

> **Note:** The IP addresses, MAC addresses, number of hosts, and topology information above should be replaced with the actual results from my own network scan before final submission.

# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network-scanning activities, I identified the following potential security risks.

| **#** | **Risk / Finding**                           | **Evidence / Observation**                                    | **Potential Impact**                                                                                            | **Risk Level** |
| ----- | -------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | -------------- |
| **1** | Web technology information exposed           | WhatWeb identified WordPress and WP Download Manager          | Attackers may use exposed technology/version information to identify software requiring further security review | **🟠 Medium**  |
| **2** | Server IP address identifiable               | Nslookup resolved the domain to `192.232.216.135`             | Provides information about the network location of the web service                                              | **🟢 Low**     |
| **3** | HTTP technical information exposed           | cURL returned HTTP response headers and exposed `/wp-json/`   | May assist technology fingerprinting and further enumeration                                                    | **🟢 Low**     |
| **4** | WAF technology identifiable                  | Wafw00f identified ModSecurity (SpiderLabs)                   | Reveals information about the web application's security architecture                                           | **🟢 Low**     |
| **5** | DNS infrastructure information exposed       | DNSRecon identified DNS, mail and service-related records     | DNS information can help build a broader infrastructure profile                                                 | **🟠 Medium**  |
| **6** | Multiple live hosts visible on local network | Zenmap identified active hosts on my authorized local network | Provides visibility into devices present on the network                                                         | **🟠 Medium**  |

### Risk Level Key

* 🔴 **Critical**
* 🟠 **Medium**
* 🟢 **Low**

The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical activities primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed during these activities.

Therefore, the presence of information such as a software version, IP address, DNS record, HTTP endpoint, or active host does not by itself prove that a system is vulnerable.

Additional authorized security testing would be required to confirm any suspected vulnerability.

# 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

### 1. Review Publicly Exposed Technology Information

Organizations should regularly review what information about their web technologies, CMS platforms, plugins, and frameworks is publicly visible.

### 2. Keep Software Updated

CMS platforms, plugins, frameworks, and other web technologies should be regularly updated and reviewed against current security advisories.

### 3. Review HTTP Headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 4. Review DNS Records Regularly

DNS records should be periodically reviewed to ensure that only required information and services are publicly exposed.

### 5. Properly Configure and Monitor the WAF

The Web Application Firewall should remain enabled, properly configured, monitored, and regularly tuned according to the organization's security requirements.

### 6. Perform Regular Internal Network Discovery

Organizations should periodically scan their authorized internal networks to identify active devices and maintain visibility of their infrastructure.

### 7. Investigate Unknown Devices

Any unexpected device discovered during an authorized network scan should be investigated and verified.

### 8. Maintain Network Documentation

Network topology and device information should be documented and updated regularly.

### 9. Perform Security Testing With Authorization

Reconnaissance, scanning, enumeration, and other security-testing activities should only be performed against systems and networks where appropriate authorization has been provided.

# 7. Conclusion

During Week 2 of my cybersecurity training, I completed practical activities covering **footprinting, reconnaissance, and network scanning**.

In the footprinting activity, I used six Kali Linux tools to collect and analyze information about the authorized target.

I learned how:

* **WHOIS** can provide domain and infrastructure information.
* **WhatWeb** can identify web technologies.
* **Nslookup** can resolve domain names to IP addresses.
* **cURL** can inspect HTTP response headers.
* **Wafw00f** can identify Web Application Firewall technology.
* **DNSRecon** can provide additional DNS information.

In the network-scanning activity, I used **Zenmap** to identify my local network configuration and discover active hosts within my authorized network.

I also learned how network scanning can provide information about IP addresses, MAC addresses, active hosts, and network topology.

The exercises showed me that information gathering is an important part of cybersecurity. Before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain:

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

Most importantly, these exercises reinforced the requirement that reconnaissance and network scanning must always be conducted within an authorized scope.

This project represents another step in my development as a cybersecurity professional and contributes to my practical experience in **ethical hacking, network security, reconnaissance, and security assessment**.

# 8. Evidence Collected

Screenshots collected during the practical activities should be stored in the `screenshots/` folder of this repository.

### Footprinting Evidence

* WHOIS output
* WhatWeb output
* Nslookup output
* cURL output
* Wafw00f output
* DNSRecon output

### Network Scanning Evidence

* Windows `ipconfig` output
* Zenmap scan results
* Host/IP information
* MAC address information
* Network topology

## Suggested Screenshot Structure

```text
screenshots/
│
├── 01-whois.png
├── 02-whatweb.png
├── 03-nslookup.png
├── 04-curl.png
├── 05-wafw00f.png
├── 06-dnsrecon.png
├── 07-ipconfig.png
├── 08-zenmap-scan.png
└── 09-zenmap-topology.png
```

---

# 👤 Author

**Daraobong Ufot**

Cybersecurity Learner | Ethical Hacking | Network Security

**CYBERSECURITY • ETHICAL HACKING • NETWORK SECURITY**

> Learn → Practice → Analyze → Secure
