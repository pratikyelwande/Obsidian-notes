### Overview of Bug Bounty

- **Bug Bounty**: Reward system for ethical hackers who find vulnerabilities.
- **Fancy Hacking**: Competitive hacking in ethical scope.

---

### Key Terms

- **VDP (Vulnerability Disclosure Program)**: No monetary reward.
- **BBP (Bug Bounty Program)**: Monetary rewards for valid vulnerabilities.
- **CVD (Coordinated Vulnerability Disclosure)**: Monetary rewards for disclosed vulnerabilities.
- **VRP (Vulnerability Rewards Program)**: Rewards from tech giants like Apple, Microsoft, Google.
- **RDP (Recognition and Disclosure Program)**: Non-monetary rewards (swags, goodies, gift cards).

---

### Policies

- **Scope**: Defines what is in scope and out of scope for testing.

#### In-Scope Example

- `*.web.whatsapp.com`

---

### Reward Structure

#### Priority-Based Rewards

##### Bugcrowd & HackerOne

- **P1**: $5,000 – $7,500
- **P2**: $1,500 – $4,500
- **P3**: $600 – $1,400
- **P4**: $100 – $500

##### Other Platforms (Example Range)

- **P1**: $3,000 – $10,000
- **P2**: $500 – $4,000
- **P3**: $200 – $700
- **P4**: $100 – $200

---

### Platforms

- **Bugcrowd**
- **HackerOne**
- **YesWeHack**
- **Intigriti**

---

### Priorities and Examples

- **Priority P1**: Critical (High rewards, typically root access).
- **Priority P2-P4**: Based on severity and complexity.

**Example Target Domains**

- `*.tidal.com`
- `*.dell.com`

---

### Status Definitions

- **NA**: Not Applicable.
- **OOS**: Out of Scope.
- **Duplicate**: Already reported.

---

### Tools and Setup

#### 1. WSL Subsystem - Ubuntu

1. Install from Microsoft Store.
2. Enable via **Windows Features**: "Turn Windows Features on or off" → **Linux Subsystem**.

#### 2. Browser Extensions

- **OpenMultiple URLs**
- **TruffleHog**
- **DotGit**
- **Wappalyzer**

#### 3. BBHTv2
[BBHT script](https://github.com/pratikyelwande/bbtv)
1. Create script: `cat > bbhtv2.sh`
2. Paste code, save.
3. Make executable: `chmod +x bbhtv2.sh`
4. Run: `./bbhtv2.sh`

#### 4. ReconFTW

1. Clone: `git clone https://github.com/six2dez/reconftw`
2. Install: `./install.sh`

#### 5. BurpSuite
	Java Version 8 needed
1. **Java** installation: Download from [Java download](https://www.java.com/download/ie_manual.jsp)
2. **PwnFox** extension: [Mozilla link](https://addons.mozilla.org/en-US/firefox/addon/pwnfox/)
3. **Proxy setup**: Import Burp certificate for HTTPS interception.

#### 6. SQLMap

1. Download from GitHub: `https://github.com/sqlmapproject/sqlmap/zipball/master`
2. Extract, navigate to directory.
3. Run SQLMap: `sqlmap.py`

---

### Common Commands

- **Subdomain Enumeration**: `subfinder -d <domain> | httpx -mc 200 | tee target.txt`
- **Wayback URL Extraction**: `cat subs.txt | waybackurls | tee wayback`

---

### Recon and Target Analysis

#### Google Dorking

- Search engines for reconnaissance: Google, Bing, Yandex, Censys, Shodan, Zoomeye, FOFA.
- Purpose: Subs, URLs, VHOST discovery, fuzzing.

## Google Dorking Cheat Sheet

### What is Google Dorking?

Google Dorking, also known as Google Hacking, involves using advanced search operators to refine Google search results. It’s often used to find specific types of information on the web, such as exposed files, website vulnerabilities, and detailed data.

### Main Search Filters

|Filter|Description|Example|
|---|---|---|
|`allintext`|Searches for occurrences of all the keywords in the text of a page.|`allintext:"keyword"`|
|`intext`|Searches for occurrences of keywords all at once or one at a time within the text of a page.|`intext:"keyword"`|
|`inurl`|Searches for occurrences of a keyword in the URL.|`inurl:"keyword"`|
|`allinurl`|Searches for occurrences of all keywords in the URL.|`allinurl:"keyword"`|
|`intitle`|Searches for occurrences of keywords in the title of a page.|`intitle:"keyword"`|
|`allintitle`|Searches for occurrences of all keywords in the title of a page.|`allintitle:"keyword"`|
|`site`|Restricts the search to a specific site.|`site:"www.example.com"`|
|`filetype`|Searches for a specific file type (e.g., PDF, DOC).|`filetype:"pdf"`|
|`link`|Finds pages that link to a specified URL.|`link:"keyword"`|
|`numrange`|Finds results within a specific number range.|`numrange:100-200`|
|`before`/`after`|Searches within a particular date range (usually combined with `filetype`).|`filetype:pdf after:2020-01-01 before:2021-01-01`|
|`allinanchor` (or `inanchor`)|Shows pages with keywords in the anchor text of links pointing to them.|`inanchor:"keyword"`|
|`allinpostauthor` (or `inpostauthor`)|Searches for blog posts written by a specific author.|`allinpostauthor:"author_name"`|
|`related`|Lists web pages that are “similar” to a specified page.|`related:www.example.com`|
|`cache`|Shows the cached version of a specified page.|`cache:www.example.com`|

---

### Examples of Common Google Dorks

- **Directory Listings**:
    - `intext:"index of /"`
    - `intitle:"index of" "parent directory" "size" "last modified"`
- **Finding Sensitive Files**:
    - `filetype:config inurl:web.config`
    - `filetype:env inurl:.env`
- **Exposed Data**:
    - `ext:pdf intext:"confidential"`
    - `ext:doc | ext:xls | ext:pdf intext:"salary" OR intext:"budget"`

---

### Key Search Operators

|Operator|Description|
|---|---|
|`"phrase"`|Searches for the exact phrase in quotes. Useful for finding specific text.|
|`OR`|Searches for one term OR another term. Example: `site:example.com OR site:another.com`|
|`AND`|Searches for results containing both terms. Example: `site:example.com AND intext:"login"`|
|`-`|Excludes results containing the term after `-`. Example: `site:example.com -site:sub.example.com`|
|`+`|Emphasizes results containing the term after `+`. Example: `+keyword`|
|`~`|Finds synonyms of the search term. Example: `~configure`|
|`*`|Acts as a wildcard to substitute any unknown terms in a phrase. Example: `site:*.com`|

---

### Advanced Usage & Examples

#### Combining Operators for Precision

- **Login Pages on Social Media**:
    - `(site:facebook.com | site:twitter.com) AND intext:"login"`
- **Sensitive Files on Target Domain**:
    - `site:example.com filetype:pdf OR filetype:doc intitle:"confidential"`

#### Common Google Dorks for Reconnaissance

1. **Subdomain Enumeration**: `site:*.example.com`
2. **URL Discovery**: `inurl:"login"` or `inurl:"admin"`
3. **Directory Listings for Media Files**:
    - `intitle:"index of" "parent directory" "mp3"` – Finds music files.
    - `intitle:"index of" "movies"` – Finds video files.

---

### Important Google Dorks for Security Research

- **Finding Open Directories**:
    - `intitle:"index of /" intext:"password"`
- **Discovering Email Lists**:
    - `filetype:xls intext:"email" | intext:"@example.com"`
- **Vulnerable Configurations**:
    - `filetype:conf inurl:nginx`
- **Social Security Information**:
    - `filetype:xls OR filetype:csv "social security number"`

---

### Practical Reconnaissance Tasks with Dorks

1. **Subdomain Enumeration**:
    - `site:example.com -www` – Lists all subdomains of a site.
2. **Using Wayback URLs for Historical Data**:
    - Combine `waybackurls` with `site:example.com` for old URLs.
3. **Virtual Host Discovery**:
    - `intitle:"Apache2 Ubuntu Default Page"` – Common for finding Apache default pages.

### Key Google Dorking Search Operators

1. **Grouping**: Use parentheses `()` to group terms or operators together for complex queries.
    
    - Example: `inurl:(html | php)`
2. **Wildcard `*`**: Acts as a placeholder for any word or phrase, useful for filling in gaps in phrases.
    
    - Example: `How to * a computer`
3. **Exact Match `""`**: Searches for an exact phrase, which is case-insensitive.
    
    - Example: `"advanced search filters"`
4. **Number Range `m..n`**: Searches for numbers within a specified range.
    
    - Example: `"google" 1..100`
5. **Exclude `-`**: Excludes results containing specific terms.
    
    - Example: `-site:youtube.com`
6. **Include `+`**: Ensures that results include a particular term.
    
    - Example: `+site:github.com`
7. **OR `|`**: Uses logical OR for terms where any specified term matches.
    
    - Example: `"google" | "bing"`
8. **Date Filters (`after:` & `before:`)**: Limit results based on publication dates.
    
    - Example: `after:2020-01-01`

### Common Google Search Filters for Targeted Results

1. **Title Filters**: Searches for terms within page titles.
    
    - `allintitle:<keywords>` – Searches multiple terms in the title.
        - Example: `allintitle:cybersecurity threats`
2. **URL Filters**: Searches for terms within page URLs.
    
    - `allinurl:<keywords>` – Matches all specified keywords in URL.
        - Example: `allinurl:research pdf`
3. **Text Filters**: Targets terms within the page’s main content.
    
    - `allintext:<keywords>` – Matches all keywords in text.
        - Example: `allintext:data analysis`
4. **File Type `filetype:`**: Finds specific document types like PDFs, DOCs, etc.
    
    - Example: `filetype:pdf cybersecurity`
5. **Cache `cache:`**: Views a cached version of a site as stored by Google.
    
    - Example: `cache:example.com`

### Google Dorking Tips for Security and Information Gathering

- **Finding Configurations and Logs**:
    
    - `intext:password ext:log` – Searches for files with "password" in plaintext logs.
- **Locating Open Directories**:
    
    - `intitle:"index of /"` – Finds accessible directories that may contain files or folders.
- **Email or Sensitive Information**:
    
    - `inurl:email.xls ext:xls` – Finds Excel files containing email addresses.
- **Public Webcams or Vulnerable Web Servers**:
    
    - `intitle:"webcamXP 5" | inurl:"lvappl.htm"` – Finds open/public webcams.
#### Status Codes

- **200 OK**: Valid page.
- **404 Not Found**: Non-existent page.
- **403 Forbidden**: Restricted access.
- **401 Unauthorized**: Authentication required.
- **500 Internal Server Error**: Server issue.

#### Tasks

1. Subdomain Enumeration
2. Valid URL Extraction

# Domain Enumeration + FUZZING

## 1. Single Domain Enumeration

Command:

bash

Copy code

`subfinder -d khealth.io | httpx -mc 200 | tee khealth-subs`

## 2. Multi Root Domain Enumeration

Create a list of domains:

plaintext

Copy code

`khealth.us khealth.io khealth.com hydrogenhealth.com hackerone.com bugcrowd.com`

Command:

bash

Copy code

`subfinder -dL domains.txt | httpx -mc 200 | tee subs`

### Flags

- `-mc 200`: Match code 200 to filter only accessible domains.

## Dorking for Subdomain Enumeration

### Useful Extensions

- `.in`, `.nl`, `.br`, `.sg`, `.uk`

Example Google Dork:

plaintext

Copy code

`site:*.bugcrowd.com`

---

# FUZZING

### Domain Examples for Fuzzing

- `optus.com.au`
- `yesware.com`
- `apigateway.co`
- `mitwpu.ac.in`

### Dirsearch Setup

**Path**: `C:\Users\The Kong\Desktop\dirsearch`

**Usage**:

1. Open CMD and navigate:
    
    bash
    
    Copy code
    
    `cd C:\Users\The Kong\Desktop\dirsearch`
    

### Requirements

- Technology check (e.g., server type like Apache, PHP, ASPX)
- Rate limit / Thread management
- Understanding HTTP status codes and response sizes

---

## FUZZING Steps

1. **Create Target File**:
    
    bash
    
    Copy code
    
    `cat > target.txt # Paste all domains, then Ctrl + D`
    
2. **Run Subdomain Enumeration**:
    
    bash
    
    Copy code
    
    `subfinder -dL target.txt | httpx -mc 200 | tee subs.txt`
    
3. **Find Technologies**:
    
    - Use Google and online resources to identify technologies used by each domain.
4. **Create Wordlist**:
    
    - Gather common paths from Google or use:
        - [Apache fuzz wordlist](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/Apache.fuzz.txt)
        - [ASPX wordlist](https://github.com/orwagodfather/WordList/blob/main/aspx.txt)
5. **Run Dirsearch**:
    
    bash
    
    Copy code
    
    `dirsearch.py -l target.txt -w php.txt -i 200 --full-url`
    

---

# Tasks

1. Obtain valid subdomains for `.gov.uk`.
2. Perform fuzzing.
3. Identify valid files.

---

## Subdomain Examples

- `https://bb.yesware.com`
- `https://brand.optus.com.au`
- `https://docs.apigateway.co`

---

# Technology Check

- Technologies: ASP, Apache HTTP Server, Java
- Example subdomain technology:
    - `PHP` on `http://www.pcsamana.org.in`
    - `Apache HTTP Server` on `https://nmimshyderabad.org`

---

## Common Commands and Flags

### Subfinder

- `-d` for a single domain
- `-dL` for multiple domains

### HTTPx

- `-ct`: show content type
- `-sc`: show status code
- `-mc`: match code (e.g., 200 for OK)
    - `200 OK`, `404 Not Found`, `403 Forbidden`, `401 Unauthorized`

Example:

bash

Copy code

`subfinder -dL target.txt | httpx -mc 200 | tee kong.txt`

---

## Sample Domain Targets

- `https://adfs.aerlingus.com`
- `https://chat.avios.com`
- `https://forwardrewards.iagcargo.com`

# Zaid Bug bounty course
# ### **1. Recon – Find All Targets (Passive)**

> 🎯 **Goal**: Discover domains, subdomains, and endpoints in-scope

🛠 Tools:

- `subfinder`, `amass`, `assetfinder`, `crt.sh`, `chaos`, `github-subdomains`
    

bash

CopyEdit

`subfinder -d target.com -silent > subs.txt amass enum -passive -d target.com >> subs.txt`

---

### 🔶 **2. Probe for Live Assets**

> 🎯 **Goal**: Find which subdomains are alive and hosting services

🛠 Tools:

- `dnsx`, `httpx`
    

bash

CopyEdit

`cat subs.txt | dnsx > resolved.txt cat resolved.txt | httpx -title -tech-detect -status-code > live.txt`

---

### 🔶 **3. Crawl & Discover Endpoints**

> 🎯 **Goal**: Get all available URLs, hidden paths, APIs, JS files

🛠 Tools:

- `waybackurls`, `gau`, `hakrawler`, `gospider`
    

bash

CopyEdit

`cat live.txt | waybackurls > wayback.txt`

---

### 🔶 **4. Parameter Discovery**

> 🎯 **Goal**: Find parameters to test for XSS, SQLi, IDOR, etc.

🛠 Tools:

- `gf`, `paramspider`, `LinkFinder`, `qsreplace`
    

bash

CopyEdit

`cat wayback.txt | gf xss cat wayback.txt | gf sqli`

---

### 🔶 **5. Fuzzing and Bruteforcing**

> 🎯 **Goal**: Discover hidden endpoints, files, or logic via brute-force

🛠 Tools:

- `ffuf`, `dirsearch`, `gobuster`
    

bash

CopyEdit

`ffuf -u https://site.com/FUZZ -w raft-medium-directories.txt -mc 200,403`

---

### 🔶 **6. Load into Burp Suite — 🔥 Manual Testing Begins**

> 🎯 **Goal**: Deep testing, fuzzing, and exploitation

### 💥 Burp Suite Tasks:

- 🔍 Map endpoints using **Proxy** and **Spider**
    
- 🧪 Send requests to **Repeater** for manual tampering
    
- 🚨 Use **Intruder** for:
    
    - Bruteforcing
        
    - Bypassing WAFs
        
    - Fuzzing inputs
        
- 📦 Load **extensions**:
    
    - `Autorize` – IDOR & Auth checks
        
    - `Turbo Intruder` – Fast fuzzing
        
    - `Param Miner` – Find hidden params
        
    - `JS Link Finder` – JS endpoint scraping
        
- 📊 Use **Scanner (Pro)** for auto-vuln checks
    

> 🧠 Example: Test reflected parameters from recon in Burp Repeater with:

html

CopyEdit

`<script>alert(1)</script>`

---

### 🔶 **7. Vulnerability Testing (Manual + Tool-assisted)**

> 🎯 **Goal**: Find actual bugs – XSS, SSRF, SQLi, IDOR, etc.

🛠 Tools:

- Burp Suite
    
- `nuclei` for CVE/misconfig scanning
    
- Browser DevTools for CSP, CORS, etc.
    

---

### 🔶 **8. Reporting**

> 🎯 **Goal**: Create a clean, reproducible bug report with impact and PoC

Include:

- Request/response (Burp export)
    
- Screenshots or videos
    
- Clear steps and affected endpoints
## zone one Transfer-
---

## ✅ 1. What is DNS?

**DNS (Domain Name System)** is the internet's phonebook.

It translates **domain names (like `example.com`)** into **IP addresses (like `93.184.216.34`)**, so browsers can load websites.

---

## ✅ 2. What are Nameservers?

Nameservers are **special DNS servers** that store the DNS records for a domain.

They:

- Answer queries like “what is the IP of www.example.com?”
    
- Store DNS records like `A`, `MX`, `NS`, `TXT`, etc.
    
- Can **share records with each other** via **zone transfers**
    

---

## ✅ 3. What is a Zone File?

A **zone file** is the full list of DNS records for a domain.

It contains:

- `A` – maps domain to IPv4
    
- `AAAA` – maps domain to IPv6
    
- `CNAME` – aliases
    
- `MX` – mail servers
    
- `TXT` – metadata (SPF, DKIM, verification)
    
- `NS` – nameservers
    
- `PTR`, `SOA`, `SRV`, `NAPTR`, etc.
    

---

## ✅ 4. What is a Zone Transfer (AXFR)?

Zone transfer is a **mechanism to sync DNS records between nameservers**.

### 🔥 AXFR = "Authoritative Zone Transfer Request"

It's **used between DNS servers** to copy full zone data:

- Master to slave
    
- Primary to secondary
    

### ⚠️ If misconfigured, **anyone can ask for it** — **that’s the vulnerability**.

---

## ✅ 5. Why AXFR Is a Security Risk

If a public DNS server **allows AXFR from anyone**, an attacker can:

- Get a full list of **all DNS records**
    
- Discover **internal**, **dev**, and **hidden** subdomains
    
- Bypass brute-force recon
    
- Increase attack surface instantly
    

💣 This is a serious bug bounty finding — especially if it leaks sensitive services like:

- `dev.target.com`
    
- `admin.target.com`
    
- `db1.internal.target.com`
    

---

## ✅ 6. Real-World Analogy

- 🔍 **Normal DNS**: “What’s the phone number of _John_?”
    
- 💣 **AXFR**: “Give me your **entire phonebook** — every contact!”
    

---

## ✅ 7. Practical: Step-by-Step AXFR Test

### 🔧 Step 1: Install dig

bash

CopyEdit

`sudo apt update && sudo apt install dnsutils -y`

---

### 🔎 Step 2: Get Nameservers

bash

CopyEdit

`dig ns zonetransfer.me +short`

🔽 Output:

CopyEdit

`nsztm1.digi.ninja. nsztm2.digi.ninja.`

---

### 💣 Step 3: Run Zone Transfer

bash

CopyEdit

`dig axfr zonetransfer.me @nsztm1.digi.ninja`

✅ If vulnerable, you'll see:

- All subdomains
    
- All mail servers
    
- Admin/dev hosts
    
- Internal IPs
    
- XSS/SQLi test records
    

---

## ✅ 8. Real Bug Bounty Example

bash

CopyEdit

`dig axfr target.com @ns1.target.com`

🎯 You get:

csharp

CopyEdit

`jenkins.target.com staging.target.com api-internal.target.com dev.target.com`

You scan with:

bash

CopyEdit

`cat subdomains.txt | httpx`

And find:

- Open Jenkins → RCE
    
- Leaky dev login → IDOR
    
- API on staging → unauth access
    

→ 🔥 $1000–$5000 bounty

---

## ✅ 9. How to Extract Subdomains from AXFR Output

bash

CopyEdit

`dig axfr zonetransfer.me @nsztm1.digi.ninja | grep 'zonetransfer.me' | awk '{print $1}' | sort -u > subs.txt`

Then:

bash

CopyEdit

`cat subs.txt | httpx`

---

## ✅ 10. All Relevant DNS Record Types

|Type|Purpose|Example|
|---|---|---|
|A|IPv4 Address|`www → 93.184.216.34`|
|AAAA|IPv6 Address|`ipv6.example.com → ::1`|
|MX|Mail Server|`mail.example.com`|
|NS|Nameserver|`ns1.example.com`|
|TXT|Text/Meta|`"v=spf1 include:_spf.google.com"`|
|CNAME|Alias|`www → example.com`|
|PTR|Reverse lookup|`IP → domain`|
|SOA|Start of Authority|Info about the zone itself|
|SRV|Service records|`for SIP, VoIP, etc.`|
|NAPTR|Enum and SIP routing|`VoIP use cases`|
|LOC|Physical location|`GPS coords`|

---

## ✅ 11. Tools You Can Use

|Tool|Command|
|---|---|
|🧪 `dig`|`dig axfr example.com @ns1.example.com`|
|🧠 `dnsrecon`|`dnsrecon -d example.com -t axfr`|
|🔁 `dnsenum`|`dnsenum example.com`|
|🧼 Cleanup|`awk`, `grep`, `sort`, `uniq` for subdomain extraction|
|🌐 Scan|`httpx`, `ffuf`, `nuclei` on extracted hosts|

---

## ✅ 12. Bug Bounty Report Template

**Title**: Unauthenticated DNS Zone Transfer on `ns1.target.com`

**Impact**:

- Leaks internal infrastructure (50+ subdomains)
    
- Includes dev, staging, and internal services
    
- Expands attack surface significantly
    

**Steps to Reproduce**:

bash

CopyEdit

`dig axfr target.com @ns1.target.com`

**Recommendation**:

- Restrict AXFR to internal trusted IPs only
    
- Disable AXFR if not required
    

---

## ✅ 13. Auto Zone Transfer Tester Script (Bonus)

Want one? Just say:

> **"Give me zone transfer script"**

I’ll drop a bash or Python script to:

- Automatically test a list of domains
    
- Pull NS records
    
- Try AXFR
    
- Dump results
    

---

## 🧠 Final Summary

|Concept|Explanation|
|---|---|
|DNS|Translates domain ↔ IP|
|Nameserver|DNS server that stores zone info|
|Zone File|All DNS records for a domain|
|AXFR|Request to transfer all DNS records|
|Bug|If NS allows AXFR from anyone → critical info leak|
|Bug bounty value|🏆 P2–P3 depending on data leaked|
## 1. `nslookup` — Name Server Lookup

### 🧠 What is `nslookup`?

`nslookup` is a tool used to query DNS (Domain Name System) to get info about:

- IP addresses of domains
    
- Mail servers (MX records)
    
- Nameservers (NS)
    
- Other DNS records (CNAME, TXT, etc.)
    

---

### ✅ Basic Syntax

bash

CopyEdit

`nslookup [domain]`

### 📘 Example:

bash

CopyEdit

`nslookup example.com`

🖥️ Output:

makefile

CopyEdit

`Name:    example.com Address: 93.184.216.34`

## 2. `whois` — Domain Ownership Lookup

### 🧠 What is `whois`?

`whois` is used to look up **domain registration info**, including:

- Domain owner
    
- Registrar (GoDaddy, Namecheap, etc.)
    
- Creation & expiry dates
    
- Nameservers
    
- Admin contact (sometimes email, phone)
    

---

### ✅ Basic Syntax

bash

CopyEdit

`whois example.com`

### 📘 Example Output:

yaml

CopyEdit

`Domain Name: EXAMPLE.COM Registry Domain ID: ... Registrar WHOIS Server: whois.iana.org Registrar: RESERVED-Internet Assigned Numbers Authority Updated Date: 2024-01-01 Creation Date: 1995-08-14 Name Server: a.iana-servers.net ...`

## **What is WPScan?**

> **WPScan** is a free, open-source **WordPress vulnerability scanner** used to find:

- Vulnerable **core versions**
    
- Outdated or insecure **plugins** and **themes**
    
- Leaked **usernames**
    
- Misconfigurations and **exposed files**
    
- Known CVEs via the WPVulnDB API
    

---

## 🔍 **When to Use WPScan**

✅ If the target runs WordPress — confirmed by:

- `wp-admin`, `wp-login.php`, `wp-content`, `wp-includes`
    
- Wappalyzer/WhatWeb shows WordPress
    
- Meta tags like `<meta name="generator" content="WordPress">`
  
## ==IDOR (Indirect Object Reference)==

 