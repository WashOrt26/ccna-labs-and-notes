# Lab 3: TCP/IP Model & Encapsulation

## 📋 Overview
This lab corresponds to **Day 3** of Jeremy's IT Lab CCNA 200-301 course. The primary objective is to understand the 5-layer network model, the distinction between protocols and standards, how data encapsulation works, and how Protocol Data Units (PDUs) are structured across layers.

* **Course Reference:** Day 3 - TCP/IP Model
* **Simulator Used:** Theoretical / Conceptual Lab

---

## 🌐 Fundamentals of Protocols & Standards
* **Protocol:** A set of rules defining how data should be communicated between devices over a network.
* **Standard:** An agreed-upon specification that describes how a protocol or technology should work.
* **Why TCP/IP Won:** TCP/IP became dominant over legacy vendor-proprietary solutions because it was published as open standards that any vendor could implement and run across diverse network types.

### Standards Organizations
* **IEEE (Institute of Electrical and Electronics Engineers):** Develops many of the technologies used on local area networks (LANs).
  * *Ethernet:* IEEE 802.3
  * *Wi-Fi:* IEEE 802.11
* **IETF (Internet Engineering Task Force):** An open community that defines core internet protocols (TCP, IP, UDP, HTTP, DNS, etc.) and publishes standards in documents called **RFCs (Request for Comments)**.

---

## 🧱 The 5-Layer Network Model
Network communication involves complex tasks—such as physical signal transmission, local delivery, routing across networks, end-to-end conversations, and application services. A layered model groups related jobs, where each layer relies on the services of the layer below and provides services to the layer above.

1. **Layer 1: Physical Layer**
   * **Function:** Sends and receives raw bits as electrical, optical, or radio signals over the transmission medium.
   * **Details:** Defines cables, connectors, signal levels, and link speeds.
   * **Examples:** Copper UTP cables, fiber-optic cables, Wi-Fi radios/antennas, and Network Interface Cards (NICs).
2. **Layer 2: Local Network Layer (Data Link)**
   * **Function:** Provides hop-to-hop delivery of messages on a local network segment. Uses **MAC addresses** to identify interfaces.
   * **Key Concept:** A "hop" is one step along the path between two devices (e.g., host-to-router or router-to-router). Switches extend the local network segment but do not count as routing hops.
   * **Protocols:** Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11).
3. **Layer 3: Internet Layer**
   * **Function:** Provides end-to-end delivery of packets across multiple distinct networks. Uses **IP addresses** to identify hosts.
   * **Key Devices:** Routers operate mainly at this layer, inspecting destination IP addresses to forward traffic toward its destination.
   * **Protocols:** IP (IPv4, IPv6), ICMP (Internet Control Message Protocol).
4. **Layer 4: Transport Layer**
   * **Function:** Provides process-to-process (service-to-service) communication between application processes on communicating hosts. Uses **port numbers** to identify specific processes.
   * **Protocols:** 
     * **TCP (Transmission Control Protocol):** Connection-oriented, robust, and reliable delivery.
     * **UDP (User Datagram Protocol):** Simple, connectionless, and efficient.
5. **Layer 5: Application Layer**
   * **Function:** Where network communications interface directly with applications (often mapped conceptually to OSI Layer 7). Defines how application processes format, send, and interpret data.
   * **Protocols:** HTTP/HTTPS (web browsing), FTP/TFTP (file transfer), SMTP/POP3/IMAP (email), DNS.

---

## 📦 Encapsulation, Decapsulation & PDUs
As data moves through the protocol stack, headers (and trailers) are added or removed in a process known as encapsulation and decapsulation.

### Protocol Data Units (PDUs) and Payloads
At each stage of the encapsulation process, the message is referred to as a PDU:
* **L4 PDU (Segment / Datagram):** Application Data + Transport Layer Header. *(TCP creates segments; UDP creates datagrams).*
* **L3 PDU (Packet):** L4 PDU + Internet Layer Header.
* **L2 PDU (Frame):** L3 PDU + Data Link Header and Trailer. *(This is what is actually transmitted over the physical wire).*

> **Payload Definition:** Everything encapsulated inside a layer's header or trailer is considered the payload for that layer. For instance, a packet's payload is the transport segment/datagram, and a frame's payload is the network packet.