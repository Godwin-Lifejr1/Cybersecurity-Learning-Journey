# NET-008 — TCP Connection Establishment and Termination

**Date:** 2026-11-02  
**Environment:** Kali Linux in Oracle VirtualBox  
**Interface:** eth0  
**Scope:** HTTPS connections initiated by the learner's own Kali VM

## Objective

Observe TCP connection establishment, data exchange, and connection termination using tcpdump. Distinguish TCP-level success from the success of the application request.

## Commands used

Capture TCP traffic to HTTPS port 443:

```bash
sudo tcpdump -ni eth0 'tcp port 443'
```

Generate an HTTP/1.1 HEAD request over HTTPS:

```bash
curl --http1.1 -I --connect-timeout 10 --max-time 20 https://korlinktech.com
```

Command breakdown:

- `sudo`: runs tcpdump with elevated privileges, which are commonly required for packet capture.
- `tcpdump`: command-line packet capture and inspection utility.
- `-n`: disables address and port name resolution so numeric addresses and ports remain visible.
- `-i`: selects the capture interface.
- `eth0`: the Kali VM's observed network interface.
- `tcp port 443`: capture filter selecting TCP packets where either source or destination port is 443.
- `curl`: command-line client for making network requests.
- `--http1.1`: asks curl to use HTTP/1.1.
- `-I`: requests headers only using an HTTP HEAD request.
- `--connect-timeout 10`: limits the time allowed to establish the connection to 10 seconds.
- `--max-time 20`: limits the total operation time to 20 seconds.

## Observed TCP connection

The capture showed a TCP handshake involving:

- Kali source address: `10.0.2.15`
- Kali ephemeral source port: `38622`
- Remote address: `172.67.212.235`
- Remote destination port: `443`

Observed flag sequence:

1. Kali to remote host: `[S]` — SYN.
2. Remote host to Kali: `[S.]` — SYN-ACK.
3. Kali to remote host: `[.]` — ACK.

This confirms that the TCP three-way handshake completed for this observed flow.

The capture also showed packets marked `[P.]` and other ACK packets, indicating TCP payload transfer and acknowledgments. Packet payload lengths varied; the HTTPS application data was not readable from this TCP capture because it was encrypted.

## Observed termination

For the flow using Kali source port `38622`, the screenshot showed:

- Kali sent `[F.]` (FIN-ACK).
- The remote endpoint sent `[.]` acknowledging that FIN.
- The remote endpoint then sent `[F.]` (FIN-ACK).
- A repeated server FIN was visible in the capture.
- Kali sent `[.]` acknowledging the server FIN.

This is consistent with an orderly TCP shutdown exchange. The repeated FIN is consistent with retransmission, but the screenshot alone does not establish why it was repeated.

## Other observed flow

The capture also showed a separate connection attempt involving `104.21.23.191:443`:

- Kali sent SYN.
- The remote endpoint replied with SYN-ACK.
- Kali then sent RST.

This flow was reset rather than completing the usual three-way handshake. The packet evidence does not establish the reason; a reset should not automatically be labelled malicious.

## curl result and interpretation

The curl terminal reported:

```text
curl: (28) Operation timed out after 20003 milliseconds with 0 bytes received
```

This means curl reached its total operation timeout without receiving response data it could report. The packet capture nevertheless shows that TCP communication occurred. A completed TCP handshake does not guarantee that TLS negotiation or the HTTP request will succeed. The exact cause of the curl timeout was not determined in this lab.

## Capture statistics

The learner's screenshot showed:

- 23 packets captured
- 23 packets received by filter
- 0 packets dropped by kernel

## What I learned

- TCP uses SYN, SYN-ACK, and ACK to establish a connection.
- FIN is used for orderly shutdown; RST resets a connection.
- ACK packets acknowledge sequence-space progress.
- Ephemeral source ports identify individual client-side connections.
- TCP payload metadata remains observable even when HTTPS application data is encrypted.
- A TCP connection can be established while the higher-level TLS or HTTP operation still times out.
- Packet evidence should be separated from assumptions about the cause of a network event.

## Evidence and limitations

Findings are based on the learner's terminal screenshot dated 2026-11-02. The raw packet capture was not supplied as a file and is not committed to this repository. The report records only what is visible in the screenshot; it does not claim to identify the cause of the curl timeout or the RST.

## Next steps

- Continue TCP/UDP fundamentals and socket inspection.
- Practise identifying connection states and teardown sequences in Wireshark.
- Investigate the curl timeout separately if it recurs.
- Continue with DNS record types and DNS security after the TCP/UDP foundation.
