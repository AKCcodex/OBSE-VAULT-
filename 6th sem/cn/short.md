### 1. Signal Characteristics and Network Types

**a) Pulse Rate and Bit Rate Calculation:**
- **Pulse Rate:** Pulse rate is the reciprocal of the pulse duration. Given the pulse duration is 1 ms (millisecond):

- **Bit Rate:** Bit rate is calculated as the number of bits per signal level multiplied by the pulse rate. Given there are 4 data levels,

**b) Definitions:**
- **LAN (Local Area Network):** A network that connects computers within a limited area such as a residence, school, laboratory, or office building.
- **MAN (Metropolitan Area Network):** A network that spans a metropolitan area, usually a city or large campus.
- **WAN (Wide Area Network):** A network that covers a broad area (i.e., any telecommunications network that links across metropolitan, regional, or national boundaries).

### 2. Error Correction and Topology

**a) Forward Error Correction:**
- **Definition:** Forward Error Correction (FEC) is a technique used in data transmission to enhance the reliability of data. The sender adds redundant data (error correction code) to its messages, which allows the receiver to detect and correct errors without needing a retransmission.
- **Detailed Discussion:** FEC involves encoding the message in such a way that the receiver can detect and correct errors using the redundant bits. Common FEC methods include Hamming Code, Reed-Solomon Code, and Convolutional Code. It is widely used in applications where retransmissions are costly or impossible, such as satellite and space communications.

**b) Bus Topology:**
- **Explanation:** In bus topology, all devices are connected to a single central cable, called the bus. Data sent by a device is available to all other devices on the network, but only the intended recipient accepts and processes that data. This topology is relatively easy to install and requires less cable than other topologies, but a failure in the main cable can disable the entire network.

### 3. Bit Rate and Baud Rate

**Definitions:**
- **Bit Rate:** The number of bits transmitted per second.
- **Baud Rate:** The number of signal units transmitted per second.

**Calculation:**
- **Given:** An analog signal carries 4 bits per signal unit, and 1000 signal units are sent per second.
  \[
  \text{Baud Rate} = 1000 \text{ signal units per second}
  \]
  \[
  \text{Bit Rate} = \text{Baud Rate} \times \text{Number of bits per signal unit} = 1000 \times 4 = 4000 \text{ bits per second}
  \]

### 4. Network Devices

**a) Gateways:**
- **Definition:** Gateways are network nodes that serve as an access point to another network. They facilitate the communication between different network architectures and protocols by translating the data format.

**b) Hub vs. Switch:**
- **Hub:** A hub is a simple network device that broadcasts incoming data packets to all devices in the network, regardless of the destination address.
- **Switch:** A switch is more advanced and can filter and forward data to specific devices on the network based on MAC addresses.

### 5. Error Types and CSMA/CD

**a) Single-bit Error vs. Burst Error:**
- **Single-bit Error:** An error in which only one bit in the data unit is changed.
- **Burst Error:** An error where two or more bits in the data unit are changed. These bits are not necessarily contiguous.

**b) CSMA/CD in Wireless LAN:**
- **Reason:** CSMA/CD (Carrier Sense Multiple Access with Collision Detection) is not used in wireless LANs because it is difficult to detect collisions due to the hidden node problem and the nature of wireless signal propagation.

**c) ARP Packet Size:**
- **Explanation:** The size of the ARP (Address Resolution Protocol) packet is not fixed. It varies depending on the hardware and protocol address sizes. Typically, it includes fields like hardware type, protocol type, hardware length, protocol length, operation code, sender hardware address, sender protocol address, target hardware address, and target protocol address.

### 6. Encoding and Bit Rate

**a) Differential Manchester Encoding:**
- **Bit Pattern:** 010011010
  - Differential Manchester encoding encodes each bit as a transition, with the specifics depending on the previous bit and the current bit to be encoded. 

**b) Bit Rate Calculation:**
- **Given:** Bandwidth = 1 MHz, SNR = 63.
- **Shannon Capacity Formula:** 
  \[
  \text{Capacity} = B \log_2(1 + \text{SNR}) = 1 \times 10^6 \log_2(1 + 63) = 1 \times 10^6 \log_2(64) = 1 \times 10^6 \times 6 = 6 \text{ Mbps}
  \]

### 7. CRC Calculation

**CRC Algorithm:**
- **Bit Stream:** 11010111
- **Generator Polynomial:** \( x^3 + x^2 + 1 \) (which is 1101 in binary)
- **Steps:** Append 3 zeros (since the degree of the polynomial is 3) to the bit stream, perform binary division, and calculate the remainder. This remainder is the CRC checksum. The transmitted frame includes the original bit stream followed by the checksum.

### 8. Channel Capacity and Network Comparison

**a) Channel Capacity Calculation:**
- **Bandwidth:** 300-3300 Hz
- **SNR:** 3162
- **Shannon Capacity Formula:**
  \[
  \text{Capacity} = B \log_2(1 + \text{SNR}) = 3000 \log_2(1 + 3162) \approx 3000 \log_2(3163) \approx 3000 \times 11.62 \approx 34860 \text{ bps}
  \]

**b) Virtual Circuit Network vs. Datagram Network:**
- **Virtual Circuit Network:** Establishes a fixed path before data transfer, maintains a connection state, and ensures ordered delivery.
- **Datagram Network:** Each packet is treated independently, routes dynamically, and does not guarantee order or connection state.

### 9. Sliding Window Protocol

**a) Sliding Window Protocol Scenario:**
- **Window Size:** 15
- **Packets Sent:** 0 to 11
- **NAK Received for Packet 6:** Indicates packet 6 was not received correctly. The window would slide to allow the sender to retransmit packet 6 while acknowledging the correctly received packets.

**b) Selective-Repeat ARQ:**
- **Correctness:** It is incorrect. In Selective-Repeat ARQ, the sender window size should be ≤ \( 2^m \) to avoid ambiguity in acknowledgments and ensure proper operation.

### 10. Go-Back-N ARQ

**Explanation:**
- **Lost Frame:** If a frame is lost, the sender retransmits all frames starting from the lost frame upon timeout.
- **Delayed Acknowledgements:** The sender continues to send frames until the window is exhausted, then retransmits starting from the last unacknowledged frame.
- **Lost Acknowledgements:** The sender will retransmit the frame upon timeout.

### 11. Network Layer Services

**a) Connection-Oriented vs. Connectionless Services:**
- **Connection-Oriented:** Establishes a dedicated connection before data transfer (e.g., TCP).
- **Connectionless:** Sends data without establishing a connection, with each packet treated independently (e.g., UDP).

**b) TCP/IP Reference Model:**
- **Description:** A conceptual framework for communications protocols used on the Internet, consisting of layers: Application, Transport, Internet, and Link.

### 12. Firewalls

**a) Definition:**
- **Firewall:** A network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules.

**b) Security Resolution:**
- **Explanation:** Firewalls filter traffic, prevent unauthorized access, block malicious data, and monitor network activity. They can also enforce security policies and act as a barrier between trusted and untrusted networks.

### 13. Stop and Wait Protocol

**a) Channel Utilization Calculation:**
- **Propagation Delay:** 20 ms
- **Frame Size:** 160 bits
- **Bandwidth:** 4 kbps
- **Channel Utilization:**
  \[
  \text{Utilization} = \frac{\text{Transmission Time}}{\text{Transmission Time} + 2 \times \text{Propagation Delay}}
  \]
  - Transmission Time = \(\frac{160 \text{ bits}}{4000 \text{ bits/second}} = 0.04 \text{ seconds}\)
  - Utilization = \(\frac{0.04}{0.04 + 0.04} = 0.5 = 50\% \)

**b) Bit Stuffing and Byte Stuffing:**
- **Bit Stuffing:** Inserting non-information bits into data to break up bit patterns that might be mistaken for

 control signals.
- **Byte Stuffing:** Inserting escape characters into data to differentiate data from control information.

### 14. Selective-Repeat ARQ

**a) Lost Frame Handling:**
- **Explanation:** If a frame is lost, the sender retransmits only the lost frame instead of all frames from the lost frame onward.

**b) Window Size in Go-Back-N ARQ:**
- **Justification:** The window size should be < \( 2^m \) (where m is the number of bits for the sequence number) to prevent ambiguity in the acknowledgment of frames.

### 15. Addressing

**a) Classful Addressing:**
- **Definition:** A method of IP addressing that divides the address space into fixed-size classes (A, B, C, D, E).
- **Advantages of Classless Addressing:** More efficient allocation of IP addresses, reduced wastage, and support for Variable Length Subnet Masking (VLSM).

### 16. Private Address and NAT

**a) Private Address:**
- **Definition:** IP addresses not routable on the public Internet, used within private networks (e.g., 192.168.x.x, 10.x.x.x).

**b) NAT (Network Address Translation):**
- **Definition:** A method that allows multiple devices on a local network to share a single public IP address for accessing the Internet, providing security and conserving IP addresses.

### 17. DNS System

**a) Need for DNS:**
- **Explanation:** DNS translates human-readable domain names into IP addresses, facilitating easier access to websites and resources on the Internet.

**b) Inverse Domain:**
- **Definition:** Part of the DNS used to map IP addresses back to host names, typically for network troubleshooting and logging.

### 18. TCP vs. UDP

**Comparison:**
- **TCP:** Provides reliable, ordered, and error-checked delivery of a stream of data between applications. Suitable for applications requiring high reliability.
- **UDP:** Provides a simpler, connectionless communication model with no guarantee of delivery, order, or error checking. Suitable for applications needing fast, efficient transmission (e.g., streaming).

### 19. Leaky Bucket vs. Token Bucket

**Comparison:**
- **Leaky Bucket Algorithm:** Controls data transmission rate by sending data at a constant rate, smoothing out bursts but potentially leading to data loss.
- **Token Bucket Algorithm:** Allows burstiness by accumulating tokens in a bucket. Data can be sent as long as there are enough tokens, providing flexibility and better utilization of available bandwidth.

### 20. Quality of Service (QoS)

**Description:**
- **Definition:** QoS refers to the performance level of a service, particularly in terms of bandwidth, latency, jitter, and error rate. It ensures that critical applications receive the necessary network resources and prioritizes traffic to meet specific performance requirements.
- **Key Components:** Traffic shaping, priority queuing, bandwidth management, and resource reservation.