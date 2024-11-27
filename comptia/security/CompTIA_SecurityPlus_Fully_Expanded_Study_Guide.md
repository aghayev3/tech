
# CompTIA Security+ (SY0-601) Study Guide

## Domain 1: Attacks, Threats, and Vulnerabilities

### 1.1 Threat Actors and Their Characteristics
- **Types of Threat Actors:**
  - **Script Kiddies:** Inexperienced attackers who rely on prebuilt tools; often opportunistic.
  - **Hacktivists:** Motivated by political or social causes; focus on defacement or information leaks.
  - **Insider Threats:** Employees, contractors, or partners misusing access; may be malicious or accidental.
  - **Organized Crime:** Sophisticated groups aiming for financial gain using ransomware, phishing, or fraud.
  - **Nation-States:** State-sponsored cyberattacks with significant resources; often target critical infrastructure.
  - **APTs (Advanced Persistent Threats):** Long-term campaigns targeting organizations with stealth and persistence.

---

### 1.2 Attack Vectors
- **Vectors:**
  - **Email:** Phishing, spear phishing, whaling.
  - **Web Applications:** Exploiting vulnerabilities via SQL injection, XSS.
  - **Removable Media:** USB drives with malware.
  - **Cloud Services:** Misconfigured storage, API exploits.
  - **Wireless Networks:** Evil twin attacks, rogue access points.
- **Real-World Examples:**
  - Target data breach (2013): Phishing email led to stealing credentials.
  - Colonial Pipeline ransomware attack (2021): Resulted in fuel shortages.

---

### 1.3 Social Engineering Attacks
- **Techniques:**
  - **Phishing:** Deceptive emails to steal credentials.
  - **Spear Phishing:** Targeted phishing attacks aimed at specific individuals.
  - **Whaling:** Targets executives or high-ranking officials.
  - **Pretexting:** Impersonating someone to extract information.
  - **Baiting:** Offering enticing items like free USB drives infected with malware.
  - **Tailgating:** Following authorized personnel into restricted areas.
  - **Dumpster Diving:** Retrieving confidential information from discarded materials.
- **Defense:**
  - User education, spam filters, and two-factor authentication.

---

### 1.4 Malware and Indicators of Compromise
- **Types of Malware:**
  - **Viruses:** Requires user interaction; spreads by infecting files.
  - **Worms:** Self-replicating and spreads without user input.
  - **Trojan Horses:** Disguised as legitimate software but malicious.
  - **Ransomware:** Encrypts data; demands payment for decryption keys.
  - **Spyware:** Gathers sensitive information; keyloggers are a common type.
  - **Rootkits:** Provides persistent administrative-level access.
  - **Adware:** Displays unwanted advertisements; may track user behavior.
  - **Botnets:** Networks of compromised devices controlled remotely.
- **Indicators of Compromise (IoCs):**
  - Unusual outbound traffic, increased CPU/network usage, unauthorized access attempts.

---

### 1.5 Network and Application Attacks
- **Common Network Attacks:**
  - **Man-in-the-Middle (MITM):** Intercepts and alters communication between parties.
  - **DDoS:** Overwhelms a target system with excessive traffic.
  - **DNS Poisoning:** Redirects users to malicious websites by tampering with DNS.
  - **MAC Spoofing:** Fakes a device's MAC address to bypass security.
  - **ARP Poisoning:** Associates the attacker's MAC address with the IP of a legitimate device.
- **Common Application Attacks:**
  - **SQL Injection:** Executes malicious queries on a database.
  - **XSS (Cross-Site Scripting):** Injects malicious scripts into web pages viewed by users.
  - **Buffer Overflow:** Exploits memory to execute arbitrary code.

---

### 1.6 Vulnerability Scanning and Penetration Testing
- **Vulnerability Scanning:**
  - Identifies weaknesses in systems.
  - Tools: Nessus, OpenVAS, Qualys.
- **Penetration Testing:**
  - Simulates attacks to exploit vulnerabilities.
  - **Phases:**
    1. **Planning:** Define scope and objectives.
    2. **Discovery:** Gather information about the target.
    3. **Exploitation:** Attempt to exploit vulnerabilities.
    4. **Reporting:** Document findings and recommendations.

---

### 1.7 Threat Intelligence and Threat Hunting
- **Threat Intelligence:**
  - **Sources:** OSINT, ISACs, proprietary feeds.
  - **Usage:** Identifying potential attacks, improving defenses.
- **Threat Hunting:**
  - Proactively searches for hidden threats.
  - Techniques: Behavior analysis, anomaly detection.
  - Tools: SIEM (Security Information and Event Management), EDR (Endpoint Detection and Response).

---

### 1.8 Real-World Scenarios
1. **Example 1:**
   - An attacker gains access to a corporate network using spear phishing.
   - Uses lateral movement to access sensitive databases.
   - Deploys ransomware, encrypting critical data.
2. **Example 2:**
   - SQL injection vulnerability allows attackers to extract user credentials from a web application.
3. **Example 3:**
   - Insider threat: An employee leaks confidential company information for personal gain.

---


# CompTIA Security+ (SY0-601) Study Guide

## Domain 2: Architecture and Design

### 2.1 Secure Network Architecture
- **Network Segmentation:**
  - **Purpose:** Limits lateral movement of attackers; improves performance.
  - **Types:**
    - **Physical Segmentation:** Isolates networks using separate hardware.
    - **Logical Segmentation:** Uses VLANs to create isolated segments within the same hardware.
    - **Air Gaps:** Physically isolates networks with no connectivity.
- **DMZ (Demilitarized Zone):**
  - Hosts public-facing services (e.g., web servers) while isolating them from internal networks.
- **Zero Trust Architecture:**
  - No implicit trust; requires strict access verification for every device and user.
- **Defense in Depth:** Layered security approach combining multiple controls (e.g., firewalls, IDS/IPS, endpoint security).

---

### 2.2 Virtualization and Cloud Security
- **Cloud Service Models:**
  - **IaaS (Infrastructure as a Service):** Virtualized computing resources (e.g., AWS EC2).
  - **PaaS (Platform as a Service):** Tools for application development (e.g., Google App Engine).
  - **SaaS (Software as a Service):** Hosted applications (e.g., Microsoft 365, Dropbox).
- **Cloud Deployment Models:**
  - Public, Private, Hybrid, Community Clouds.
- **Cloud Security Considerations:**
  - **Shared Responsibility Model:** Cloud providers secure infrastructure; customers secure data.
  - **CASB (Cloud Access Security Broker):** Enforces security policies for cloud applications.
  - **Cloud Misconfigurations:** Unsecured storage, overly permissive access controls.

---

### 2.3 Security Controls
- **Control Types:**
  - **Preventive Controls:** Firewalls, access control policies.
  - **Detective Controls:** IDS/IPS, logging, audits.
  - **Corrective Controls:** Backups, patching, disaster recovery.
- **Physical Controls:**
  - Locks, security guards, cameras, fences.
- **Logical Controls:**
  - Authentication, encryption, firewalls.

---

### 2.4 Secure System Design
- **System Hardening:**
  - Disable unnecessary services.
  - Regularly apply patches and updates.
  - Enforce strong passwords and access controls.
- **Secure Baselines:**
  - Standardized configurations for systems.
  - Baselines are monitored for deviations using tools like configuration management systems.
- **Embedded Systems Security:**
  - IoT Devices: Protect against default credentials, insecure firmware.
  - Industrial Control Systems (ICS): Use segmentation and strong authentication.

---

### 2.5 Physical and Environmental Security
- **Physical Security Controls:**
  - Mantraps, access cards, biometric scanners, video surveillance.
- **Environmental Controls:**
  - **HVAC (Heating, Ventilation, and Air Conditioning):** Maintains optimal temperatures for equipment.
  - **Fire Suppression:** Gas-based systems (e.g., Halon replacements) to prevent damage to electronics.

---

### 2.6 Secure Design Principles
- **Least Privilege:** Users and systems only get the minimum permissions required.
- **Separation of Duties:** No single individual has full control over critical systems.
- **Fail-Secure Defaults:** Systems default to a secure state in case of failure.
- **Diversity of Defense:** Use varied security mechanisms to avoid single points of failure.

---

### 2.7 Threat Modeling
- **Definition:** Identifies potential threats and vulnerabilities in a system.
- **Common Methods:**
  - **STRIDE Framework:** Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege.
  - **DREAD Model:** Damage potential, Reproducibility, Exploitability, Affected users, Discoverability.

---

### 2.8 Cryptographic Concepts in Architecture
- **Symmetric Encryption:** Single key for encryption and decryption (e.g., AES).
- **Asymmetric Encryption:** Public/private key pairs (e.g., RSA, ECC).
- **Hashing:** Ensures data integrity (e.g., SHA-256).
- **PKI (Public Key Infrastructure):** Manages digital certificates and encryption keys.

---

### 2.9 Secure Application Development
- **Best Practices:**
  - Input validation, output encoding.
  - Use secure coding frameworks (e.g., OWASP guidelines).
  - Regular code reviews and penetration tests.
- **Secure DevOps:**
  - Integrate security into CI/CD pipelines.
  - Automate testing and vulnerability scanning.

---

### Real-World Scenarios
1. **Example 1:**
   - A company misconfigures its cloud storage, exposing sensitive customer data. The breach leads to compliance violations and fines.
2. **Example 2:**
   - An IoT device in a manufacturing plant is exploited due to default credentials. The attacker gains access to industrial systems.
3. **Example 3:**
   - Weak separation of duties allows a disgruntled employee to bypass controls and access critical financial data.

---

---

## Domain 3: Implementation

### 3.1 Secure Protocols
- **Common Protocols and Their Uses:**
  - **HTTPS:** Secure web browsing (uses TLS).
  - **SSH:** Secure remote administration.
  - **FTPS/SFTP:** Secure file transfers.
  - **DNSSEC:** Ensures DNS integrity and authenticity.
  - **SNMPv3:** Secure network device management.
  - **IPSec:** Secures IP communication using authentication and encryption.
- **Weak Protocols to Avoid:**
  - **HTTP:** Use HTTPS instead.
  - **Telnet:** Replace with SSH.
  - **FTP:** Use FTPS or SFTP.

---

### 3.2 Endpoint Security
- **Key Solutions:**
  - **Antivirus/Anti-malware:** Scans for and removes malicious software.
  - **Host-based Firewalls:** Protect individual devices from network threats.
  - **EDR (Endpoint Detection and Response):** Advanced monitoring and response to endpoint threats.
- **Hardening Techniques:**
  - Regular software updates and patches.
  - Disable unnecessary ports and services.
  - Use application whitelisting.

---

### 3.3 Wireless Security
- **Wi-Fi Encryption Protocols:**
  - **WPA3:** Current standard, strong encryption.
  - **WPA2:** Commonly used, secure but aging.
  - **WEP:** Deprecated due to weak security.
- **Best Practices:**
  - Use strong passwords for wireless networks.
  - Disable SSID broadcasting for added privacy.
  - Enable MAC address filtering.
- **Wireless Threats:**
  - Evil twin attacks, rogue access points, deauthentication attacks.

---

### 3.4 Implementing Secure Network Designs
- **Segmentation:**
  - Create isolated segments for sensitive systems (e.g., payment processing).
- **Access Control:**
  - Use VLANs to separate traffic.
  - Implement ACLs (Access Control Lists) to limit access.
- **Load Balancers:**
  - Distribute traffic to prevent overloading and ensure availability.

---

### 3.5 Cryptography and PKI Implementation
- **Encryption Types:**
  - **Symmetric:** AES for fast encryption.
  - **Asymmetric:** RSA for secure key exchanges.
- **Certificate Management:**
  - Use trusted Certificate Authorities (CAs).
  - Regularly renew and revoke certificates as needed.
- **PKI Components:**
  - Public/Private Keys, CAs, CRLs (Certificate Revocation Lists).

---

### Real-World Scenarios
1. **Example 1:**
   - An organization deploys HTTPS across its website to secure customer transactions.
2. **Example 2:**
   - A company strengthens endpoint security by implementing EDR and regularly patching devices.
3. **Example 3:**
   - A wireless network is compromised by an attacker using a rogue access point. Security is improved by implementing WPA3 and monitoring wireless activity.

---

---

## Domain 4: Operations and Incident Response

### 4.1 Incident Response Procedures
- **Phases of Incident Response:**
  1. **Preparation:** Develop incident response policies, procedures, and tools.
  2. **Identification:** Detect and verify incidents.
  3. **Containment:** Isolate the issue to prevent further damage.
  4. **Eradication:** Remove the root cause (e.g., malware).
  5. **Recovery:** Restore systems to operational status.
  6. **Lessons Learned:** Document and review to prevent recurrence.
- **Key Tools:**
  - SIEM (Security Information and Event Management).
  - Incident Response Platforms (e.g., CrowdStrike, Splunk).

---

### 4.2 Digital Forensics
- **Forensic Process:**
  - Identify evidence.
  - Preserve evidence (chain of custody).
  - Analyze and report findings.
- **Forensic Tools:**
  - FTK (Forensic Toolkit), Autopsy.
  - Memory analyzers like Volatility.

---

### 4.3 Disaster Recovery and Business Continuity
- **Key Metrics:**
  - **RTO (Recovery Time Objective):** Maximum acceptable downtime.
  - **RPO (Recovery Point Objective):** Maximum data loss measured in time.
- **Disaster Recovery Strategies:**
  - Cold Site: Inexpensive, requires setup during disaster.
  - Warm Site: Pre-configured but limited functionality.
  - Hot Site: Fully operational backup site.

---

### 4.4 Mitigation Techniques
- **DDoS Mitigation:**
  - Use rate limiting, blackholing, or scrubbing services.
- **Malware Mitigation:**
  - Isolate infected systems.
  - Use antivirus and endpoint security tools.
- **Data Exfiltration Mitigation:**
  - Monitor outbound traffic.
  - Implement DLP (Data Loss Prevention) tools.

---

### Real-World Scenarios
1. **Example 1:**
   - A ransomware attack encrypts company files. The organization uses incident response steps to isolate, clean, and recover systems from backups.
2. **Example 2:**
   - A forensic investigation identifies an insider threat leaking sensitive data through external devices.

---

---

## Domain 5: Governance, Risk, and Compliance

### 5.1 Governance and Security Policies
- **Key Policies:**
  - Acceptable Use Policy (AUP).
  - Data Retention Policy.
  - Access Control Policy.
- **Best Practices:**
  - Regular policy reviews.
  - Ensure alignment with organizational goals.

---

### 5.2 Risk Management
- **Risk Assessment Steps:**
  - Identify risks.
  - Analyze impact and likelihood.
  - Prioritize risks based on severity.
  - Implement controls to mitigate risks.
- **Frameworks:**
  - NIST Cybersecurity Framework.
  - ISO/IEC 27001 (Information Security Management Systems).

---

### 5.3 Compliance and Legal Considerations
- **Key Regulations:**
  - **GDPR (General Data Protection Regulation):** Focuses on data privacy.
  - **HIPAA (Health Insurance Portability and Accountability Act):** Protects health information.
  - **SOX (Sarbanes-Oxley Act):** Ensures financial transparency.
- **Auditing and Monitoring:**
  - Perform regular audits to ensure compliance.
  - Use automated monitoring tools for real-time compliance checks.

---

### 5.4 Ethics in Security
- **Examples:**
  - Avoiding unauthorized access, even during penetration tests.
  - Reporting vulnerabilities responsibly (responsible disclosure).

---

### Real-World Scenarios
1. **Example 1:**
   - A company faces GDPR fines for failing to protect customer data. Risk management processes are enhanced to avoid future incidents.
2. **Example 2:**
   - An audit reveals outdated policies. The organization updates and trains employees on new governance standards.

---
