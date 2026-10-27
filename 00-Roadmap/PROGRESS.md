# Cybersecurity Progress Tracker

Update this file after each lesson or lab. Do not mark work complete before practice, evidence, and review.

| ID | Topic / milestone | Status | Evidence link | Notes / next action |
|---|---|---|---|---|
| NET-001 | Lab environment and network interface discovery | Complete | [DNS/network lab report](../05-Reports/NET-007-DNS-Packet-Capture.md) | Verified `eth0` UP, IPv4 `10.0.2.15/24`, subnet `10.0.2.0/24`, and default route via `10.0.2.2`. |
| NET-002 | OSI and TCP/IP models | In progress | — | Introductory lesson delivered; explain encapsulation and map common protocols in your own words. |
| NET-003 | IPv4 addressing and CIDR | In progress | — | Introductory subnetting lesson delivered; complete the /26 exercises and show your calculations. |
| NET-004 | Default gateway, ARP, and routing | In progress | [DNS/network lab report](../05-Reports/NET-007-DNS-Packet-Capture.md) | Inspected `ip route`, verified gateway reachability with 4/4 ping replies, and inspected `ip neigh`. Observed the gateway entry remain `STALE`; reviewed what this cache state means. Still need to explain local vs remote destinations and deepen ARP practice. |
| NET-005 | TCP, UDP, and ports | In progress | — | Introductory lesson delivered; run `ss -tuln` and explain the output from your VM. |
| NET-006 | DNS and DHCP | In progress | [DNS packet capture report](../05-Reports/NET-007-DNS-Packet-Capture.md) | DNS A/AAAA queries and responses were captured and inspected. DHCP concepts and further DNS troubleshooting remain to be covered. |
| NET-007 | Packet capture fundamentals | Complete | [DNS packet capture report](../05-Reports/NET-007-DNS-Packet-Capture.md) | Captured four DNS packets with tcpdump, saved `dns-lab.pcap` locally, and inspected matching query/response transaction IDs in Wireshark. Raw PCAP is not committed. |
| LNX-001 | Linux filesystem and navigation | Not started | — | Begin after the networking foundation. |
| PY-001 | Python fundamentals | Not started | — | Begin after Linux fundamentals. |
| SEC-001 | Security principles and lab safety | In progress | — | Lab safety and authorisation boundaries reviewed; continue using isolated or explicitly authorised systems. |

## Status definitions
- **Not started** — no lesson or practical work yet.
- **In progress** — learning has begun; practical verification may still be pending.
- **Blocked** — waiting on a dependency or troubleshooting issue.
- **Review needed** — lab ran, but evidence or understanding needs improvement.
- **Complete** — practical work, evidence, and reflection are documented and reviewed.

## Learning log
Add newest entries at the top. A course lesson being provided does not mean a practical lab has been completed.

| Date | Lesson / lab | What I learned | Problem solved | Next step |
|---|---|---|---|---|
| 2026-10-27 | NET-007: DNS packet capture and Wireshark analysis | Verified Kali interface and route; tested gateway, DNS resolution, and HTTPS; captured four DNS packets with tcpdump; inspected A and AAAA queries and matching response transaction IDs in Wireshark. | DNS lookup results were initially absent, then later worked; HTTPS returned HTTP/2 301 for Google and HTTP/2 200 for Korlink. Cause of the earlier inconsistency remains unconfirmed. DNS resolver shown in `/etc/resolv.conf` differed from the server observed in the later capture, and that discrepancy remains unresolved. | Gateway ping succeeded (4/4, 0% loss); `ip neigh` showed the gateway MAC mapping as `STALE`. Added the follow-up observation to the lab report. Next: explain ARP/local vs remote traffic, then continue TCP/UDP exercises. |
| 2026-10-26 | Module 1 launched: Networking Fundamentals | Started a full-field cybersecurity course with networking first. Covered OSI/TCP-IP, IPv4/CIDR, common ports, routing, ARP, DNS, Linux network commands, virtual lab design, and packet capture workflow. | No hands-on results had been reported at launch; practical results are now recorded in the 2026-10-27 entry. | Continue remaining networking fundamentals and retain screenshots/evidence for future labs. |
