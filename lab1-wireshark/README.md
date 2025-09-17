# Lab 1: Wireshark & Networking

Goal: Capture and explain ARP, ICMP, DNS, TCP handshake, HTTP, TLS in a controlled VirtualBox lab.

## Architecture
- Hypervisor: VirtualBox (Adapter 1: NAT, Adapter 2: Host-Only)
- Windows 11 (Host-Only IP: 192.168.56.101/24)
- Ubuntu (Host-Only IP: 192.168.56.102/24)

## Steps I Performed
1. Verified adapters (NAT & Host-Only) on both VMs.
2. Set static Host-Only IPs.
3. Enabled Windows inbound ICMP.
4. Installed Wireshark (Windows 11), Wireshark/tcpdump/iperf3 (Ubuntu).
5. Ran baseline tests: "ipconfig", "ip a", "ping", "traceroute".
6. Captures:
   - ARP & ICMP across Host-Only: [Capture](./captures/lab01_arp_icmp_capture.pcapng)
   - DNS via NAT: [Capture](./captures/lab01_nat_dns_capture.pcapng)
   - HTTP to Ubuntu local server: [Capture](./captures/lab01_http_capture.pcapng)
   - TLS to public HTTPS site: [Capture](./captures/nat_tls_capture.pcapng)

## Key Findings
- ARP: Observed "who-has" and "is-at" resolving MACs on the Host-Only LAN.
- ICMP: Echo Requests (type 8) and Replies (type 0) showed successful reachability.
- DNS: Query for "example.com" over UDP/53 with matching A/AAAA answers.
- TCP Handshake: SYN → SYN/ACK → ACK before data transfer.
- HTTP (cleartext): Visible GET and 200 OK, full payload readable (why HTTPS matters).
- TLS: ClientHello/ServerHello & SNI visible; application data encrypted.

## Screenshots & Commands
- ARP & ICMP: [Screenshot](./screenshots/lab01_arp_icmp.png), [Command](./screenshots/lab01_arp_icmp_command.png)
- DNS Query: [Screenshot](./screenshots/lab01_dns.png), [Command](./screenshots/lab01_dns_command.png)
- TCP Handshake & HTTP: [Screenshot](./screenshots/lab01_tcp_handshake_http.png), [Command](/screenshots/lab01_tcp_handshake_http_command.png)
- TLS Handshake: [Screenshot](/screenshots/lab01_tls_handshake.png), [Command](/screenshots/lab01_tls_handshake_command.png)
