# ReconScript
A custom Bash script designed to automate basic infrastructure reconnaissance and vulnerability scanning.

## 🛠️ Features
The script provides an interactive command-line menu with two main automation tracks:

1. **Nmap Scan**
   * Prompts for a target address.
   * Runs an aggressive scan (`-A`) with service version detection (`-sV`) across all 65,535 ports (`-p1-65535`).

2. **OSINT Framework (Subfinder + Httpx + Nuclei)**
   * Prompts for a target domain.
   * **Subfinder:** Passively gathers subdomains and saves them to a temporary file.
   * **Httpx-toolkit:** Validates live HTTP/HTTPS servers, extracting status codes and page titles.
   * **Nuclei:** Automatically checks the validated live hosts for known vulnerabilities.

## 🚀 Usage Guide

1. Make the script executable:
   ```bash
   chmod +x recon.sh
   ```

2. Run it:
   ```bash
   ./recon.sh
   ```

3. Choose an option from the menu:
   ```
   1. Nmap
   2. subfinder+httpx+nuclei
   ```

4. Follow the prompts to enter a target IP/hostname (option 1) or domain (option 2).

## 📦 Dependencies

This script assumes the following tools are already installed and on your `PATH`:

* [`nmap`](https://nmap.org/)
* [`subfinder`](https://github.com/projectdiscovery/subfinder)
* [`httpx-toolkit`](https://github.com/projectdiscovery/httpx)
* [`nuclei`](https://github.com/projectdiscovery/nuclei)

All four are commonly preinstalled on Kali Linux, or installable via `go install` for each ProjectDiscovery tool.

## 📁 Reports

Example writeups produced using this script, located in [`report/`](report/):

* [`report/OSINT_Report_vulhub.md`](report/OSINT_Report_vulhub.md) — passive OSINT footprinting exercise (WHOIS, DNS, certificate transparency, search engine indexing, Shodan), with supporting screenshots in the same folder
* [`report/nmap_report.md`](report/nmap_report.md) — full-port Nmap scan against an isolated local Metasploitable VM
* [`report/subfinder_report.md`](report/subfinder_report.md) — subdomain enumeration and live-host validation writeup

## ⚖️ Scope & Ethics

* The **OSINT report** uses only passive, publicly available data sources (WHOIS, DNSDumpster, BuiltWith, crt.sh, search engines, Shodan's existing index). No active scanning was performed against the example domain as part of producing that report.
* The **Nmap/vulnerability scanning option** is intended for use against infrastructure you own or are explicitly authorized to test — e.g., a local lab VM (such as Metasploitable), a CTF environment, or a system covered by a signed pentest engagement.
* Do not point this script's active scanning options (Nmap, Nuclei) at systems you do not have explicit, documented authorization to test. Unauthorized scanning can be illegal depending on jurisdiction.

## 📄 License

Specify a license here (e.g., MIT) if you'd like others to be able to reuse this script.
