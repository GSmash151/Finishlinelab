domain poisoning
how to attack all in one ?
what is DDos ?
how can use multi-nodes or users ?

![[HomeWork/Session 10/ReconnaissanceAttacks.png]]
A **reconnaissance attack** is a type of cyberattack where an adversary gathers information about a target system, network, or organization to identify vulnerabilities that can later be exploited. These attacks are typically passive, meaning they aim to collect information without triggering alarms or alerting the target. However, they can also involve active techniques.
1. **Network Mapping:** Identifying the structure and layout of the target's network, including devices, servers, and IP addresses.
2. **Vulnerability Identification:** Finding weaknesses, such as outdated software, mis-configured devices, or open ports.
3. **Gaining Contextual Information:** Learning about the organization, such as employee names, email addresses, or technologies in use.
#### Types of Reconnaissance Attacks:
**Passive Reconnaissance:**    
- Gathering information without directly interacting with the target, minimizing detection risks. 
- Social engineering or dumpster diving for sensitive information. 
- Scanning public records, websites, or social media for insights.
- Monitoring encrypted network traffic using sniffing tools.
**Active Reconnaissance:**  
- Actively probing the target system to gather data, which increases the risk of detection.- **Port Scanning:** Identifying open ports using tools like Nmap.
- **Ping Sweeps:** Sending ICMP packets to identify live hosts. 
- **Service Enumeration:** Determining which services and versions are running on the target.
#### **Common Tools Used:**
##### **Wireshark**
- **Purpose:** Network protocol analyzer that captures and inspects packets.
- **Use Case:** Analyze real-time or previously captured network traffic to identify potential issues or security threats.
```bash
wireshark
```
##### **Nmap (Network Mapper)**
- **Purpose:** Network discovery and vulnerability scanning.
- **Use Case:** Scan networks for open ports, running services, and operating system detection.
```bash
nmap [options] [target]
```
##### **Zenmap**
- **Purpose:** GUI front-end for Nmap.
- **Use Case:** Easier visualization of Nmap scan results.
```bash
zenmap
```
#### **Tcpdump**
- **Purpose:** Command-line packet capture and analysis tool.
- **Use Case:** Monitor network traffic by capturing packets.
```bash
tcpdump [options]
```
#### **Netstat**
- **Purpose:** Displays network connections, routing tables, and statistics.
- **Use Case:** Check active connections, listening ports, and overall network health.
```bash
netstat [options]
```
#### **IPTraf-ng**
- **Purpose:** Real-time network traffic monitoring.
- **Use Case:** Analyze incoming and outgoing traffic on various interfaces.
```bash
iptraf-ng
```
#### **EtherApe**
- **Purpose:** Graphical network traffic visualization tool.
- **Use Case:** Visualize network activity and analyze protocols in real-time.
```bash
etherape
```
#### **Netcat (nc)**
- **Purpose:** Network utility for reading/writing over TCP/UDP.
- **Use Case:** Test connectivity, port scanning, and setting up reverse shells.
```bash
nc [options] [target] [port]
```
#### **Kismet**
- **Purpose:** Wireless network detector, sniffer, and intrusion detection system.
- **Use Case:** Monitor Wi-Fi networks, identify access points, and detect rogue devices.
```bash
kismet
```
#### **OpenVAS**
- **Purpose:** Vulnerability scanner for networks.
- **Use Case:** Assess systems for mis-configurations, open ports, and vulnerabilities.
```bash
openvas-start
```
#### **ARPwatch**
- **Purpose:** Monitors Ethernet traffic and maintains logs of MAC-IP mappings.
- **Use Case:** Detect ARP spoofing or MAC address changes.
```bash
arpwatch -i [interface]
```
#### **Hping3**
- **Purpose:** Packet crafting and network testing tool.
- **Use Case:** Test network security, perform traceroute, and evaluate firewall rules.
```bash
hping3 [options] [target]
```
#### **Snort**
- **Purpose:** Network Intrusion Detection System (NIDS).
- **Use Case:** Detect malicious activity by analyzing packet payloads.
```bash
snort -c /etc/snort/snort.conf
```

 ![video](https://youtu.be/BWaGnsRirtU)

---
![[AccessAttacks.png]]
 #### **Password-Based Attacks**  
  Attackers attempt to guess, steal, or bypass passwords to access accounts or systems. This can include techniques like:
   **Brute Force Attacks**: 
   Trying all possible password combinations until the correct one is found. 
   **Dictionary Attacks**: 
   Using a list of common passwords or phrases to guess a password.
   **Credential Stuffing**: 
   Using stolen username-password pairs from one breach to access other systems.
   
**Phishing and Social Engineering**  
Attackers trick individuals into revealing login credentials or sensitive information by pretending to be legitimate entities. Examples include: 
- Emails or messages directing users to fake login pages. 
- Impersonating technical support to obtain login credentials.

**Privilege Escalation:** 
An attacker gains elevated permissions beyond their current access level to control sensitive areas of a system or network. This can involve: 
- **Horizontal Escalation**: Accessing another user’s privileges at the same level. 
- **Vertical Escalation**: Gaining higher-level administrative privileges.

**Backdoor Access:** 
Attackers install or exploit back-doors (hidden entry points) in software or systems, allowing them unauthorized access without detection.

**Man-in-the-Middle (MitM) Attacks**  
Attackers intercept communications between two parties to gain unauthorized access to sensitive data like login credentials or session tokens.

**Keylogger Attacks**  
Software or hardware is used to secretly record keystrokes on a victim's device, capturing sensitive information like passwords and credit card details.

**Session Hijacking**  
An attacker takes over a user's active session, often by stealing session cookies or exploiting vulnerabilities in session management.

**Exploit-Based Attacks**  
Attackers exploit vulnerabilities in software or systems to gain unauthorized access. Examples include: 
**Buffer Overflow Attacks**: Exploiting programming errors to execute malicious code.
**Zero-Day Exploits**: Using unknown vulnerabilities before they are patched.
#### Consequences of Access Attacks
- Data theft or exposure of sensitive information.
- Disruption of operations or services.
- Financial losses or fraud.
- Damage to reputation and trust.
- Legal or compliance penalties.
#### Prevention and Mitigation Strategies
- Implement strong password policies and multi-factor authentication (MFA).
- Regularly update and patch systems to close vulnerabilities.
- Educate users about phishing and social engineering risks.
- Monitor and audit access logs for suspicious activity.
- Use firewalls, intrusion detection systems, and encryption.
- Limit access privileges based on roles and the principle of least privilege.
--- 
![[DenialofServiceAttacks.png]]
DoS attacks exploit vulnerabilities in a system or its resources by flooding it with illegitimate requests or exploiting resource-intensive processes. This causes the system to:
1. **Exhaust Resources:** Utilize all available memory, CPU, bandwidth, or storage.
2. **Crash:** Overload software or hardware to the point of failure.
3. **Drop Legitimate Traffic:** Prevent legitimate users from accessing the system due to congestion.
#### **Types of DoS/DDoS Attacks**
1. **Volumetric Attacks (Bandwidth Exhaustion)**
- **Description:** These attacks aim to consume the target's network bandwidth by overwhelming it with a large volume of traffic.
- **UDP Floods:** Send a massive number of **User Datagram Protocol** (UDP) packets to random ports, forcing the target to handle unnecessary traffic.
-  **ICMP Floods (Ping Floods):** Overload the target with a high rate of ICMP Echo Request packets (pings).  
- **Impact:** The legitimate traffic is slowed or blocked.
#### **Protocol Attacks**
- **Description:** Exploit weaknesses in the protocol stack to disrupt network communication.
- **SYN Floods:** Send a large number of TCP SYN requests without completing the handshake, tying up server resources. 
- **Smurf Attack:** Exploits ICMP by sending spoofed ping requests to a broadcast address, overwhelming the target with replies. 
- **Ping of Death:** Send over-sized or malformed ping packets to crash the target.
#### **Application Layer Attacks**
- **Description:** Target vulnerabilities in applications by sending resource-intensive requests.
- **HTTP Floods:** Send a massive number of HTTP GET/POST requests to a web server.
- **Slowloris:** Open many connections to the server but send data very slowly, preventing other legitimate users from connecting.
- **Impact:** Overloads application-specific resources like databases, web servers, or APIs.
#### **Tools for Launching DoS/DDoS Attacks**
- **LOIC (Low Orbit Ion Cannon):** Used for sending massive requests.
- **HOIC (High Orbit Ion Cannon):** A more advanced version of LOIC with multi-threading.
- **Hping3:** Craft and send custom TCP/IP packets.
- **Botnets:** Networks of compromised devices used to launch DDoS attacks.
#### **Impact of DoS/DDoS Attacks**
1. **Service Disruption:** Prevents legitimate users from accessing the service.
2. **Financial Losses:** Downtime can result in lost revenue, especially for online businesses.
3. **Reputational Damage:** Loss of customer trust due to unavailability of services.
4. **Legal Consequences:** Organizations may face penalties for failing to secure critical infrastructure.
### **Defenses Against DoS/DDoS Attacks**
#### **Network Defenses**
- **Firewalls and Routers:** Filter malicious traffic by setting up rules to block known attack patterns.
- **Rate Limiting:** Restrict the number of requests a user or IP can make within a given time-frame.
- **Black-hole Routing:** Divert traffic to a null route to prevent overload on the main system.
#### **Traffic Monitoring**
- Use tools like **Wireshark**, **Snort**, or **Nagios** to monitor abnormal traffic patterns.
- Employ Intrusion Detection and Prevention Systems (IDPS).
#### **Load Balancing**
- Distribute traffic across multiple servers to reduce the load on any single system.
#### **Use of Content Delivery Networks (CDNs)**
- CDNs, such as Cloudflare or Akamai, can absorb and mitigate DDoS attacks by leveraging their global infrastructure.
#### **Anti-DDoS Services**
- Services like **AWS Shield**, **Akamai Kona**, or **Imperva Incapsula** specialize in detecting and mitigating large-scale DDoS attacks.
#### **Regular Updates and Patches**
- Address known vulnerabilities in software or protocols to reduce the risk of exploitation.
#### **Real-World Examples of DoS/DDoS Attacks**
1. **Dyn DNS Attack (2016):** A massive DDoS attack using the Mirai botnet targeted the DNS provider Dyn, affecting major websites like Twitter, Netflix, and Spotify.
2. **Amazon Web Services (AWS) DDoS Attack (2020):** One of the largest volumetric DDoS attacks recorded, peaking at 2.3 Tbps.
Understanding the nature of DoS/DDoS attacks and implementing robust defenses is crucial for maintaining the availability and reliability of online services.
--- 
![[KeepBackups.png]]

---

![[Upgrade,Update&Patch.png]]

---

![[Authentication,Authorization&Accounting.png]]

#### Network Attack Mitigation
Network attack mitigation involves implementing measures to prevent, detect, and respond to malicious activities targeting a network. The goal is to reduce the impact of attacks such as denial-of-service (DoS), data breaches, and unauthorized access.
#### Techniques for Network Attack Mitigation:
**Firewalls**
- Block unauthorized access by filtering incoming and outgoing traffic based on rules.
**Intrusion Detection and Prevention Systems (IDPS)**  
- Detect and stop suspicious or malicious activities in real-time.
**Virtual Private Networks (VPNs)**    
- Secure communications over public or untrusted networks by encrypting traffic.
**Network Segmentation**
- Divide the network into isolated segments to limit the spread of attacks.
**Rate Limiting and Traffic Shaping**     
- Control the volume of traffic to prevent overloads and mitigate DoS attacks.
**Anti-Malware Tools**    
- Scan and block malicious files or code from entering the network.
**Patch Management**    
- Regularly update software to fix vulnerabilities exploited by attackers.
**Encryption** 
- Protect data in transit and at rest to prevent interception or unauthorized access.
**Behavioral Analytics**   
- Monitor user and system behavior for anomalies that may indicate an attack.
### Authentication
Authentication is the process of verifying the identity of a user, device, or system attempting to access a resource. It ensures that the entity requesting access is who or what it claims to be.
#### Methods of Authentication:
**Single-Factor Authentication (SFA)**    
- Uses one credential type, such as a password.
**Multi-Factor Authentication (MFA)**
- Combines two or more factors, such as:
- **Something You Know**: Password, PIN.
-  **Something You Have**: Security token, smartphone.
- **Something You Are**: Biometric data (fingerprint, facial recognition).
**Certificate-Based Authentication** 
 - Uses digital certificates to verify identity.
**OAuth/OpenID Connect**    
- Standards for secure token-based authentication in web applications.
### Authorization
Authorization is the process of granting or denying access to specific resources or actions based on the authenticated entity's permissions or roles. It ensures that users can only perform actions or access resources they are allowed to.
#### Authorization Techniques:
**Role-Based Access Control (RBAC)**
- Permissions are assigned based on user roles (e.g., admin, editor, viewer).
**Attribute-Based Access Control (ABAC)**    
- Access is determined based on user attributes (e.g., department, location).
**Policy-Based Access Control**   
- Centralized policies define who can access what under specific conditions.
**Principle of Least Privilege**   
- Users are given the minimum access necessary to perform their tasks.
### Accounting (or Auditing)
Accounting refers to tracking and logging user actions, resource usage, and system events to maintain accountability and traceability. This information is crucial for auditing, compliance, and forensic analysis.
#### Key Aspects of Accounting:
**Logging**   
- Recording events such as logins, file access, and system changes.
**Monitoring** 
- Continuously observing network and system activity for anomalies.
**Auditing**   
- Reviewing logs to ensure compliance with policies and detect potential threats.
**Reporting**
- Generating summaries of activities for stakeholders and regulatory compliance.

### Combined Use: AAA Framework

The concepts of **Authentication**, **Authorization**, and **Accounting** form the **AAA framework**, which is widely used in network security. It ensures that:
- Only verified users (authentication)
- Can access appropriate resources (authorization)
- And their actions are tracked for accountability (accounting).

AAA protocols, like RADIUS and TACACS+, implement these principles in modern networks.

4o