# 🛡️ Red Shield: Quantum-Native Blockchain

[🌐 Official site](https://redshield.online) · [🔒 Security & verification](https://redshield.online/security) · [📥 Releases](https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases)

> **The first distributed ledger engineered from block zero to survive the post-quantum era.**

[![GitHub Release](https://img.shields.io/github/v/release/redshield-pqc/RED-SHIELD---SIMBA-Prime)](https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases)
[![GitHub Stars](https://img.shields.io/github/stars/redshield-pqc/RED-SHIELD---SIMBA-Prime?style=social)](https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Go Version](https://img.shields.io/badge/go-1.25.3-blue.svg)](https://golang.org)
[![NIST FIPS 204](https://img.shields.io/badge/crypto-NIST%20FIPS%20204-green.svg)](https://csrc.nist.gov)
[![Microsoft Security Intelligence](https://img.shields.io/badge/security-Microsoft%20Whitelisted-brightgreen.svg)](https://www.microsoft.com)

---

## ⚡ What Is Red Shield?

**Red Shield** is a **production-ready quantum-resistant blockchain** implementing the **SIMBA PRIME** consensus model. It decouples network influence from wealth through **merit-based validation**[...]

### Why Red Shield Matters

```
Legacy Chains (BTC, ETH, SOL)    →    Red Shield (Next Generation)
┌────────────────────────────────────────────────────────────────�[...]
│ ❌ ECDSA (vulnerable to Shor's)   │  ✅ ML-DSA-87 + Ed25519    │
│ ❌ Wealth = Power                 │  ✅ Contribution = Power   │
│ ❌ Linear scaling                 │  ✅ Logarithmic efficiency │
│ ❌ Single-axis risk               │  ✅ Triple-layer consensus │
│ ❌ Halts on partitions            │  ✅ Self-healing protocol  │
└────────────────────────────────────────────────────────────────�[...]
```

---

## 🚀 Quick Start (60 Seconds)

### 1️⃣ Download
```powershell
# Download from official releases
wget https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases/tag/SIMBA_PRIME_3.1
```

### 2️⃣ Verify & Install
```powershell
# Verify checksum
Get-FileHash .\RedShield-SIMBA_PRIME_v3.1.0.0.msi -Algorithm SHA256

# Run installer
.\RedShield-SIMBA_PRIME_v3.1.0.0.msi
```

### 3️⃣ Launch Dashboard
```powershell
# Red Shield Controller opens automatically
# Enter your REDS Reward Address
# Start validating!
```

**⏱️ Active Validator Status:** ~55 minutes from start

[📖 Full Installation Guide](INSTALL.md)

---

## 🎯 Key Features

### 🔐 Quantum-Native Security
| Feature | Benefit |
|---------|---------|
| **ML-DSA-87** (NIST FIPS 204) | Post-quantum signature security level 5 |
| **Ed25519** (Classical fallback) | Protection against zero-day implementation bugs |
| **SHAKE-256** (Universal hashing) | 128-bit post-quantum margin on all protocol identifiers |
| **Hardware-Bound Keys** (Windows DPAPI) | Signing keys tied to your specific machine & OS user |

### 💰 Anti-Whale Economics
| Mechanism | Effect |
|-----------|--------|
| **Quadratic Stake Weighting** | 100x capital = only 10x influence (not 100x) |
| **Conviction Multiplier** | 10-year lockup = 101x voting & production weight |
| **Merit-Based Promotion** | Small committed stakers > large liquid whales |

**Live Example:** 100k mBITS staked for 4 years beats 10M mBITS liquid by **70%**

[📊 Economics Deep Dive](ECONOMICS.md)

### ⚡ SIMBA PRIME Consensus
```
Layer 1: Proof of Authority (PoA)
  └─ Deterministic scheduling prevents spam

Layer 2: Proof of Capacity (PoC)
  └─ Storage-efficient "mining" via SHAKE-256 plots

Layer 3: Proof of Network (PoN)
  └─ Adaptive Byzantine fault tolerance finality
      Threshold = min(67%, max(51%, 4.45/log₂(N)))
```

[🏗️ Architecture Details](ARCHITECTURE.md)

### 🛡️ Never Halt Protocol
Network partitions heal automatically with **zero value loss**:
1. **Harvest** orphaned transactions
2. **Compare** trust via cumulative merit (PTS)
3. **Rollback** to common ancestor
4. **Sync** winning branch
5. **Resubmit** orphaned transactions
6. **Reconcile** via Commutative Transaction Union

---

## 📊 Network Specifications

| Parameter | Value |
|-----------|-------|
| **Chain ID** | `redshield-mainnet` |
| **Consensus** | SIMBA (PoA + PoC + PoN) |
| **Block Time** | 30 seconds |
| **Signature** | ML-DSA-87 + Ed25519 (hybrid) |
| **Hash** | SHAKE-256 |
| **Issuance** | KALKI+ (protocol-native) |
| **Annual Supply** | ~1,051.2 REDS (~0.1% inflation) |
| **Runtime** | Go 1.25.3 (memory-safe) |
| **Database** | BadgerDB v4 (lock-free LSM) |

---

## 🎮 Become a Validator

### Hardware Requirements
```
✓ Windows 10/11 (64-bit)
✓ 4+ GB RAM
✓ 10+ GB disk (SSD recommended)
✓ Open port 45507
✓ REDS Reward Address
```

### Revenue Model
**80/20 Block Reward Split:**
- **80%** → Block producer (immediate reward)
- **20%** → Staking pool (distributed to stakers by conviction)

**Example Annual Returns:**
- 100 GB plot allocation
- 4-year lockup conviction
- ~$X,XXX annual REDS earning potential

[💎 Join Validator Program](INSTALL.md)

---

## 📚 Documentation

| Document | Purpose |
|----------|---------|
| **[ARCHITECTURE.md](ARCHITECTURE.md)** | Technical protocol specification & design rationale |
| **[ECONOMICS.md](ECONOMICS.md)** | Token system, issuance, anti-whale mechanics |
| **[INSTALL.md](INSTALL.md)** | Step-by-step node deployment & troubleshooting |
| **[SECURITY.md](SECURITY.md)** | Cryptographic hardening & audit details |
| **[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)** | Merit-based community standards |

---

## 🔒 Security & Compliance

✅ **Microsoft Security Intelligence** - Official whitelist  
✅ **NIST FIPS 204/202** - Cryptographic standards compliance  
✅ **Go 1.25.3** - Memory-safe runtime (no buffer overflows)  
✅ **BadgerDB v4** - ACID-compliant ledger  
✅ **Hardware-Bound Keys** - DPAPI machine tethering  
✅ **Supply Chain Hardened** - go.sum integrity pinning (zero CVEs)  

[🛡️ Full Security Audit](RED%20SHIELD%20-%20SECURITY_CERTFICATE-04_JUNE_2026.md)

---

## 🌍 Community & Support

| Channel | Link |
|---------|------|
| **Official Website** | [https://redshield.online](https://redshield.online) |
| **Twitter/X** | [@RedShieldPQC](#) |
| **Email Support** | redshield.pqc@gmail.com |
| **GitHub Issues** | [Report Issues](https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/issues) |

---

## 🚀 Roadmap

| Quarter | Milestone |
|---------|-----------|
| **Q2 2026** | ✅ SIMBA PRIME v3.1 Launch |
| **Q3 2026** | Quantum Wallet v2.0 (Android/iOS) |
| **Q4 2026** | Mainnet TPS optimization (10k+) |
| **Q1 2027** | Cross-chain bridge protocols |

---

## 💡 Why Choose Red Shield?

### For Validators
✅ Merit-based earning potential (no whale dominance)  
✅ Hardware-bound security (laptop theft-proof)  
✅ Low operational cost (storage-efficient PoC)  
✅ Quantum-safe from day one  

### For Developers
✅ Open protocol specification  
✅ Production-hardened Go runtime  
✅ Comprehensive documentation  
✅ Active community support  

### For Organizations
✅ Institutional-grade security  
✅ Regulatory-compliant audit trail  
✅ Zero-value-loss partition recovery  
✅ Long-term cryptographic resilience  

---

## 📥 Get Started Now

**Choose Your Path:**

1. **I want to run a validator node**
   → [Installation Guide](INSTALL.md)

2. **I want to understand the protocol**
   → [Architecture & Economics](ARCHITECTURE.md)

3. **I want to join the community**
   → [Discord](#) | [Reddit](#)

4. **I found a security issue**
   → redshield.pqc@gmail.com

---

## 📄 License

Red Shield is released under the **MIT License**. See [LICENSE](LICENSE) for details.

---

## 🙏 Credits

**Built with cryptographic rigor by the Red Shield community.**

**MBITS © 2026 Red Shield — SIMBA PRIME v3.1**

> *Quantum-native. Merit-based. Never halts.*
