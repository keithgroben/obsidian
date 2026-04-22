---
title: Development - Technology Stack & Architecture
version: 2.0
last_updated: 2025-10-23
status: Production-Ready
parent: 11-development
related:
  - 11-00-development-overview
  - 11-01-development-phases
  - 02-architecture
  - 03-hardware-specifications
tags: [development, technology, stack, architecture]
---

## Mobile App Stack

### Language & Framework
- **Kotlin** (Android native)
- **Jetpack Compose** (modern UI)
- Minimum SDK: Android 8.0 (API 26)
- Target SDK: Android 14+ (API 34)

### Core Libraries

**Networking:**
- WiFi Direct: `android.net.wifi.p2p`
- BLE: `android.bluetooth.le`
- HTTP client: OkHttp or Retrofit

**Encryption & Identity:**
- Matrix SDK (Java/Kotlin fork)
- Web3j (Ethereum wallet integration)
- Android Keystore API

**Media:**
- MediaCodec (video compression)
- CameraX (camera API)
- ExoPlayer (video playback)

**Storage:**
- Room (local database)
- DataStore (preferences)
- File encryption: Jetpack Security

**IPFS:**
- HTTP client only (not full daemon)
- Custom API wrapper for Pinata/Web3.Storage

### Architecture Pattern
- MVVM (Model-View-ViewModel)
- Repository pattern for data
- Clean architecture principles
- Dependency injection: Hilt/Dagger

---

## Relay Node Stack

### Hardware
- Raspberry Pi 4 (4GB RAM minimum)
- 64GB+ microSD card (A2 rating)
- Power: 5V/3A USB-C
- WiFi: Built-in + optional external adapter
- Ethernet: Built-in for uplink

### Operating System
- Raspberry Pi OS Lite (64-bit)
- Minimal installation (no desktop)
- Automatic updates enabled
- Hardened security configuration

### Core Services

**Routing:**
- `babeld` (Babel routing daemon)
- Custom configuration for mesh
- Automatic route updates
- Metrics export for monitoring

**Messaging:**
- Matrix Synapse (lightweight mode)
- SQLite backend (small deployments)
- PostgreSQL (larger deployments)
- Federation disabled (mesh-only)

**IPFS Gateway:**
- Custom Go service (not full daemon)
- HTTP API only
- Caching layer (100GB)
- Pin monitoring client

**Monitoring:**
- Prometheus (metrics collection)
- Node exporter (system metrics)
- Custom mesh metrics exporter
- Grafana dashboard (optional)

### Database
- SQLite for <100 users per node
- PostgreSQL for >100 users per node
- Automatic backups
- Replication for critical nodes

---

## Bridge Node Stack

### Hardware
- Intel NUC or Raspberry Pi 5
- 8GB+ RAM
- 256GB+ SSD
- Dual Ethernet (mesh + WAN)
- Starlink dish + router

### Operating System
- Ubuntu Server 24.04 LTS
- Minimal installation
- Automatic security updates
- Firewall: ufw configured

### Core Services

**Connectivity:**
- Starlink satellite internet
- WireGuard VPN (privacy)
- Automatic failover (if multiple WANs)
- Traffic shaping/QoS

**IPFS Services:**
- Lightweight HTTP gateway (Go)
- Pinata API client
- Web3.Storage API client
- Pin monitoring service
- Local cache (500GB-1TB)

**Monitoring:**
- Prometheus + Grafana
- Uptime monitoring
- Bandwidth tracking
- Pin status dashboard
- Alert system (critical failures)

### Security
- UFW firewall (strict rules)
- Fail2ban (intrusion prevention)
- WireGuard VPN (all WAN traffic)
- Automatic security updates
- Log rotation and monitoring

---

## Smart Contract Stack

### Language & Framework
- Solidity ^0.8.20
- Hardhat (development/testing)
- TypeScript for scripts
- Ethers.js for interaction

### Libraries
- OpenZeppelin Contracts:
  - `Ownable` (access control)
  - `Pausable` (emergency stops)
  - `TimelockController` (delayed execution)
  - `TransparentUpgradeableProxy` (upgradability)

### Deployment Target
- **Polygon PoS** (primary choice)
  - Low fees (~$0.01 per vote)
  - Fast confirmation (2-3 seconds)
  - EVM compatible
- **Base L2** (alternative)
  - Lower fees (~$0.001 per vote)
  - Coinbase backing
  - Growing ecosystem

### Testing
- Hardhat Network (local)
- Mumbai testnet (Polygon)
- Base Goerli (Base)
- 100% test coverage required
- Formal verification (critical functions)

### Security
- Multiple audits required
- Slither static analysis
- Mythril symbolic execution
- Manual review by experts
- Bug bounty program post-launch

---

## Development Tools

### Version Control
- Git + GitHub/GitLab
- Conventional commits
- Branch protection rules
- Code review required

### CI/CD
- GitHub Actions or GitLab CI
- Automated testing on commits
- Android APK builds
- Smart contract testing
- Security scanning

### Testing
- JUnit (unit tests)
- Espresso (Android UI tests)
- Hardhat (smart contract tests)
- Selenium (web dashboard tests)

### Documentation
- Markdown (technical docs)
- Dokka (Kotlin API docs)
- Solidity NatSpec (contract docs)
- Swagger/OpenAPI (API specs)

---

## Third-Party Services

### IPFS Pinning
- **Pinata** (primary)
  - Free tier: 1GB storage
  - Paid: $20/month for 10GB
  - API rate limits: 30 req/min
- **Web3.Storage** (backup)
  - Free tier: 1TB storage
  - No egress fees
  - W3C standard APIs

### Infrastructure
- **Starlink** (satellite internet)
  - $120/month per bridge
  - 50-150 Mbps down
  - 10-20 Mbps up
  - 20-40ms latency

### Monitoring (Optional)
- Sentry (error tracking)
- DataDog (infrastructure monitoring)
- PagerDuty (alerting)

---

## Performance Targets

### Mobile App
- Cold start: <3 seconds
- Message send: <500ms (local network)
- Video compression: <60s for 2-min video
- Battery drain: <5%/hour with screen off
- APK size: <50MB

### Relay Nodes
- Message routing: <100ms per hop
- Concurrent connections: 50+ devices
- Uptime: 95%+ required
- CPU usage: <50% average
- Memory: <2GB used

### Bridge Nodes
- IPFS upload: <30s for 10MB file
- Pin confirmation: <2 minutes
- Concurrent uploads: 10+ simultaneous
- Uptime: 99%+ required
- Bandwidth: Handle 100+ concurrent users

---

## Related Documents

- **11-00:** Development overview
- **11-01:** Detailed phase breakdown
- **02:** System architecture
- **03:** Hardware specifications
