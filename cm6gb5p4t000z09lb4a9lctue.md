---
title: "TCP 3-Way Handshake"
seoTitle: "TCP 3-Way Handshake"
seoDescription: "TCP Protocol 3 way Handshake Communication, TCP Header"
datePublished: Tue Jan 28 2025 10:01:44 GMT+0000 (Coordinated Universal Time)
cuid: cm6gb5p4t000z09lb4a9lctue
slug: tcp-3-way-handshake
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738052939113/54662de0-86ea-4b6b-a0c8-ebb80ee59fe2.png
tags: 2articles1week, web-basic, chaicode, jargoniseasy, webkmsyed

---

# **Introduction**

When you send a message over the internet, whether it's a simple text or a critical transaction, the process involves more than just pressing 'send.' Behind the scenes, an intricate process ensures the reliable delivery of your data. This process starts with something called the **TCP 3-way handshake** — a foundational mechanism that sets the stage for communication between devices.

Think of it as introducing yourself before a conversation. Just as you wouldn't jump into a serious discussion without saying, "Hi," computers first exchange a series of signals to ensure they're on the same page. The TCP 3-way handshake achieves this, establishing trust and confirming readiness between devices before they exchange data. In this article, we'll break down this process in simple, human terms while diving into its technical brilliance.
<br>
<br>
# **What Is TCP and Why Does It Matter?**

Before diving into the handshake, let’s briefly talk about TCP itself. The **Transmission Control Protocol (TCP)** is one of the core protocols in the TCP/IP suite that powers the internet. Its primary role is to ensure **reliable communication** between devices by breaking data into packets, transmitting them, and ensuring they're reassembled in the correct order.

* **Key Features of TCP:**
    
    * Connection-oriented protocol (requires a session to be established).
        
    * Ensures data integrity (no missing or duplicate packets).
        
    * Implements error-checking and flow control.
        

From browsing websites to streaming videos or gaming, TCP ensures your experience remains smooth and reliable. But none of this is possible without the 3-way handshake. Let’s explore how it works.

# **TCP Header Format**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738057763831/afa64208-4b1a-4270-af10-bd3e759ec4be.png align="center")

## **Key Fields in the TCP Header**

### **1\. Source Port and Destination Port**

* **Purpose:** These 16-bit fields identify the application or process on the source and destination devices.
    
* **Example:** When accessing a website, the source port is randomly chosen, while the destination port is usually **80 (HTTP)** or **443 (HTTPS)**.
    

### **2\. Sequence Number**

* **Purpose:** A unique 32-bit number assigned to each byte in the data stream to ensure ordered delivery.
    
* **Example:** The sequence number helps reassemble packets in the correct order even if they arrive out of sequence.
    

### **3\. Acknowledgment Number**

* **Purpose:** A 32-bit number used to confirm receipt of data. It specifies the next byte the receiver expects.
    
* **Example:** If a sender transmits bytes 1-100, the acknowledgment number will be **101**, indicating the receiver successfully got all bytes up to 100.
    

### **4\. Data Offset (Header Length)**

* **Purpose:** Indicates the size of the TCP header (in 32-bit words) and where the actual data (payload) starts.
    
* **Importance:** Ensures the receiver knows where to look for the application data.
    

### **5\. Reserved**

* **Purpose:** Reserved for future use and currently set to **0**.
    

### **6\. Flags (Control Bits)**

* **Purpose:** A set of 6 bits that control various TCP operations, such as connection establishment or termination.
    
    * **SYN:** Starts a connection.
        
    * **ACK:** Acknowledges received data.
        
    * **FIN:** Ends a connection.
        
    * **RST:** Resets a connection.
        
    * **PSH:** Pushes data immediately to the receiver.
        
    * **URG:** Indicates urgent data.
        

### **7\. Window Size**

* **Purpose:** A 16-bit field that specifies how much data (in bytes) the receiver can accept without acknowledgment.
    
* **Importance:** Plays a key role in **flow control**.
    

### **8\. Checksum**

* **Purpose:** Used for error-checking the header and data. Ensures the data isn’t corrupted during transmission.
    

### **9\. Urgent Pointer**

* **Purpose:** Points to urgent data within the segment, used with the **URG flag**.
    

### **10\. Options (If Any)**

* **Purpose:** Optional field used for extensions like **maximum segment size (MSS)** or **timestamps**.
    
* **Example:** The MSS option limits the maximum data size per packet.
    

### **11\. Data (Payload)**

* **Purpose:** The actual information being transmitted (e.g., web page content, email data, etc.).
    

This header format ensures reliable data transmission by organizing and validating the data as it travels between devices. It is the backbone of TCP's reliability and ordered communication.

# **Understanding the 3-Way Handshake**

![TCP 3 Way Handshake](https://cdn.hashnode.com/res/hashnode/image/upload/v1738057424642/81e5943e-b696-4e56-984d-ac74b80e47b9.png align="center")

The **TCP 3-way handshake** is a three-step process that establishes a connection between a client and a server. It ensures both parties are ready to communicate and agree on essential parameters like sequence numbers. The steps are:

1. **SYN (Synchronize):**
    
    * The client sends a synchronization request (SYN) to the server. This is like the client saying, "I want to connect. Are you available?"
        
    * The SYN packet includes an initial sequence number (ISN), which helps organize data later.
        
2. **SYN-ACK (Synchronization Acknowledgment):**
    
    * The server responds with a SYN-ACK packet, confirming it received the client’s request and is ready to communicate. It also sends its own ISN.
        
    * This is like the server replying, "I’m here. Let’s proceed."
        
3. **ACK (Acknowledgment):**
    
    * Finally, the client sends an ACK packet back to the server, confirming that the connection parameters are accepted.
        
    * This step completes the handshake, and the connection is officially established.
        

Now both devices can start exchanging data.

## **Why Use Three Steps?**

At first glance, the 3-way handshake might seem excessive. Why not just send a single confirmation? The answer lies in reliability. The handshake ensures:

* **Mutual Agreement:** Both devices confirm they're ready to communicate.
    
* **Synchronization of Sequence Numbers:** Sequence numbers prevent data from being misplaced or duplicated.
    
* **Error Checking:** Any issues during the handshake are identified and resolved before data transfer begins.
    

By taking these steps, TCP eliminates the risk of unreliable communication, especially over complex networks.

## **Breaking Down the Handshake with an Example**

Let’s visualize the handshake in a real-world scenario: accessing a website.

* **Step 1: SYN**
    
    * You (the client) open your browser and type in a URL (e.g., [www.example.com](http://www.example.com/)). Your device sends a SYN packet to the web server hosting the website.
        
    * Think of it as knocking on the server’s door and saying, "Hello, I’d like to connect."
        
* **Step 2: SYN-ACK**
    
    * The server responds with a SYN-ACK packet, saying, "Sure, I’m here and ready to talk. Let’s establish a connection."
        
* **Step 3: ACK**
    
    * Your device sends back an ACK, confirming that it’s ready to start the session. The server receives this acknowledgment and begins serving the webpage.
        

In just milliseconds, the 3-way handshake ensures that both you and the server are aligned for communication.

## **How the Handshake Works in Online Gaming (PUBG Example)**

In games like PUBG or Free Fire, where latency and reliability are crucial, the TCP handshake ensures smooth gameplay:

1. When you join a match, your game client sends a SYN packet to the game server, requesting a connection.
    
2. The game server responds with a SYN-ACK packet, signaling its readiness to receive data.
    
3. Your client then sends an ACK packet, and the connection is established.
    

This handshake ensures that every action, such as shooting or moving, is accurately transmitted to the server and reflected in the game.

### **What Happens When the Handshake Fails?**

If the TCP handshake doesn’t complete, the connection isn’t established. Some common reasons include:

* **Network Issues:** Packet loss or high latency can disrupt the handshake.
    

* **Firewall Restrictions:** Firewalls may block SYN or SYN-ACK packets.
    

* **Server Overload:** A server under heavy load might fail to respond.
    

For example, if you try to load a website but only the SYN packet is sent, your browser may show a "Connection Timed Out" error.

# **TCP Handshake vs. UDP Communication**

You might wonder how this differs from UDP (User Datagram Protocol). Unlike TCP, UDP skips the handshake process entirely. While this speeds up communication, it sacrifices reliability. For applications like video streaming or online gaming, TCP’s reliability is often more important than UDP’s speed.

|  | TCP | UDP |
| --- | --- | --- |
| Connection Setup | Requires 3-way handshake | Connectionless |
| Reliability | Ensures data integrity and delivery | No guarantees |
| Speed | Slower due to overhead | Faster |
| Use Cases | Web browsing, email, file transfer | Video streaming, DNS |

# **Conclusion**

The TCP 3-way handshake is more than just a technical process. It’s the foundation of reliable communication across the internet. From loading a website to playing your favorite game, this handshake ensures that data flows smoothly and accurately.

It starts with a simple "SYN" message, but behind it lies the magic of ensuring both devices are ready to communicate. This handshake isn’t just about data transfer; it’s about trust and ensuring the connection is stable before any information is exchanged.

Imagine sending a message to a friend. The handshake is like saying, "Are you there?" and waiting for them to respond, "Yes, I am. Are you ready to talk?" Only after both sides confirm readiness does the conversation begin.

Understanding this process gives you a deeper appreciation for the technology we often take for granted. It highlights the incredible engineering that keeps our digital world running smoothly. Every email, every game, and every video call relies on this.

The beauty of the 3-way handshake is in its simplicity and effectiveness. Even in moments when connections fail, the system ensures that no partial or corrupted data causes confusion. It’s a silent guardian of your online interactions.

So, the next time you stream a movie, send an email, or join an online game, remember the silent handshake working tirelessly to connect the dots and make it all possible. It’s a small but essential process that forms the backbone of modern communication.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Want to explore more fun jargon in the Web Basics series? Comment below, and we'll try to add it!</div>
</div>

%[https://jargoniseasy.hashnode.dev/series/web-basics] 

%[https://jargoniseasy.hashnode.dev/tcpip-basics] 

%[https://jargoniseasy.hashnode.dev/client-side-vs-server-side]