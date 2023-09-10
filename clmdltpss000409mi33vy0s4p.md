---
title: "TCP/IP Shortcuts for beginners"
datePublished: Sun Sep 10 2023 15:22:56 GMT+0000 (Coordinated Universal Time)
cuid: clmdltpss000409mi33vy0s4p
slug: tcpip-shortcuts-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694358127817/c22d0a0d-0198-4e5a-8e98-3d89313f49b0.png
tags: osi, protocols, data-communication, tcpip-model, ppp

---

# Data Communication

Data communication means the exchange of information between two or more devices using some transmission medium.

* **Effectiveness of Data Communication Layer: (DATJ)**
    
    1. Delivery, 2. Accuracy, 3. Timeliness, 4. Jitter
        
* **Components of Data Communication**
    
    1. Message, 2. Sender, 3. Receiver, 4. Transmission Medium, 5. Protocol
        
* **Data Representation**
    
    1. Text, 2. Number, 3. Images, 4. Audios, 5. Videos
        
* **Data Flow**
    
    1. Simplex, 2. Half Duplex, 3. Full Duplex
        
* **Network Criteria (PRS)**
    
    1. Performance →
        
        a. Throughput
        
        The throughput is a measure of how fast we can actually send data through a network
        
        **Unit: bps**
        
        b. Latency
        
        The latency or delay defines how long it takes for an entire message to completely arrive at the destination from the time the first bit is sent out from the source.
        
        **Latency = propagation time + transmission time + queuing time + processing delay**
        
        **Unit: second**
        
    2. Reliability,
        
    3. Security
        

What is a network? Interconnection between devices

Network components → 1. Host, 2. Connecting Devices ( Router, Switch, Modem)

Router → Network to Network Connection

Switch → Device to Device Connection

Modem → Data form exchange

Types of Connections → 1. Wired, 2. Wireless

Wired Connection → 1. Point to Point, 2. Multi-point

Topologies → 1. Bus, 2. Ring, 3. Mesh, 4. Star

* **Accessing the Internet**
    
    1. Using Telephone → Dial-up and DSL
        
    2. Using Wireless Network → point-to-point WAN
        
    3. Using Cable Network → Through Cable
        
    4. Direct Connect to the Internet → ISP
        

Switches →

1. Circuit Switched Network
    
2. Packed Switched Network
    

**Two popular Data Communication Models:**

1. OSI → 1. Application, 2. Presentation, 3. Session, 4. Transport, 5. Network, 6. Data-link, 7. Physical
    
2. TCP/IP → 1. Application, 2. Transport, 3. Network, 4. Data-link, 5. Physical
    

**Two principles for all protocols:**

1. First principle: Each layer needs to work on two opposite tasks.
    
2. Second principle: Each layer must be identical between the source and destination
    

**Addressing each layer of TCP/IP:**

| Packet | Layers | Address |
| --- | --- | --- |
| Message | Application | Name |
| Segment/ User Datagram | Transport | Port Number |
| Datagram | Network | Logical Address |
| Frame | Data-link | Data-link Address |
| Bits | Physical | \- |

**Lacks of OSI Model Success:**

1. To replace the infrastructure from TCP/IP to OSI model, it needs a lot of time and money,
    
2. Services are not fully described in the presentation and session layer of the OSI model and
    
3. Performances are not high enough to attract ISOC to switch TCP/IP to the OSI model.
    

**There are 4 signals:**

1. Periodic Analog Signal,
    
2. Non-periodic Analog Signal,
    
3. Periodic Digital Signal
    
4. Non-periodic Digital Signal
    

**Signal Basics:**

Bandwidth: The bandwidth of a composite signal is the difference between the highest and the lowest frequencies contained in that signal. **Unit: Hz**.

$$B = F_h - F_l$$

Bit Rate: The number of bits transferred per second is called bitrate. Unit: **bps**

$$number \space of \space bits = log_2 (bit \space level)$$

**Bit length = propagation speed \* bit duration**

The non-periodic digital signal can be converted to as non-periodic analog signal.

**Transmission of Digital Signal**

1. Baseband:
    
    Baseband transmission means transferring ***digital signal to digital signal*** using a ***low-pass*** channel.
    
    ![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F155d0b75-e884-40e6-a538-1ccf97929d38%2FUntitled.png?table=block&id=17cd6084-69c8-41d8-be57-48a22c4dbe4d&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")
    
    Case 1. Low Pass Channel with Wide Bandwidth
    
    Case 2. Low Pass Channel with Limited Bandwidth,
    
2. Broadband:
    
    Broadband transmission means converting ***digital signal to analog signal*** in the sending end using ***modulation,*** and in the receiving end, it converts ***analog signal to digital signal*** through the ***band-pass channel.***
    
    ![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F7f7dce2a-0b70-4dd7-9a17-ffe4fd6754bd%2FUntitled.png?table=block&id=28bb390f-c6b3-4ca2-b5c0-f67aa1163a55&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")
    

**Transmission Impairment:**

1. Attenuation (loss of energy),
    
    loss of power (unit: dB)
    

$$10log_{10}\frac{p_2}{p_1}$$

1. Distortion (Changes in shape)
    
2. Noise
    
    Type of Noises:
    
    1. thermal: the random motion of electrons in a wire, which creates an extra signal.
        
    2. Induced: comes from sources such as motors and appliances.
        
    3. Crosstalk: the effect of one wire on the other
        
    4. Impulse: a spike (a signal with high energy in a very short time) that comes from power lines or lightning.
        

**Signal-to-Noise Ratio (SNR):**

to find the theoretical bit rate limit, we need to know the ratio of the signal power to the noise power. The signal-to-noise ratio is defined as,

$$SNR = \frac{average\space signal \space power}{average \space noise \space power}$$

A high SNR means the signal is less corrupted by noise; a low SNR means the signal is more corrupted by noise. Because SNR is the ratio of two powers, it is often described in decibel units,

$$SNR_{dB} = 10 log_{10}\frac{average\space signal \space power}{average \space noise \space power} = 10 log_{10}(SNR)$$

**Data Rate Limits:**

A very important consideration in data communications is how fast we can send data, in bits per second, over a channel. The data rate depends on three factors:

1. The bandwidth available
    
2. The level of the signals we use
    
3. The quality of the channel (the level of noise)
    

Two theoretical formulas were developed to calculate the data rate: one by Nyquist for a noiseless channel, and another by Shannon for a noisy channel.

Noiseless Channel: Nyquist Bit Rate

$$bitrate = 2 \times bandwidth \times bit \space length = 2 \times bandwidth \times log_2(Level)$$

Noisy Channel: Shannon Capacity

$$Capacity = bandwidth \times log_2(1 + SNR)$$

capacity is the capacity of the channel in bits per second

**Note: The Shannon capacity gives us the upper limit; the Nyquist formula tells us how many signal levels we need.**

Equations:

1. **Transmission time = (Message size) / Bandwidth**
    
2. **The bandwidth-delay product defines the number of bits that can fill the link**
    

### **Digital Signal Conversion**

Characteristics of Digital Signal Conversion:

1. **Baseline wandering** refers to the slow, low-frequency variations or shifts in the baseline or the zero-level reference of a signal.
    
2. When the voltage level in a digital signal is constant for a while, the spectrum creates very low frequencies which creates **DC Components** problem.
    
3. **Self-synchronization** refers to the sync between the receiver’s bits interval and the sender’s bits interval.
    
4. **Built-in error-detecting** capability in the generated code to detect some or all of the errors that occurred during transmission.
    
5. **Immunity to Noise and Interference**
    
6. **Complexity:** A more complex Scheme is costly.
    

**Digital to Digital Data Encoding:**

$$r = \frac {data\space element}{signal \space element} = \frac{data \space rate}{ signal \space rate} = \frac{N}{S}$$

![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2Fa70ea2fb-f261-49ed-9719-196debb6f02e%2FUntitled.png?table=block&id=ea208083-5e25-432e-9b47-92c209d85a77&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")

Three types of encoding schemes:

1. Line encoding:
    
    1. Unipolar: (0, + v / - v)
        
        1. NRZ:
            
            bit 1 = + v bit 0 = 0
            
    2. Polar: (+ v, - v )
        
        1. NRZ-L:
            
            bit 1 = - v
            
            bit 0 = + v
            
        2. NRZ-I:
            
            bit 1 = change
            
            bit 0 = no change
            
        3. Biphase:
            
            1. Manchester:
                
                bit 1 = - v to + v
                
                bit 0 = + v to - v
                
            2. Differential Manchester:
                
                bit 1 = no transition = no inversion
                
                bit 0 = transition = inversion
                
    3. Bipolar:
        
        1. AMI:
            
            bit 1 = transition
            
            bit 0 = 0
            
        2. Pseudo-ternary:
            
            bit 1 = 0
            
            bit 0 = transition
            
    4. Multilevel:
        
        1. 2B1Q:
            
            | level | +ve | \-ve |
            | --- | --- | --- |
            | 00 | +1 | \-1 |
            | 01 | +3 | \-3 |
            | 10 | \-1 | +1 |
            | 11 | \-3 | +3 |
            
    5. Multitransition:
        
        1. MLT-3
            
            bit 1 = opposite of last non-zero if the current level is zero 0 if the current level is non-zero
            
            bit 0 = no transition
            
    
    **Bandwidth Table:**
    
    | Line encoding name | Bandwidth |
    | --- | --- |
    | Unipolar NRZ, Polar NRZ, Polar RZ, AMI, Pseudo-ternary | N/2 |
    | Polar Biphase (Manchester, Diffential Manchester) | N |
    | 2B1Q | N/4 |
    | 8B6Q | 3 N/4 |
    | 4D-PAM5 | N/8 |
    | MLT-3 | N/3 |
    
2. Block encoding: mBnB
    
    1. 4B/5B, b. 8B/10B
        
3. Scrambling:
    
    1. B8ZS: (Bipolar with 8 zeros Substuition)
        
        0000 0000 = 000VB0VB V = last non-zero level
        
        B = opposite of the last non-zero level
        
    2. HDB3: (High Density Bi-polar 3 Zeros)
        
        0000 = 000V (odd numbers of last non-zeros)
        
        0000 = B00V (even numbers of last non-zeros)
        

**Analog to Digital Conversion:**

1. PCM: (Pulse Code Modulation)
    
    1. Sampling by Nyquist theorem
        
    2. Quantizing : Delta = (V\_max - V\_min) / L
        
    3. Encoding
        
2. DM: (Delta Modulation)
    
    1. Modulator,
        
    2. Demodulator,
        
    3. Adaptive DM
        
    4. Quantizing Error
        

**Digital** **Transmission Mode:**

1. Serial:
    
    1. Asynchronous, (stop bit, start bit)
        
    2. Synchronous (sender and receiver’s clock time = same)
        
    3. Isochronous (video and audio real-time data)
        
2. Parallel
    

### Analog Signal Transmission

Digital to Analog: (Digital Signal + Carrier Signal = Modulated Signal)

1. ASK
    
    0 = 0 amplitude
    
    level = 2 (BASK)
    
    r = Log( Level)
    
    B = (1 + d) *S = (1 +d )* N/ r
    
2. PSK
    
    0 = 180 phase
    
    level = 2 (BPSK)
    
    r = Log( Level)
    
    B = (1 + d) *S = (1 +d )* N/ r
    
3. FSK
    
    1 = Frequency Increased
    
    B = ( 1 + d) \* S + 2F
    
4. QAM (ASK + PSK)
    
    Use constellation diagram
    
    example: 4 QAM, 16 QAM, 64 QAM
    

Analog to Analog: (Modulating Analog Signal + Carrier Signal = Modulated Signal)

1. AM
    
2. FM
    
3. PM
    

### **Bandwidth Utilization**

There are 3 multiplexing techniques to utilize the bandwidth:

1. FDM (Analog Signal)
    
    Frequency Division Multiplexing: Create a composite signal of broad frequencies from input signals. Guard bands are strips of unused bandwidth. In Frequency-division multiplexing (FDM), Channels can be separated by guard bands to prevent signals from overlapping.
    
2. WDM (Optical Signal)
    
    Wavelength Division Multiplexing: Create a multiple wavelength signal from input-specific wavelength signals. We use prism for WDM.
    
3. TDM (Digital Signal)
    
    1. Synchronous:
        
        1. The frame is a combination of time slots. In a frame, number of time slots is the number of input lines.
            
        2. Frame rate = input data rate
            
        3. Frame duration = 1 / Frame rate
            
        4. bitrate = number of input lines \* frame rate
            
        5. To fill empty slots:
            
            1. Multilevel Multiplexing (100 + 100 → 200)
                
            2. Multi-slot multiplexing (200 → 100 + 100)
                
            3. Pulse stuffing ( 190 + 10 → 200)
                
        6. It uses framing bit as 0 or 1 for synchronization
            
        7. Interleaving: TDM can be visualized as two fast-rotating switches, one on the multiplexing side and the other on the demultiplexing side. On the multiplexing side, as the switch opens in front of a connection, that connection has the opportunity to send a unit onto the path. This process is called interleaving
            
    2. Statistical:
        
        1. It uses no-synchronization
            
        2. It only takes slots that are filled and inserts an address beside the time slot to identify which slot it is referred to.
            
        3. In peak time, data lines need to wait for overhead bits.
            

**Spectrum Spreading for Preventing Interference and Spying:**

1. FHSS (Frequency Hopping Spread Spectrum)
    
    It uses a hopping sequence to hop frequencies for transfering data in runtime.
    
    Hopping sequence: 100, 400, 300, 200
    
    Data: 100, 010, 011, 101
    
    | 400 MHz |  | 010 |  |  |
    | --- | --- | --- | --- | --- |
    | 300 MHz |  |  | 011 |  |
    | 200 MHz |  |  |  | 101 |
    | 100 MHz | 100 |  |  |  |
    | 0 MHz | 1 Time Unit | 2 Time Unit | 3 Time Unit | 4 Time Unit |
    
2. DSSS (Direct Sequence Spread Spectrum)
    
    The signal encoding scheme is Polar NRZ-L. ( bit 1 = -v, Bit 0 = +v)
    
    Sending data: 101
    
    Spreading code: 1011
    
    Spread code: 1011 0100 1011
    

### Transmission Media

1. Guided Media
    
    1. Twisted pair:
        
        1. Ground and Signal
            
        2. Plastic Cover + Core = UTP, Plastic Cover + Metal + Core = STP
            
        3. Connected by RJ45
            
    2. Co-axial:
        
        1. Outer Layer + Insulator + Outer Conductor + Insulator + Inner Conductor
            
        2. Connected by BNC
            
    3. Optical Fibre:
        
        1. Outer Layer + Dupont Kevlar + Plastic Buffer + Cladding + Core
            
        2. ST or SC Connector
            
        3. Mode:
            
            ![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2Ff41085ff-7992-4315-bda0-b18a0ec195f1%2FUntitled.png?table=block&id=d294867e-e3c5-4e6e-ba28-12b65afe146e&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")
            
            1. Multimode:
                
                1. Step index:
                    
                    1. The density of the core is constant
                        
                    2. Cladding and core are made of the same material
                        
                2. Graded index:
                    
                    1. The density of the center of the core is higher and decreases gradually to its lowest at the edge.
                        
                    2. Cladding and core are not made of the same material
                        
            2. Single mode:
                
                1. The critical angle is almost up to 90
                    
                2. The propagation of the beam is almost horizontal
                    
    
    Unguided Media:
    
    1. Radiowave: (3 KHz - 1 GHz)
        
    2. Microwave: (1 GHz - 300 GHz)
        
    3. Infrared: (300 GHz - 400 THz)
        
    
    Propagation of Radiowave:
    
    1. Ground propagation:
        
        1. It used a very low-frequency band
            
        2. propagates below the lower point of the atmosphere
            
        3. distance depends on the power of the signal
            
    2. Sky propagation:
        
        1. Works by reflecting in the ionosphere
            
        2. Greater distance traveled by lower output data
            
        3. Band: High, very high-frequency band
            
    3. Line of sight:
        
        1. Antenna-to-antenna data transfer
            
        2. Band: UHF, EHF
            
        3. Used in satellite
            
    
    Antenna:
    
    1. Omnidirectional Antenna:
        
        1. One sender to many receivers
            
        2. Used by radio wave
            
    2. Unidirectional / Parabolic Antenna:
        
        1. Send only to one direction
            
        2. Used by microwave signal
            
    
    Infrared:
    
    1. Line of sight propagation
        
    2. No Antenna needed
        
    3. Used for shorter distance
        
    
    ### Introduction to Data-link Layer
    
    Packet: frame, Address: link-layer address
    
    Connection between: node
    
    Nodes are connected with links. Links are 2 types:
    
    1. point to point link (DLC sublayer)
        
    2. broadcast link (MAC and DLC sublayers)
        
    
    Services of Data-link layer:
    
    1. Framing
        
    2. Flow Control (Produced Frames &gt; Consumed Frames)
        
    3. Error Control
        
    4. Congestion Control
        
    
    Link layer Addressing: (48 bits / 6 bytes / 12 hexadecimal digits)
    
    1. Unicast:
        
        Address: 23:53:29:61:07:F1
        
    2. Multicast:
        
        Address: 24:54:28:62:08:F2
        
    3. Broadcast:
        
        Address: FF:FF:FF:FF:FF:FF
        
    
    ARP (Address Resolution Protocol):
    
    ARP accepts an IP Address from Internet Protocol and maps the address to the link-layer address in the data-link layer.
    
    ARP Packet format:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694359121436/50888257-290e-412e-85b4-c0aeb4be334e.png align="center")
    
    ARP Caching:
    
    Broadcast Link → Store Destination’s link-layer address → Unicast Link
    
    ### Types of error
    
    1\. single error, 2. burst error
    
    Burst length = length (position of first error, position, last error)
    
    There are 2 types of block coding:
    
    1\. Dataword, 2. Codeword
    
    The hamming distance can be solved by XORing a two-bit string
    
    Minimum Hamming distance = s + 1 where s = number of errors that can be solved.
    
    **CRC and Polynomials:**
    
    ![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F0a31210b-807b-41c0-806b-058eb96a1f09%2FScreenshot_2023-09-10_at_12.25.44_PM.png?table=block&id=b809cb0c-b803-4c8b-8b43-56f5ca79cc07&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")
    
    **Checksum**:
    
    ![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F3fe48459-2a50-4a95-ab27-4b8625371b94%2FUntitled.png?table=block&id=a9f8c9ff-7fa8-4275-a928-1bf92fafcac3&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")
    
    Forward Error Correction Methods:
    
    1. Hamming Distance
        
    2. XOR
        
    3. Chunk interleaving
        
    4. Chunk interleaving with Hamming Distance
        
    5. Compounding high and low-resolution packet
        

**Note: CRC is better than Checksum in correcting errors.**

### DLC (Data link Control) Protocols

Framing: 1. Bit oriented, 2. Character Oriented (byte-oriented)

Byte stuffing: When data has a flag-like byte, we add an ESC byte before it so that the receiver doesn’t end the frame while reading user information. It is used in Character oriented framing

Bit stuffing: The flag is 01111110; while reading user information, it replaces 01111110 with 011111010

Buffer: A buffer is a set of memory locations that can hold packets at the sender and receiver. When the buffer of the receiving data-link layer is full, it informs the sending data-link layer to stop pushing frames. It is used in flow control.

Error Control: This service is provided by a 2-4 byte CRC added to the frame header.

Services: 1. Framing, 2. Flow control, 3. Error Control

DLC protocols can be:

1. Connectionless oriented: Frames are unnumbered
    
2. Connection-oriented: Frames are unnumbered
    

Simple protocol:

![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F82cb0d89-c839-457e-b201-842c38858049%2FUntitled.png?table=block&id=c89086b0-99b0-45e0-8476-00513eedeef3&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")

Stop and wait Protocol:

Flow control is provided by sequence number (0,1,0,1,..) and acknowledge number (1,0,1,0,..)

Two states:

1. Ready State:
    
    1. Waiting for the packet from the network layer
        
    2. The sender creates a frame and sends it.
        
    3. The sender saves a copy of the frame
        

Blocking state:

1. If a timeout occurs, the sender resends the frame
    
2. If ACK is corrupted, the frame is discarded
    
3. else receiver sends error-free ACK to receive the next frame
    

![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F4b06dfb8-acd7-41b4-919a-9de5973dd7c7%2FUntitled.png?table=block&id=ad072c09-1ea3-4331-9d95-d38b3a1af3d1&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")

Piggybacking:

Bi-directional protocol that is sophisticated and costly. The sender and receiver both can send signals and acknowledgment.

HDLC (High-Level Data Link Control Protocol):

Characteristics: 1. Bit oriented, 2. More theoretical than practical, 3. Use Stop and Wait Protocol, 4. Use point-to-point or multi-point links.

Transfer modes:

![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F6a3332d8-f4f2-4927-a939-6bfb43f90300%2FUntitled.png?table=block&id=628dc5e1-f962-41b9-83bc-ac8db244439a&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")

1. NRM (Normal Response Mode): (Point to point / Multi-point, Unbalanced, 1 Primary Station → Multi Secondary Stations)
    
2. ABM (Asynchronous Balanced Mode) (Point to point, Balance)
    

**Framing of HDLC**

Information Frame: (Used for transferring data)

| Flag | Address | Control | User Information | FCS | Flag |
| --- | --- | --- | --- | --- | --- |

Supervisory Frame: (Used for Flow and Error Control)

ACKs: RR (Receive Ready), RNR (Receive Not Ready), REJ (Reject), SREJ (Selective Reject)

| Flag | Address | Control | FCS | Flag |
| --- | --- | --- | --- | --- |

Unnumbered Frame: (Used for connection establishment and release)

| Flag | Address | Control | Management Information | FCS | Flag |
| --- | --- | --- | --- | --- | --- |

**PPP (Point-to-Point Protocol)**

Services: 1. Most used protocol, 2. Provide Authentication and network configuration, 3. Error Control.

PPP doesn’t provide flow control.

PPP Framing:

| Flag | Address | Control | Protocol | Payload | FCS | Flag |
| --- | --- | --- | --- | --- | --- | --- |
| 01111110 | 11111111 | 00000011 | 1-2 bytes | Variable-sized | 2-4 byte CRC | 01111110 |

PPP has created two protocols for authentication: **PAP** (Password Authentication Protocol) and **CHAP** (Challenge Handshake Authentication Protocol). Internet Protocol Control Protocol (**IPCP**) is framed inside PPP framing for carrying IP data packets.

Transition phase of PPP:

![](https://anwholesquare.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2Fb6067351-1921-4756-90ef-19d0061185e8%2F0b034b54-0b19-45ea-a836-d3f25b24a8cc%2FUntitled.png?table=block&id=fd0deec0-8008-42b6-86ea-c9420fb995e4&spaceId=b6067351-1921-4756-90ef-19d0061185e8&width=2000&userId=&cache=v2 align="left")

### MAC Protocols (Media Access Control)

1. Random Access Protocol:
    
    1. ALOHA (Advocates of Linux Open-source Hawaii Association): Radio LAN
        
    2. CSMA ( Carrier Sense Multiple Access): Ethernet
        
    3. CSMA / CD (Carrier Sense Multiple Access with Collision Detection): Traditional Ethernet of 10 Mbps data rate
        
    4. CSMA / CA (Carrier Sense Multiple Access with Collision Avoidance): Wireless Network
        
2. Control Access Protocol:
    
    1. Reservation: Device needs reservation before sending data
        
    2. Polling: One device is the primary station, and others are the secondary station
        
    3. Token Passing: Networks are organized in a logical ring, and all stations are either predecessors or successors.
        
3. Channelization:
    
    1. FDMA (Frequency Division Multiple Access): The bandwidth of the common channel is divided into bands that are separated by guard bands.
        
    2. TDMA (Time Division Multiple Access): Stations share timeslots.
        
    3. CDMA (Code Division Multiple Access): All data are sent by one channel with different codes.
        

Abbreviations:

1. ARPANET: Advanced Research Projects Agency Network
    
2. TCP: Transmission Control Protocol
    
3. IP: Internet Protocol
    
4. ISOC: Internet Society
    
5. IAB: Internet Architecture Board
    
6. ASCII: American Standard Code for Information Interchange
    
7. ISO: Internation Organization for Standardization
    
8. OSI: Open Systems Interconnection