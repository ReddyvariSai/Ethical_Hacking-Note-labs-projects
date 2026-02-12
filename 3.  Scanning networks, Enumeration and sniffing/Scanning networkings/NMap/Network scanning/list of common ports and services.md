Here is a consolidated list of the most common and important TCP/UDP ports and their associated services, compiled from IANA assignments, industry-standard training materials, and vendor documentation .

**Port Number** | **Protocol** | **Service Name** | **Primary Function / "Used By"** | **Common Use Case in 2025**
:--- | :--- | :--- | :--- | :---
**20/21** | TCP | **FTP** (File Transfer Protocol) | Data transfer (20) / Command (21)  | Legacy file transfers; **high-risk** due to cleartext credentials 
**22** | TCP | **SSH** (Secure Shell) | Encrypted remote administration, file transfers (SFTP, SCP)  | **Universal standard** for secure server/network device management
**23** | TCP | **Telnet** | Unencrypted remote terminal  | Obsolete; **avoid in production** (cleartext, easily intercepted)
**25** | TCP | **SMTP** | Email routing between mail servers  | Mail Transfer Agent (MTA) communication
**53** | TCP/UDP | **DNS** | Domain Name System (hostname to IP translation)  | **Critical**; enables all web/application lookups
**67/68** | UDP | **DHCP** | Bootstrap Protocol server (67) / client (68)  | Automatic IP address assignment
**80** | TCP | **HTTP** | Unencrypted web traffic  | Standard web; largely replaced by HTTPS in production
**88** | TCP/UDP | **Kerberos** | Network authentication (esp. Active Directory)  | Domain authentication; critical for Windows environments
**110** | TCP | **POP3** | Post Office Protocol v3 (email retrieval)  | Downloading emails to local client
**123** | UDP | **NTP** | Network Time Protocol  | Clock synchronization (security/audit critical)
**137-139** | TCP/UDP | **NetBIOS** | Windows naming/file sharing (NS, DGM, SSN)  | Legacy Windows networking; often disabled in modern secure networks
**143** | TCP | **IMAP** | Internet Message Access Protocol (email retrieval)  | Server-side email management (keeps messages on server)
**161/162** | UDP | **SNMP** | Simple Network Mgmt Protocol (agents/traps)  | Network device monitoring (bandwidth, status, alerts)
**389** | TCP/UDP | **LDAP** | Lightweight Directory Access Protocol  | Directory services (user/store lookups)
**443** | TCP/UDP | **HTTPS/QUIC** | HTTP over SSL/TLS; QUIC (UDP)  | **Dominant web traffic**; encrypted web, APIs, mobile apps
**445** | TCP | **SMB** | Server Message Block (Windows file sharing)  | Modern Windows file/print sharing; major ransomware vector
**465/587** | TCP | **SMTP Submission** | Authenticated SMTP (secure email sending)  | Email client submission to server
**514** | UDP | **Syslog** | System log collection  | Centralized logging (network/Unix events)
**548** | TCP | **AFP** | Apple Filing Protocol  | Legacy Mac file sharing
**554** | TCP/UDP | **RTSP** | Real Time Streaming Protocol  | Streaming media control (AirPlay, IP cameras)
**587** | TCP | **SMTP Submission** | Message submission (authenticated)  | Standard email submission port
**631** | TCP/UDP | **IPP** | Internet Printing Protocol  | Network printing (modern)
**636** | TCP | **LDAPS** | Secure LDAP (SSL/TLS)  | Encrypted directory lookups
**993** | TCP | **IMAPS** | IMAP over SSL/TLS  | Secure email retrieval
**995** | TCP | **POP3S** | POP3 over SSL/TLS  | Secure email download
**1433** | TCP | **MS SQL** | Microsoft SQL Server  | Database access
**1701** | UDP | **L2TP** | Layer 2 Tunneling Protocol (VPN)  | VPN implementation (often with IPsec)
**1723** | TCP | **PPTP** | Point-to-Point Tunneling Protocol | Legacy VPN; **deprecated/insecure**
**3306** | TCP | **MySQL** | MySQL database  | Web application databases (LAMP stacks)
**3389** | TCP | **RDP** | Remote Desktop Protocol  | Windows remote GUI access; **heavily targeted**
**5000** | TCP | **AirPlay** | Apple AirPlay (legacy)  | Media streaming (often reassigned; conflict with Docker)
**5432** | TCP | **PostgreSQL** | PostgreSQL database  | Advanced open-source database
**5900** | TCP/UDP | **VNC/RFB** | Virtual Network Computing / Remote Framebuffer  | Cross-platform remote screen sharing
**6379** | TCP | **Redis** | Redis key-value store | Caching/session store (common in web apps)
**8080** | TCP | **HTTP Alternate** | Proxy/caching/development servers  | Common alternate HTTP port (Tomcat, Jenkins, dev)
**8443** | TCP | **HTTPS Alternate** | Tomcat SSL, web admin panels  | Secure web management interfaces
**9100** | TCP | **JetDirect** | Raw printing protocol  | Network printers (HP, etc.)
**27017** | TCP | **MongoDB** | MongoDB database | NoSQL database (default port)

## 📋 Port Number Ranges & Key Context
To properly interpret this list, you need to understand the three official IANA categories, which determine **how** and **who** can bind to these ports :

1.  **Well-Known/System Ports (0–1023)** : Assigned to core internet services (HTTP, SSH, DNS). On Unix/Linux, **root/administrator privileges are required** to run a service on these ports. This is a security measure to prevent users from impersonating critical services .
2.  **Registered Ports (1024–49151)** : Assigned by IANA for specific applications from vendors (e.g., Microsoft SQL, MySQL). User-level processes *can* use these, but collisions can occur if multiple apps choose the same unassigned port .
3.  **Dynamic/Private/Ephemeral Ports (49152–65535)** : **Never assigned**. The OS automatically uses these as temporary source ports for outbound connections. You should never need to open these inbound for a standard service .

**Critical Security Context (2025):**
- **"Filtered" vs. "Closed":** In modern scanning, a port returning no response (`filtered`) is more common than a definitive `closed` (RST) due to stateful firewalls and cloud security groups .
- **Service Misplacement:** Attackers and malware frequently run services on **non-standard ports** (e.g., SSH on 2222, RDP on 3388). While port numbers provide a strong hint, **banner grabbing/version detection (`-sV`)** is the only way to definitively identify the service .
- **Apple-Specific:** Enterprise environments using Apple devices require a specific set of ports (5223, 2197, 16384-16403) for iCloud, Push Notifications, and FaceTime which are not in standard IANA listings .

If you are using this list to build a firewall whitelist or study for a certification (Network+/CCNA), the **top 20 ports** (specifically 22, 80, 443, 53, 25, 3389, 445) will cover >95% of production traffic scenarios.
