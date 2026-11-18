# Cybersecurity Progress Tracker

Update this file after each lesson or lab. Do not mark work complete before practice, evidence, and review.

| ID | Topic / milestone | Status | Evidence link | Notes / next action |
|---|---|---|---|---|
| NET-001 | Lab environment and network interface discovery | Complete | [DNS/network lab report](../05-Reports/NET-007-DNS-Packet-Capture.md) | Verified eth0 UP, IPv4 10.0.2.15/24, subnet 10.0.2.0/24, and default route via 10.0.2.2. |
| NET-002 | OSI and TCP/IP models | In progress | — | Introductory lesson delivered; explain encapsulation and map common protocols in your own words. |
| NET-003 | IPv4 addressing and CIDR | In progress | — | Introductory subnetting lesson delivered; complete the /26 exercises and show calculations. |
| NET-004 | Default gateway, ARP, and routing | In progress | [DNS/network lab report](../05-Reports/NET-007-DNS-Packet-Capture.md) | Inspected ip route, verified gateway reachability with 4/4 ping replies, and inspected ip neigh. Observed the gateway entry as STALE and reviewed what this cache state means. Still need deeper local-vs-remote routing practice. |
| NET-005 | TCP, UDP, ports, and connection lifecycle | In progress | [TCP connection lifecycle report](../05-Reports/NET-008-TCP-Connection-Lifecycle.md) | Captured a TCP three-way handshake to TCP/443, observed payload/ACK traffic, FIN-based termination, a repeated FIN, and a separate RST flow. Curl timed out despite observed TCP communication; cause not established. |
| NET-006 | DNS and DHCP | In progress | [DNS packet capture report](../05-Reports/NET-007-DNS-Packet-Capture.md) | DNS A/AAAA queries and responses were captured and inspected. DHCP concepts and further DNS troubleshooting remain to be covered. |
| NET-007 | Packet capture fundamentals and Wireshark | Complete | [DNS packet capture report](../05-Reports/NET-007-DNS-Packet-Capture.md) | Captured DNS packets with tcpdump, saved dns-lab.pcap locally, and inspected matching query/response transaction IDs in Wireshark. Applied the dns display filter and began learning the packet-list, packet-details, and raw-bytes panes. Raw PCAP is not committed. |
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
| 2026-11-18 | Portfolio and evidence review | Reviewed the repository structure against the goal of building an employable cybersecurity portfolio. Confirmed that existing practical work includes DNS/Wireshark and TCP lifecycle evidence. | Identified that the repository needed clearer separation between roadmap, evidence, projects, and career-readiness material. Added portfolio structure and career documentation without inventing additional completed work. | Continue networking training and convert each verified lab into strong, interview-ready evidence. |
| 2026-11-13 | NET-007: Wireshark DNS display filtering | Applied the Wireshark display filter dns to an existing dns-lab.pcap capture and confirmed DNS query/response packets. Began learning the packet-list, packet-details, and raw-bytes panes and how a DNS transaction maps across IPv4, UDP, and DNS layers. | Successfully isolated DNS traffic and identified the query for korlinktech.com and the response addresses. | Inspect DNS query and response fields in detail, then continue with additional Wireshark display filters and packet-analysis exercises. |
| 2026-11-02 | NET-008: TCP connection establishment and termination | Captured SYN, SYN-ACK, ACK for a connection from Kali 10.0.2.15:38622 to remote 172.67.212.235:443; observed PSH-ACK/data packets, FIN-based shutdown, a repeated FIN, and a separate SYN/SYN-ACK/RST flow. Reviewed ephemeral ports, TCP flags, retransmission, and why TCP success does not guarantee HTTP success. | Tcpdump captured 23 packets with 0 reported kernel drops. Curl to Korlink timed out after about 20 seconds with 0 bytes received, even though TCP communication was visible. Exact cause of the timeout and RST was not established. | Complete the TCP knowledge check; continue TCP/UDP socket inspection and Wireshark connection-state analysis. |
| 2026-10-27 | NET-007: DNS packet capture and Wireshark analysis | Verified Kali interface and route; tested gateway, DNS resolution, and HTTPS; captured four DNS packets with tcpdump; inspected A and AAAA queries and matching response transaction IDs in Wireshark. | DNS lookup results were initially absent, then later worked; HTTPS returned HTTP/2 301 for Google and HTTP/2 200 for Korlink. Cause of the earlier inconsistency remains unconfirmed. DNS resolver shown in /etc/resolv.conf differed from the server observed in the later capture, and that discrepancy remains unresolved. | Gateway ping succeeded with 4/4 and 0% loss; ip neigh showed the gateway MAC mapping as STALE. Continue ARP/local-vs-remote traffic analysis and TCP/UDP exercises. |
| 2026-10-26 | Module 1 launched: Networking Fundamentals | Started a full-field cybersecurity course with networking first. Covered OSI/TCP-IP, IPv4/CIDR, common ports, routing, ARP, DNS, Linux network commands, virtual lab design, and packet capture workflow. | No hands-on results had been reported at launch; practical results were recorded in later entries. | Continue remaining networking fundamentals and retain screenshots/evidence for future labs. |
