---
title: C - Glossary
version: 1.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 10/10
tags: [reference, glossary, terminology, definitions]
---

---

## Glossary of Terms

**Reference Guide for Non-Technical Users**

---

### A

**AODV (Ad hoc On-Demand Distance Vector)**  
Reactive routing protocol considered but not selected for this project. Babel was chosen instead due to better production history and faster convergence. AODV remains experimental (RFC 3561).

**Android**  
Operating system for most smartphones except iPhones. Based on Linux. Most affordable phones use Android, making it ideal for this project.

---

### B

**Babel (Routing Protocol)**  
Loop-avoiding distance-vector routing protocol (RFC 8966) designed for mesh networks. Uses link quality metrics (ETX) instead of hop count. Fast convergence (~5 seconds). Production-proven. Runs as babeld daemon on relay nodes.

**babeld**  
Software that implements Babel routing protocol. Runs on Raspberry Pi relay nodes to handle multi-hop routing. Lightweight, reliable, available in standard Linux repositories.

**Bandwidth**  
Amount of data transmitted over network in given time. Like water through a pipe - wider pipe (more bandwidth) = more data flow. Measured in Mbps (megabits per second).

**BLE (Bluetooth Low Energy)**  
Power-efficient Bluetooth for devices needing long battery life. Uses minimal power while constantly scanning for nearby devices. Perfect for mesh network discovery.

**Blockchain**  
Distributed digital ledger where transactions are recorded across many computers. No single person controls it. Used in this project for wallet identity and governance.

**Bridge Node**  
Special relay node with internet connectivity (usually satellite). Acts as gateway between local mesh and global internet/IPFS. Critical infrastructure requiring highest security.

---

### C

**Censorship-Resistant**  
Designed so no single authority can block or control communication. Achieved through decentralization - no central servers to shut down.

**Chunk / Chunking**  
Breaking large files into small pieces for transmission. Like cutting pizza into slices for easier carrying. Each 256KB chunk sent separately and reassembled at destination.

**Codec**  
Software that compresses/decompresses video/audio. H.265 makes video files smaller while maintaining quality. Essential for sending videos through mesh networks.

---

### D

**DAO (Decentralized Autonomous Organization)**  
Governance system where decisions are made by community voting, not central authority. Rules encoded in smart contracts and executed automatically.

**Decentralized**  
Distributed across many locations with no central control. Opposite of centralized (like Facebook). No single entity can shut down or control the network.

**Delay-Tolerant Networking**  
Network design accepting delays rather than requiring instant delivery. Messages stored and forwarded when connections available. Like leaving a note vs requiring phone answer.

**DHT (Distributed Hash Table)**  
Decentralized system for storing and finding data without central server. Like a phone book split up and stored by everyone. Used by BitTorrent and IPFS.

---

### E

**E2E Encryption (End-to-End Encryption)**  
Encryption where only sender and recipient can read messages. Not even relay nodes forwarding messages can decrypt content.

**Endorsement**  
Vouching for another user's trustworthiness. Multiple endorsements from trusted users build reputation and prove legitimacy.

**Ethereum**  
Blockchain platform supporting smart contracts. This project uses Ethereum Layer 2 (faster, cheaper versions) for wallet identity and governance.

**ETX (Expected Transmission Count)**  
Link quality metric used by Babel. Measures transmissions needed for successful packet delivery. Lower ETX = better link quality. Babel prefers reliable routes over shorter but lossy ones.

**EXIF Data**  
Metadata in photos - GPS location, date/time, camera model. This project strips EXIF before sharing to protect privacy.

---

### G

**Gas Fees**  
Small fees for processing blockchain transactions. Like postage stamps. This project uses Layer 2 networks where fees are very low ($0.01-0.05).

**Governance**  
System of rules and decision-making controlling network operation. In this decentralized system, governance is community-driven through voting, not controlled by company.

---

### H

**Hash / Hashing**  
Converting data into unique fixed-size string. Like a fingerprint - every file has unique hash. If file changes slightly, hash changes completely. Used to verify file integrity and identify content in IPFS.

**Hop**  
One step in message's journey through mesh. Phone A → Relay 1 → Relay 2 → Phone B = 3 hops. This network allows maximum 7 hops (~1-2 mile range).

**Hub Node**  
High-performance relay node (Mini PC with WiFi 6) at key locations for better video handling. Handles more traffic and faster speeds than standard relay nodes.

---

### I

**IPFS (InterPlanetary File System)**  
Peer-to-peer protocol for storing and sharing files in distributed way. Files identified by content (hash) not location. Once uploaded, files can't be deleted as long as anyone stores a copy.

---

### K

**Key Pair (Public/Private Keys)**  
Two mathematically related keys for encryption. Public key shared openly. Private key kept secret. Your wallet's private key signs messages proving they're really from you.

**Kotlin**  
Modern programming language for Android apps. Easier and safer than older languages. The mobile app is written in Kotlin.

---

### L

**Layer 2 (L2)**  
Blockchain networks built on Ethereum offering faster transactions and lower fees. Examples: Polygon, Base. This project uses L2 for affordable blockchain operations (pennies instead of dollars).

**Leaf Node**  
Device connecting to network but not relaying traffic for others. User phones are leaf nodes - only send/receive their own messages to save battery.

**libp2p (library peer-to-peer)**  
Modular networking library used internally by IPFS. In this project, libp2p is inside the go-ipfs daemon on bridge nodes - our application doesn't integrate it directly. User devices use native Android WiFi Direct, relay nodes use babeld for routing.

---

### M

**Matrix Protocol**  
Open-source, decentralized protocol for real-time messaging, voice, and video. No single company controls it. Anyone can run a Matrix server. This project uses Matrix for encrypted communication.

**Mesh Network**  
Network where each device connects to multiple nearby devices, forming web. Messages hop device-to-device until reaching destination. No central infrastructure required.

**Metadata**  
Data about data. For photos: GPS, date/time, camera settings. For messages: sender, recipient, timestamp. This project minimizes metadata to protect privacy.

---

### P

**P2P (Peer-to-Peer)**  
Direct communication between devices without central server. Like talking face-to-face instead of passing notes through teacher.

**Pinning (IPFS)**  
Telling IPFS node to keep permanent copy of specific content. Prevents important files from disappearing when original uploader goes offline.

**Private Key**  
Secret cryptographic key proving ownership and allowing signing/decrypting. Like a password but much more secure. Your wallet's private key must never be shared or lost.

**Pseudonymous**  
Using consistent fake identity (like wallet address) instead of real name. Different from anonymous (completely unknown) - actions traceable to pseudonym but pseudonym doesn't reveal real identity.

---

### Q

**QR Code**  
Square barcode storing information (like wallet address) scannable with camera. Easier than typing long addresses. Used to share wallet addresses for adding contacts.

---

### R

**Raspberry Pi**  
Small, cheap ($35-75) computer, credit card sized. Runs Linux, ideal for relay nodes. Low power consumption makes it perfect for always-on applications.

**Relay Node**  
Powered device (usually Raspberry Pi) forwarding messages for others. Forms mesh network backbone. Always-on and stationary, running babeld daemon.

**Reputation**  
Trust score based on endorsements from other users. High reputation indicates community trust. Built through endorsements, not purchased.

**Routing**  
Process of determining message path through network to reach destination. Like GPS navigation for data. This project uses Babel routing.

---

### S

**Seed Phrase / Recovery Phrase**  
12 or 24 words restoring access to crypto wallet. Must be written down and kept safe. If lost, wallet access permanently lost. If stolen, thief can access wallet.

**Smart Contract**  
Self-executing code on blockchain. Rules encoded and automatically enforced without requiring trust in any person or company. Used for governance in this project.

**Sneakernet**  
Moving data by physically carrying storage devices (or phones) between locations. Named because you use sneakers to "network." Effective for delay-tolerant applications.

**Solar Panel**  
Device converting sunlight to electricity. Powers relay nodes in locations without reliable wall power. Requires battery for nighttime. This project uses 20W panels.

**Stake / Staking**  
Locking up cryptocurrency as deposit. If you behave badly, stake can be "slashed" (taken away). Creates economic incentive for good behavior.

**Store-and-Forward**  
Holding messages at intermediate nodes until recipient comes online or route becomes available. Essential for delay-tolerant networking.

**Sybil Attack**  
Creating many fake identities to gain disproportionate influence. Like one person voting multiple times with fake IDs. Prevented through invitations, endorsements, and reputation.

---

### T

**TTL (Time To Live)**  
How long message exists before being deleted. Prevents old messages circulating forever. This project: 6 hours (text), 24 hours (photos), 72 hours (videos).

---

### V

**Vetting**  
Process of verifying someone is trustworthy before giving access. This project uses invitations from trusted members, endorsements from community, and optional stake requirements.

**VPN (Virtual Private Network)**  
Encrypts internet traffic and routes through another server. Hides what you're doing from ISP but they can still see you're using VPN.

---

### W

**Wallet**  
In cryptocurrency, stores your private keys (not actual coins). In this project, wallet address is your identity - like username that can't be changed. No email or phone needed.

**Wallet Address**  
Public identifier for crypto wallet. Looks like: 0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb. Used as pseudonymous identity in network. Can be shared publicly.

**Web3**  
Term for decentralized internet applications using blockchain. Emphasizes user ownership and control rather than corporate platforms.

**Web of Trust**  
Decentralized trust model where users vouch for each other rather than relying on central authority. Your trust in someone based on endorsements from people you already trust.

**WiFi Direct (WiFi P2P)**  
Technology allowing Android devices to connect directly via WiFi without router. Range: 200-500 feet. Bandwidth: 20-50 Mbps. One device becomes "group owner" (access point). Used for data transport in this mesh network.

---

## Common Acronyms

```
BLE - Bluetooth Low Energy
DAO - Decentralized Autonomous Organization
DHT - Distributed Hash Table
E2E - End-to-End (encryption)
ETX - Expected Transmission Count
IPFS - InterPlanetary File System
L2 - Layer 2 (blockchain)
P2P - Peer-to-Peer
QR - Quick Response (code)
TTL - Time To Live
VPN - Virtual Private Network
```

---

## Units of Measurement

**Data Size:** Bit → Byte (8 bits) → KB (1,000 bytes) → MB (1,000,000 bytes) → GB (1,000,000,000 bytes)

**Data Speed:** bps → Kbps (1,000 bps) → Mbps (1,000,000 bps)

**Distance:** 300 feet ≈ 90 meters | 1 mile ≈ 1.6 kilometers

**Power:** Watt (W) - unit of power consumption | 5W = typical Raspberry Pi | 20W = typical solar panel

**Time:** ms (millisecond) = 0.001 seconds | Lower latency = faster

---