# LAB-09 — Network Forensics Investigation

## Overview

This project presents a network forensic investigation conducted in a controlled cybersecurity training environment.

The investigation analyzes a 57-packet PCAP file using Wireshark to identify suspicious network activity, reconstruct an event timeline, and assess whether the available evidence supports unauthorized access or data exfiltration.

## Investigation Objectives

- Identify the source and destination of suspicious traffic.
- Analyze TCP port probing and connection establishment.
- Examine HTTP requests and server responses.
- Reconstruct the sequence of network events.
- Document evidence-based findings and investigation limitations.

## Tools Used

- Kali Linux
- Wireshark
- Linux command-line utilities
- SHA-256 integrity verification

## Key Findings

| Finding | Evidence |
|---|---|
| Suspected source | 172.28.9.77 |
| Target server | 172.28.9.20 |
| TCP port probing | Ports 22, 80, 443, 445, and 8080 |
| Established connection | TCP port 80 |
| GET /admin | HTTP 403 Forbidden |
| GET /diagnostics | HTTP 404 Not Found |
| GET /server-status | HTTP 403 Forbidden |

The observed activity is consistent with network and web reconnaissance.

A successful TCP connection was established, but the inspected HTTP responses did not demonstrate successful access to protected resources.

**No successful exploitation or data exfiltration was established from the available packet capture.**

## Evidence Integrity

The original PCAP was verified using SHA-256:

```bash
sha256sum -c network-evidence-master.pcap.sha256
```

Verification result:

```text
network-evidence-master.pcap: OK
```

## Investigation Screenshots

### 1. TCP Port Probing

![TCP Port Probes](screenshots/01-tcp-port-probes.png)

### 2. TCP Three-Way Handshake

![TCP Handshake](screenshots/02-tcp-handshake.png)

### 3. HTTP /admin — 403 Forbidden

![HTTP Admin](screenshots/03-http-admin-403.png)

### 4. HTTP /diagnostics — 404 Not Found

![HTTP Diagnostics](screenshots/04-http-diagnostics-404.png)

### 5. HTTP /server-status — 403 Forbidden

![HTTP Server Status](screenshots/05-http-server-status-403.png)

## Full Investigation Report

For the detailed analysis, event timeline, evidence assessment, security recommendations, and investigation limitations, see:

[Forensic Investigation Report](reports/forensic-investigation-report.md)

## Conclusion

The LAB-09 investigation identified TCP probing and HTTP endpoint enumeration directed at a web server.

The evidence supports a classification of suspected network and web reconnaissance. It does not establish the identity or intent of the source, successful exploitation, or data exfiltration.

All conclusions are limited to the supplied training PCAP.
