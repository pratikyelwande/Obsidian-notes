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