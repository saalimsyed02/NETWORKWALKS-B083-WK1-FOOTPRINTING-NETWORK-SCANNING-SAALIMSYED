# NETWORKWALKS-B083-WK2-FOOTPRINTING & NETWORK SCANNING

| Field | Details |
| :--- | :--- |
| **Program / Batch** | B083-Networkwalks |
| **Date** | September 14, 2026 |
| **Author** | Syed Saalim Syed Farooque Raza |
| **Modules Covered** | W2-PM2 (GHDB Footprinting) & W2-PM5 (Zenmap Scanning) |
| **Client/Target** | My own local LAN Network & authorized lab environment |
| **Permission secured from client?** | Yes (Owned devices and authorized educational lab) |
| **Phases covered** | • Phase 1: Reconnaissance & Footprinting<br>• Phase 2: Scanning & Network Discovery<br>• Phase 3-5: In Progress |

---

## 1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

---

## 2. Introduction
This report covers footprinting and reconnaissance activities alongside scanning my own local network and authorized lab environment. One part covers footprinting using public tools and search techniques (W2-PM2), while the other covers network discovery and host scanning using Zenmap (W2-PM5). Together, they demonstrate how a security professional transitions from gathering initial context to mapping live hosts on a local subnet as part of my ongoing internship program at Networkwalks.

All activities and commands were executed within a controlled environment. Every step below includes the description of the activity, the observations made, screenshots as evidence, and a brief note on the security implications from an attacker's or defender's perspective.

---

## 3. Tools Used
| Tool | Purpose |
| :--- | :--- |
| **Google Search / GHDB** | Used advanced search operators and dorks to find exposed information and files |
| **Zenmap (Nmap GUI)** | Scan the local subnet to find live hosts, IPs, and MAC addresses |
| **Windows CMD** | Local IP and MAC address identification |

---

## 4. Activities Performed

### 4.1 Module W2-PM2: Google Hacking Database (GHDB) Footprinting
## 4. Practical Implementation / Findings

### 4.1 Google Hacking Database (GHDB) Footprinting
During the reconnaissance phase, advanced Google dork queries were utilized to discover exposed directory listings, publicly accessible webcams, and sensitive files. Below are the specific samples collected:

#### 1. Public Camera Details (Google Dorks Footprinting)
| # | Google Dork Query | Target URL / Result Reference |
|---|---|---|
| 1 | `intitle:"webcamXP" inurl:8080` | `http://109.233.191.130` |
| 2 | `intitle:"Webcam" inurl:WebCam.htm` | `https://www.lmc.edu/webcam.htm` |
| 3 | `intitle:"Index of /webcam/"` | `https://ns.ph.liv.ac.uk/webcam/` |
| 4 | `inurl:webcam site:skylinewebcams.com inurl:roma` | `https://www.skylinewebcams.com/webcam/italia/lazio/roma/piazza-di-spagna.html` |
| 5 | `inurl:/multi.html intitle:webcam` | `http://68.115.218.130:32479/home.html` |
| 6 | `intitle:"webcamxp" "Flash JPEG Stream"` | `http://109.233.191.130:8080/` |
| 7 | `inurl:/ViewerFrame? intitle:"Network Camera NetworkCamera"` | `http://80.152.138.183/ViewerFrame?Mode=Motion&Language=0` |
| 8 | `intitle:"Biromsoft WebCam" -4.0 -serial ...` | `https://www.stonecircle.us/WebCam/cam.html` |
| 9 | `"powered by webcamXP" "Pro|Broadcast"` | `http://109.233.191.130:8080/` |
| 10 | `inurl:"live/cam.html"` | `http://www.insecam.org/en/bytype/webcamxp/` |

#### 2. Specific PDF Documents (Google Dorks Footprinting)
| # | Google Dork Query | Target URL / Result Reference |
|---|---|---|
| 1 | `intitle:index.of "parent directory" mathematics pdf` | `https://www.unm.edu/~megrad/Math/` |
| 2 | `intitle:index.of "parent directory" calculus pdf` | `https://www.aetkin.com/files/Math%20150%20Calculus%20I/Advanced%20Calculus%20Textbook/` |
| 3 | `intitle:index.of "parent directory" linear algebra pdf` | `https://math.mit.edu/~gs/linearalgebra/ila6/?trk=public_post_comment-text` |
| 4 | `intitle:index.of "parent directory" differential equation pdf` | `https://www.aerostudents.com/courses/differential-equations/` |
| 5 | `intitle:index.of "parent directory" discrete mathematics pdf` | `https://discrete.openmathbooks.org/pdfs/?SD` |
| 6 | `intitle:index.of "parent directory" probability and statistics pdf` | `https://www.aerostudents.com/courses/probability-and-statistics/` |
| 7 | `intitle:index.of "parent directory" geometry pdf` | `https://www.cs.tufts.edu/research/geometry/pdf/` |
| 8 | `intitle:index.of "parent directory" trigonometry pdf` | `http://www.wallace.ccfaculty.org/book/` |
| 9 | `intitle:index.of "parent directory" hc verma pdf` | `https://discrete.openmathbooks.org/pdfs/?SD` |
| 10 | `intitle:index.of "parent directory" c++ pdf` | `https://ce.cet.ac.in/downloads/Study%20Material/Computer%20Programming/` |
* **Objective:** Use advanced search operators (Google Dorks) to discover publicly exposed information, sensitive files, or misconfigured directories related to specific targets.
* **Step-by-Step Execution:**
  1. Opened a standard web browser and navigated to Google Search / Exploit-DB GHDB.
  2. Applied custom search operators and dorks (such as `site:` and `filetype:`) to query publicly indexed data within authorized boundaries.
* **Observations:** Search queries successfully isolated specific file types and indexed pages without breaching any authentication barriers.
* **Security Implications:** 
  * *Attacker Perspective:* Attackers use GHDB to quickly find exposed configuration files, backup documents, or login portals that organizations inadvertently leave indexed on the public web.
  * *Defender Perspective:* Organizations must ensure that sensitive files are properly hidden using `robots.txt`, access controls, or removed from public web server roots to prevent information disclosure.
 
   **Evidence:**
  
<img width="1917" height="1027" alt="Screenshot 2026-09-13 211843" src="https://github.com/user-attachments/assets/363a7f06-b9aa-40cf-81d7-8ecc98a05517" />


### 4.2 Module W2-PM5: Zenmap Network Scanning
* **Objective:** Perform network discovery and host enumeration on the local subnet to identify live systems, open ports, and active services using Zenmap (Nmap GUI).
* **Step-by-Step Execution:**
  1. Opened Windows CMD and ran `ipconfig` to identify the local machine's IP address and subnet range.
  2. Launched Zenmap with administrator privileges.
  3. Entered the local network target range (subnet) and selected a scan profile (such as Intense Scan or Ping Scan).
  4. Executed the scan and monitored the output in the Nmap Output and Topology tabs.
* **Observations:** The scan successfully identified live hosts on the local network, resolved active IP and MAC addresses, and listed open ports/services running on the discovered devices.
* **Security Implications:** 
  * *Attacker Perspective:* Attackers perform network mapping to discover vulnerable live hosts, hidden devices, and open ports that can be leveraged for further penetration.
  * *Defender Perspective:* Regular internal network scanning helps administrators maintain an accurate asset inventory, detect unauthorized rogue devices, and close unnecessary open ports.

**Evidence:**
<img width="1012" height="837" alt="Screenshot 2026-09-14 025312" src="https://github.com/user-attachments/assets/c86a81c5-a242-4392-a614-1ebc6d44fcd8" />

---

## 5. Conclusion
This practical module successfully demonstrated the foundational phases of a security assessment. Through W2-PM2, I gained hands-on experience in passive reconnaissance and open-source intelligence gathering using search techniques, highlighting how unintended information disclosure can expose an organization. Through W2-PM5, I utilized Zenmap to map a local network subnet, identifying live hosts and open ports, which reinforces the importance of asset visibility and network defense. Overall, these exercises bridged theoretical security concepts with practical execution in a controlled environment.
