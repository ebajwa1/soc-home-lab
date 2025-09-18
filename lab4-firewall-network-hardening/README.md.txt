# Lab 4: Basic Firewall & Network Hardening

Goal: Show host-based firewall management on Ubuntu (UFW) and Windows (Defender Firewall) with least-privilege rules, and verify with simple network tests.

## Architecture
- Hypervisor: VirtualBox (Adapter 1: NAT, Adapter 2: Host-Only)
- Windows 11 (Host-Only IP: 192.168.56.101/24)
- Ubuntu (Host-Only IP: 192.168.56.102/24)

## Steps I Performed
1. Verified Host-Only connectivity (Windows ↔ Ubuntu).
2. On Ubuntu:
   - Created a simple web page ('index.html') and served it on port 80:
     --bash
     echo "Hello from Ubuntu (port 80)" > index.html
     sudo nohup python3 -m http.server 80 --bind 0.0.0.0 &
   - From Windows, confirmed access with:
     --powershell
     curl http://192.168.56.102
   - Configured UFW firewall rules:
     --bash
     sudo ufw default deny incoming
     sudo ufw default allow outgoing
     sudo ufw allow 22/tcp
     sudo ufw deny 80/tcp
     sudo ufw enable
     sudo ufw status numbered
     ```
   - Verified SSH remained open but HTTP was blocked ('curl' failed).
3. On Windows:
   - Opened wf.msc → Inbound Rules.
   - Disabled File and Printer Sharing (Echo Request – ICMPv4-In).
   - Verified that Ubuntu could no longer ping Windows.
4. Captured before/after screenshots of firewall rules and test results.

## Key Findings
- Ubuntu: With 'ufw deny 80/tcp', port 80 was blocked while port 22 remained open, demonstrating least-privilege network access.
- Windows: Disabling inbound ICMPv4 echo prevented ping replies, reducing the system’s network visibility to attackers.
- Combined, these changes show practical host-based firewall hardening across Linux and Windows.

## Screenshots
- Ubuntu web server setup [Screenshot](./screenshots/lab04_webserver_setup.png)   
- Ubuntu curl success [Screenshot](./screenshots/lab04_curl_success.png)  
- Ubuntu UFW status [Screenshot](./screenshots/lab04_ufw_status.png) 
- Ubuntu curl blocked [Screenshot](./screenshots/lab04_curl_blocked.png) 
- Windows Firewall inbound ICMP rules [Screenshot](./screenshots/lab04_windows_icmp_disabled.png) 

