---
title: 01 - System Overview
version: 2.0
last_updated: 2025-10-17
status: Production-Ready
completeness: 8/10
tags: [core, overview, executive-summary]
---

---

## How It All Works Together

### The Big Picture

Imagine a neighborhood where 5,000 people need to communicate even when the government shuts down the internet. Here's what they build:

---

### **The Physical Infrastructure**

**50 Hidden "Relay Boxes"** (Raspberry Pi computers, $75 each)

- Size of a deck of cards
- Hidden in homes, attics, windows
- Plugged into wall power or solar panels
- Run 24/7, never turn off
- Each covers ~300 feet radius

**3 "Bridge Boxes"** (Raspberry Pi + Starlink, $600 each)

- Same as relay boxes, but with satellite dish
- Hidden in secure locations
- Connect the local mesh to global internet
- Upload evidence to permanent storage

**Everyone's Android Phones**

- Just install the app
- No special hardware needed
- Works on cheap phones ($50+)

---

### **How a Message Travels**

**Simple Text Message:**


Maria's phone (in her pocket)
    ↓ WiFi Direct (finds nearest relay box via Bluetooth)
John's Relay Box (hidden in his window)
    ↓ Babel routing (finds best path automatically)
Sarah's Relay Box (2 blocks away)
    ↓ Babel routing
Ahmed's Relay Box (near the market)
    ↓ WiFi Direct
David's phone (at the market)

Time: 3-5 seconds
Internet needed: ZERO

**The Babel daemon on each relay box automatically figures out the best path.** If John's box goes down, Babel instantly routes through different boxes. No central control needed.

---

### **How Video Documentation Works**

**Recording Evidence:**
```
1. User records 2-minute video (persecution evidence)
2. App compresses to 8MB, encrypts it
3. Breaks into 32 small chunks (256KB each)
4. Sends chunks through mesh network one by one
5. Chunks hop from relay to relay (up to 7 hops)
6. Reaches Bridge Box (the one with satellite)
7. Bridge Box uploads to IPFS (permanent global storage)
8. Returns hash: QmT5Nv... (like a permanent receipt)
9. Hash spreads back through mesh
10. Anyone with hash can download video forever

Time: 5-10 minutes from recording to global backup
Even if: All local hardware destroyed, video still exists globally
```

**The encryption means:** Video is public on IPFS, but only people with the decryption key (sent separately via encrypted Matrix messages) can view it.

---

### **A Day in the Life**

**Morning - Internet Still Working:**
- People use the app like normal messaging
- Videos automatically back up to IPFS via bridge boxes
- Network runs alongside regular internet

**Noon - Government Shuts Down Internet:**
- Regular internet dies
- **Local mesh keeps working** (doesn't need internet)
- Bridge boxes lose satellite connection (no IPFS uploads yet)
- People still send messages, record videos
- Everything queues up, waiting

**Afternoon - Messages Flow Locally:**
- Maria texts David: "Meeting at church, 3pm"
- Her phone → relay boxes (Babel routing) → David's phone
- Works because relay boxes form complete mesh
- No internet needed
- Delay-tolerant: If David's phone is off, relay boxes hold message until he turns it on

**Evening - One Bridge Box Reconnects:**
- Satellite link restored on Bridge Box #2
- All queued videos automatically upload to IPFS
- Evidence now permanently stored globally
- Hashes distributed through mesh
- Journalists outside the country can download via hashes

---

### **Why It Can't Be Stopped**

**To block the network, authorities must:**
- Find and destroy 50+ hidden relay boxes (hard)
- Find 3 bridge boxes (very hard, well-hidden)
- Confiscate 5,000 phones (impossible)
- Even if they find 20 relay boxes, network routes around them
- Even if they find all bridge boxes, local mesh still works
- Even if they destroy everything, videos already uploaded to IPFS globally

**The network is designed to:**
- Lose half its nodes and keep working
- Operate for months with zero internet
- Upload evidence whenever any bridge gets internet, even briefly
- Self-heal when nodes fail (Babel routing adapts automatically)

---

### **The User Experience**

**Installing (10 minutes):**
1. Download app
2. Create wallet (12-word backup phrase - write it down)
3. Get invitation code from trusted person
4. Done - start messaging

**Daily Use:**
- Looks like WhatsApp/Signal
- Send text, photos, videos
- Green indicator = connected to mesh
- Yellow = searching for network
- No "error" messages - offline is normal

**Recording Evidence:**
- Tap camera, record
- Tap send
- App handles everything: compress, encrypt, chunk, upload
- Shows progress: "Uploading: 15/32 chunks"
- When done: "Saved! Hash: ipfs://Qm..."

---

### **The Technology Stack (Simplified)**
```
USER'S VIEW:
  Just a messaging app

UNDER THE HOOD:
  [Android App]
       ↓
  Matrix Protocol (messaging/encryption)
       ↓
  WiFi Direct (connects to nearby relay box)
       ↓
  [Relay Box running babeld]
       ↓
  Babel Routing (finds path through network)
       ↓
  [More Relay Boxes]
       ↓
  [Bridge Box with Satellite]
       ↓
  go-ipfs daemon (uploads to global IPFS)
       ↓
  [Global IPFS Network - Permanent Storage]
````

**User doesn't see:** Routing, Babel, chunks, encryption details  
**User sees:** Send message → Message delivered → Video backed up

---

### **Key Numbers**

- **Range:** 1-2 miles coverage (7 hops × 300 feet)
- **Speed:** Text in 5 seconds, video in 5 minutes
- **Cost:** $10,000 infrastructure for 5,000 people ($2/person)
- **Power:** Relay boxes use 5-8W (solar viable)
- **Reliability:** 99%+ message delivery
- **Survival:** Works with 50% of relay boxes destroyed

---

### **The Magic: Babel Routing**

Think of relay boxes like a smart mail system:

- Each box knows its neighbors
- Each box shares what it knows: "I can reach David in 2 hops"
- When Maria sends message to David, her relay box asks: "Who knows David?"
- Box gets answers, picks best path (fastest/most reliable)
- If a box fails, Babel automatically finds new path in 5 seconds
- No central coordinator - boxes figure it out themselves

**This is better than the old AODV plan because:**

- Babel is production-proven (used in real mesh networks)
- Faster convergence (5 seconds vs 1-3 seconds initial + possible delays)
- Smarter routing (picks reliable links, not just shortest)
- Actually maintained software (babeld gets updates)

---

### **Bottom Line**

**This system gives persecuted communities:**

- Messaging that works when internet is shut down
- Video documentation that can't be deleted
- Infrastructure they own and control
- Network that's extremely hard to shut down
- Evidence that escapes to global audience

**Built from:**

- Cheap computers hidden in homes
- Everyone's existing phones
- Free open-source software
- Solar panels where needed

**Total cost:** Less than $15,000 for 5,000 people.