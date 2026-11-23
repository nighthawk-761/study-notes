# Computer Networks

인터넷의 기본 구조부터 Application Layer, Transport Layer, TCP Congestion Control까지 개념 중심으로 정리한 노트입니다.

> 공개용 노트에서는 과제 자료와 제3자 교안 이미지를 제외했습니다. 구조와 동작 과정은 직접 작성한 Mermaid 및 텍스트 도식으로 설명합니다.

## 1. 네트워크 기초

- [Internet과 Network Architecture](internet-and-network-architecture.md) — Internet 구성 요소, Protocol, Edge·Access·Core
- [Access Network와 Physical Media](access-networks-and-physical-media.md) — HFC, DSL, FTTH, Ethernet, Fiber, Wireless
- [Packet Switching과 Internet Structure](packet-switching-and-internet-structure.md) — Store-and-Forward, Circuit Switching, ISP·IXP·Peering
- [Network Performance](network-performance.md) — Delay, Loss, Throughput, Bottleneck, Traceroute
- [Protocol Layering과 Network Security](protocol-layering-and-security.md) — TCP/IP 5계층, Encapsulation, TLS, 주요 공격
- [Wireless와 Mobile Networks](wireless-and-mobile-networks.md) — Wi-Fi, CSMA/CA, 5G, MIMO·OFDMA

## 2. Application Layer

- [Application Architecture와 HTTP](application-architecture-and-http.md) — Client-Server, P2P, Socket, HTTP, Cookie, Web Cache
- [DNS와 E-mail](dns-and-email.md) — Name Resolution, Resource Record, SMTP, Mail Access
- [P2P, Streaming과 CDN](p2p-streaming-and-cdn.md) — BitTorrent, DASH, Buffering, CDN 배치와 DNS
- [Socket Programming](socket-programming.md) — UDP·TCP Client/Server의 API와 통신 과정

## 3. Transport Layer

- [Transport Layer와 UDP](transport-layer-and-udp.md) — Multiplexing, Demultiplexing, UDP Header와 Checksum
- [Reliable Data Transfer](reliable-data-transfer.md) — rdt, Stop-and-Wait, Go-Back-N, Selective Repeat
- [TCP](tcp.md) — Segment, Sequence/ACK, RTT, Flow Control, Connection Management
- [Congestion Control](congestion-control.md) — AIMD, Slow Start, CUBIC, ECN, Fairness, QUIC

## 외부 참고 자료

- [RFC 9110: HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html)
- [RFC 1034·1035: DNS](https://www.rfc-editor.org/info/rfc1034/) · [Implementation](https://www.rfc-editor.org/info/rfc1035/)
- [RFC 768: UDP](https://www.rfc-editor.org/rfc/rfc768.html)
- [RFC 9293: TCP](https://www.rfc-editor.org/rfc/rfc9293.html)
- [RFC 5681: TCP Congestion Control](https://www.rfc-editor.org/rfc/rfc5681.html)
- [RFC 9000: QUIC](https://www.rfc-editor.org/rfc/rfc9000.html)
- [RFC 8446: TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446.html)
- [IEEE 802.11 Working Group](https://www.ieee802.org/11/)
- [3GPP TS 23.501: 5G System Architecture](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3144)
