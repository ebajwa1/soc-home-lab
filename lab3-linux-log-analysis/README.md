# Lab 3: Linux Log Analysis

Goal: Show log monitoring on Ubuntu by capturing failed and successful SSH login events using `journalctl` and `/var/log/auth.log`.

## Architecture
- Hypervisor: VirtualBox (Adapter 1: NAT, Adapter 2: Host-Only)
- Windows 11 (Host-Only IP: 192.168.56.101/24)
- Ubuntu (Host-Only IP: 192.168.56.102/24)

## Steps I Performed
1. Verified Host-Only connectivity between Windows and Ubuntu ('ping' both directions).
2. Ensured OpenSSH Server was installed and running on Ubuntu ('openssh-server', 'systemctl enable --now ssh').
3. From Windows PowerShell, attempted SSH to Ubuntu:
   - Entered wrong password 3 times (failed login attempts).
   - Entered correct password once (successful login).
4. On Ubuntu, viewed authentication logs with:
   - 'sudo journalctl -u ssh -S today | grep -i "Failed password"'
5. Captured screenshots of failed login attempts and log entries.

## Key Findings
- Failed SSH attempts are logged as:  
  'Failed password for <user> from <ip> port <port> ssh2'
- Successful SSH** is logged as:  
  'Accepted password for <user> from <ip> ...'
- Multiple consecutive '"Failed password"' entries from one source IP indicate possible brute-force or password-spraying attacks.
- Log review lets analysts correlate suspicious authentication behavior across systems.

## Screenshots
- SSH Attempts (Windows → Ubuntu) [Screenshot](/screenshots/lab03_win11_login_attempts.png)  
- Failed Login Output (Windows → Ubuntu) [Screenshot](/screenshots/lab03_failed_output.png)  
