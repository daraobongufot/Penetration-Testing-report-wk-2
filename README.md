PENETRATION TESTING REPORT
FOOTPRINTING & NETWORK SCANNING PHASES
W2-PM | CYBERSECURITY |  NETWORKWALKS

Pentester Name
(Cybersecurity Professional)	Ufot Daraobong E
Program/Batch	B082-Networkwalks
Date	21 August 2026
Modules completed	W2-PM1 (Multiple Kali Tools)
W2-PM5 (Zenmap Scanning)
Client/Target	1. Networkwalks (secured written permission already)
Permission secured from client?	Yes
Phases covered	Phase 1: Reconnaissance & Footprinting
Phase 2: Scanning & Network Discovery
Phase 3-5: In Progress


1. Liability Disclaimer
I hereby confirm that I performed these security testing activities only on systems and domains for which I had authorized permission to test. These activities were conducted for educational and research purposes. I did not intentionally attempt to damage, disrupt, or gain unauthorized access to any system.
All commands and tools used in this report were executed within the authorized scope of the assessment. Any information obtained during the assessment is documented solely for security analysis and educational purposes.

2. Introduction
This report documents the reconnaissance and security assessment activities performed against networkwalks.com using multiple tools available in Kali Linux.
The assessment focused on gathering publicly available information about the target domain and examining its externally visible web and DNS infrastructure. The activities included domain registration lookup, web technology fingerprinting, DNS resolution, HTTP response header analysis, Web Application Firewall detection, and DNS record enumeration.
The objective was to understand the information that can be obtained about the target from an external perspective and identify any security-relevant information that may require further review.
All activities were performed within the authorized scope of the assessment.
3. Tools Used
1.	Tool	Purpose
2.	Kali Linux	Operating system used for reconnaissance activities
3.	WHOIS	Obtaining domain registration information
4.	WhatWeb	Fingerprinting web technologies and services
5.	NSLookup	Resolving the domain name to its IP address
6.	cURL	Reading HTTP response headers
7.	WAFW00F	Detecting whether a Web Application Firewall is present
8.	DNSRecon	Enumerating DNS records
9.	
4. Activities Performed
4.1 Footprinting & Reconnaissance
I performed reconnaissance against networkwalks.com using several Kali Linux tools. Each tool was used to collect a different type of information about the target.
First, I used WHOIS to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.
I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.0.4 and WP Download Manager 3.3.58, along with other information exposed by the website.
Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.
4.2 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts.

The example results provided in the practical identified four live hosts:
•	10.0.0.1
•	10.0.0.4
•	10.0.0.19
•	10.0.0.5
The example results also included four MAC addresses.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.
Note: The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report
5. Risk Analysis / Impact
Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.
#	Risk / Finding	Evidence / Observation	Potential Impact	Risk Level
1	Web technology information exposed	WhatWeb identified WordPress and WP Download Manager	Attackers may use exposed technology/version information to identify software requiring further security review	● Medium
2	Server IP address identifiable	Nslookup resolved the domain to 192.232.216.135	Provides information about the network location of the web service	● Low
3	HTTP technical information exposed	Curl returned HTTP response headers and exposed /wp-json/	May assist technology fingerprinting and further enumeration	● Low
4	WAF technology identifiable	Wafw00f identified ModSecurity (SpiderLabs)	Reveals information about the web application’s security architecture	● Low
5	DNS infrastructure information exposed	DNSRecon identified DNS, mail and service-related records	DNS information can help build a broader infrastructure profile	● Medium
6	Multiple live hosts visible on local network	Zenmap identified four live hosts in the example network	Unknown or unauthorized devices may potentially be present on a network	● Medium




6. Recommendations
Based on the observations from these activities, the following security improvements are recommended to address the information disclosure risks identified during the reconnaissance and network scanning exercises.
6.1 Web Application Hardening
Review Publicly Exposed Technology Information
Organizations should regularly review what information about their web technologies, content management systems, and plugins is publicly visible. The use of tools like WhatWeb can reveal detailed technology stacks to anyone on the internet, which can be used by attackers to identify known vulnerabilities in specific versions. Conducting regular self-assessments using the same tools as potential adversaries helps organizations understand their public footprint and take corrective action.
Keep Software Updated
CMS platforms, plugins, themes, and other web technologies should be regularly updated and reviewed against current security advisories. Outdated software is one of the most common entry points for attackers, as publicly disclosed vulnerabilities in older versions are well-documented and widely exploited. Organizations should establish a patch management schedule that prioritizes security updates and monitors vendor security bulletins.
Review HTTP Headers
HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed. Headers such as Server, X-Powered-By, and the exposure of API endpoints like /wp-json/ can provide attackers with valuable fingerprinting information. While these headers alone do not constitute a vulnerability, they reduce the attacker's workload by eliminating the need for discovery. Organizations should consider removing or obfuscating revealing headers where possible.
Review DNS Records Regularly
DNS records should be checked periodically to ensure that only required information and services are publicly exposed. The information gathered through DNS enumeration can help attackers build a comprehensive profile of an organization's infrastructure, including mail servers, subdomains, and service configurations. Regularly auditing DNS records helps ensure that outdated or unintentionally exposed records are removed.
Properly Configure and Monitor the WAF
Keep the Web Application Firewall (ModSecurity) enabled, properly configured, and actively tuned, since it already blocks naive attacks. However, WAFs are not set-and-forget solutions; they require ongoing tuning to reduce false positives and adapt to new threat patterns. Organizations should regularly review WAF logs, update rule sets, and test configurations to ensure they are providing effective protection without disrupting legitimate traffic.
Network Security Practices
Perform Regular Internal Network Discovery
Organizations should periodically scan their own networks to identify active devices and maintain visibility into their environment. Regular network discovery helps detect unauthorized devices, rogue access points, and misconfigured systems that may have been added without proper change management. This practice also assists in maintaining accurate asset inventories and identifying shadow IT.
Investigate Unknown Devices
Any unexpected device discovered during network scanning should be immediately investigated and verified. Unknown devices could represent unauthorized access points, compromised systems, or devices that have been connected without security review. Organizations should have a formal process for investigating and remediating unauthorized network assets.
Maintain Network Documentation
Network topology and device information should be documented and updated regularly. Accurate documentation supports incident response, change management, and security assessments by providing a clear picture of the authorized network environment. When network documentation is maintained properly, unauthorized or unexpected devices become much easier to identify.
6.3 Operational Guidance
Perform Security Testing with Authorization
Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided. Unauthorized scanning can be considered a hostile act in many jurisdictions and may violate terms of service, laws, or regulations. Always ensure written authorization is in place before conducting any security testing, and maintain clear scoping documents that define what systems are included and what testing methods are permitted.
7. Conclusion
During Week 2 of the Cybersecurity & Ethical Hacking Internship, practical activities covering footprinting, reconnaissance, and network scanning were successfully completed. These exercises provided hands-on experience with both information gathering techniques and the tools used by security professionals to assess the security posture of target environments.
In the footprinting activity, six Kali Linux tools were employed to collect information about the target domain. Through this process, I learned how WHOIS can provide domain registration and ownership information, WhatWeb can identify web technologies and their versions, Nslookup can resolve domain names to IP addresses and retrieve DNS records, Curl can inspect HTTP response headers for technical disclosures, Wafw00f can identify the presence and type of Web Application Firewall, and DNSRecon can provide comprehensive DNS infrastructure information. Each tool contributed a different piece of the overall information puzzle, demonstrating the value of a multi-tool approach to reconnaissance.
In the network scanning activity, Zenmap was used to identify local network configurations and discover active hosts. This exercise provided practical experience with network discovery techniques, including the collection of IP and MAC address information and the creation of network topology visualizations. The ability to map a network and identify live hosts is a foundational skill for both security assessments and network administration.
The exercises demonstrated that information gathering is a critically important phase of any cybersecurity assessment. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses. This passive and active reconnaissance forms the foundation upon which further testing is built, allowing for more targeted and efficient vulnerability identification.
I also learned that technical findings must be documented clearly and professionally. A well-structured cybersecurity report should explain what actions were performed, what evidence was discovered, what the observations mean in context, what risks they may create, and what can be done to reduce those risks. This report structure ensures that findings are actionable and that decision-makers can understand both the technical details and the business implications of security issues.
Finally, this exercise reinforced an essential ethical principle: reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab, with all necessary permissions in place. The skills and methodologies practiced during this week will serve as a foundation for more advanced penetration testing activities, but they must always be applied with proper authorization, clear scoping, and a commitment to ethical conduct.
