# Lab 2: Windows Security Event Logs

Goal: Capture and explain successful and failed login events (4624, 4625) in a Windows 11 VirtualBox VM.

## Architecture
- Hypervisor: VirtualBox (Adapter 1: NAT, Adapter 2: Host-Only)
- Windows 11 VM (Host-Only IP: 192.168.56.101/24)

## Steps I Performed
1. Locked the Windows 11 VM using 'Win+L'.
2. Entered an incorrect password multiple times to generate 4625 (Failed logon).
3. Logged in with the correct password to generate 4624 (Successful logon).
4. Opened Event Viewer → Windows Logs → Security.
5. Applied filter for Event IDs 4624, 4625.
6. Exported filtered log to 'security_auth.evtx'.
7. Took screenshots of:
   - Filter Current Log dialog
   - A 4625 (Failed logon) event details

## Key Findings
- 4624 (Successful logon): User authenticated successfully, showing logon type and account details.
- 4625 (Failed logon): Failed authentication attempt, logging username, source, and failure reason.
- Useful for detecting brute-force or password spray attempts when 4625 spikes occur.

## Screenshots
- Filtered Log [Screenshot](./screenshots/lab02_logs.png)
- Failed Logon Event 4625 [Screenshot](./screenshots/lab02_4625.png)
- Successful Logon Event 4624 [Screenshot](./screenshots/lab02_4624.png)
- Exported Log [File](./Artifacts/security_auth.evtx)
