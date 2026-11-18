# Evidence Index

This directory indexes practical evidence supporting the cybersecurity portfolio.

## Evidence rules

Evidence must show what actually happened in the lab.

Preferred evidence:
- Sanitised terminal output
- Wireshark screenshots
- Configuration snapshots
- Before/after comparisons
- Test results
- Logs
- Reproduction steps
- Troubleshooting notes

Do not publish:
- Passwords
- API keys
- Tokens
- Private keys
- Sensitive personal information
- Unreviewed raw packet captures
- Unauthorised target data

## Current evidence

### DNS packet analysis

Evidence includes Kali interface and route verification, tcpdump capture, saved local PCAP, and Wireshark inspection of DNS query/response packets.

See: ../05-Reports/NET-007-DNS-Packet-Capture.md

### TCP connection lifecycle

Evidence includes the observed TCP handshake, packet flags, termination sequence, and curl timeout behaviour.

See: ../05-Reports/NET-008-TCP-Connection-Lifecycle.md

## Evidence policy

A screenshot is supporting evidence, not the conclusion.

Every evidence item should answer:

What am I looking at?
What does it prove?
What does it not prove?

This distinction will be maintained throughout the portfolio.
