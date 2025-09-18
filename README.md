# SOC Home Lab (Windows 11 + Ubuntu)

Hands-on portfolio project designed for SIEM/SOC analyst roles.  
This lab series demonstrates core cybersecurity skills across log analysis, networking, host hardening, vulnerability scanning, and threat detection.

## Architecture
- **Host:** Windows 11  
- **Hypervisor:** VirtualBox  
- **VMs:** Ubuntu (server), Windows 11 (workstation)  
- **Networks:** NAT for internet, Host-Only/Internal for isolated lab

## Labs
- [Lab 1: Wireshark & Networking](/lab1-wireshark) -  Capture and analyze ARP, ICMP, DNS, HTTP, and TLS traffic.
- [Lab 2: Windows Security Event Logs (Authentication)](/lab2-windows-security-event-logs) - Collect and analyze Windows authentication events (4624/4625)
- [Lab 3: Linux Log Analysis](/lab3-linux-log-analysis) - Analyze Ubuntu SSH authentication logs with `journalctl` and `/var/log/auth.log`
- [Lab 4: Firewall & Network Hardening](/lab4-firewall-network-hardening) - Configure UFW (Ubuntu) and Windows Defender Firewall for least-privilege network access.
- [Lab 5: Password Auditing (John/Hashcat)](/lab5-password-auditing)
- [Lab 6: Threat Intel Dashboard](/lab6-threat-intel-dashboard)
- [Lab 7: Phishing Awareness (GoPhish & MailHog)](/lab7-phishing-awareness)

## How to Use This Repo
Each lab folder includes:  
- Step-by-step instructions  
- Commands and configurations  
- Screenshots and artifacts  
- Key findings
