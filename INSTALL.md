# 🚀 Installation Guide

## Red Shield SIMBA PRIME v3.1 — Technical Onboarding & Security Verification

> Unlike legacy "one-click" miners, Red Shield deployment is a **security-first process**. Follow these steps to bootstrap a production-hardened validator node.

---

## 📋 Table of Contents
- [Prerequisites](#prerequisites)
- [1. Acquisition & Integrity Verification](#1-acquisition--integrity-verification)
- [2. Installation Procedure](#2-installation-procedure)
- [3. The Onboarding Wizard](#3-the-onboarding-wizard)
- [4. Local Security Architecture](#4-local-security-architecture)
- [5. Verification of Status](#5-verification-of-status)
- [6. Troubleshooting](#6-troubleshooting)

---

## Prerequisites

Before you begin, ensure you have:

| Requirement | Specification | Notes |
|-------------|---------------|-------|
| **OS** | Windows 10/11 (64-bit) | Windows-only for DPAPI binding |
| **RAM** | Minimum 4 GB | 8 GB recommended for smooth operation |
| **Disk Space** | 10+ GB available | For Proof-of-Capacity plot files |
| **Network** | Open ports (45507) | For libp2p gossip & DHT discovery |
| **Identity** | Valid REDS Reward Address | 64-character hex, from Quantum Wallet |

### Pre-Installation Checklist

```
□ Windows 10/11 (64-bit) installed and up-to-date
□ 4+ GB free RAM available
□ 10+ GB free disk space (SSD recommended)
□ Network ports 45507 inbound/outbound accessible
□ REDS Reward Address generated (from Quantum Wallet)
□ Downloaded MSI installer from official releases
```

---

## 1. Acquisition & Integrity Verification

The production node is delivered as a **signed Windows MSI installer** built via a hardened WiX pipeline.

### Step 1.1: Download the Installer

📥 **Source:** [Official Red Shield Releases](https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases/tag/SIMBA_PRIME_3.1)

**File:** `RedShield-SIMBA_PRIME_v3.1.0.0.msi`

### Step 1.2: Verify Checksum (SHA-256)

Open **PowerShell** and verify the installer hasn't been tampered with:

```powershell
# Compute SHA-256 hash of the MSI
Get-FileHash -Algorithm SHA256 .\RedShield-SIMBA_PRIME_v3.1.0.0.msi

# Output example:
# Algorithm       Hash                                                   Path
# ---------       ----                                                   ----
# SHA256          A1B2C3D4E5F6G7H8... (64 hex characters)              RedShield-SIMBA_PRIME_v3.1.0.0.msi
```

### Step 1.3: Compare Against Official Hash

Match your output against **SHA256SUM.txt** (provided with release):

```
✓ If hashes match: Safe to proceed
✗ If hashes differ: DO NOT INSTALL — download again from official source
```

---

## 2. Installation Procedure

### Step 2.1: Run the MSI Installer

1. **Double-click** `RedShield-SIMBA_PRIME_v3.1.0.0.msi`
2. **Allow** Windows to request administrator privileges
3. Follow the on-screen prompts

**What Gets Installed:**
- ✓ **Red Shield Controller** (Flutter GUI dashboard)
- ✓ **Red Shield Engine** (Go-based consensus core)
- ✓ **System integrations** (Windows DPAPI binding, libp2p stack)

### Step 2.2: Windows Defender / Security Intelligence

Our binaries are **manually whitelisted by Microsoft Security Intelligence**.

**If you see "Windows Protected Your PC":**

1. Click **"More info"**
2. Click **"Run anyway"**
3. Ensure your **Windows Defender definitions are current**:

```powershell
# Update Defender definitions
MpCmdRun.exe -SignatureUpdate
```

> **Why?** Our use of DPAPI and cryptographic libraries may trigger older Defender signatures. This is normal and expected.

### Step 2.3: Machine-Binding (Key Initialization)

During installation, the system initializes your **master secret** using **Windows DPAPI**:

```
Installation Process:
├─ Extract files
├─ Initialize Windows DPAPI context
├─ Generate machine-bound master secret
├─ Encrypt to OS user + hardware fingerprint
├─ Create Trinity identity model keys
└─ Complete
```

**What This Means:**
- Your signing keys are **mathematically bound to your specific hardware and OS user**
- Keys **cannot be moved** to another machine
- Compromise of your laptop **cannot lead to** key theft
- Keys are **never stored** unencrypted on disk

---

## 3. The Onboarding Wizard

On first launch, the **Controller** initiates a mandatory security handshake to prevent accidental network fragmentation.

### Step 3.1: Enter Your Reward Wallet

```
┌──────────────────────────────────────────┐
│  ONBOARDING WIZARD                       │
├──────────────────────────────────────────┤
│                                          │
│  ✓ Reward Wallet Address                │
│    Input: 64-character REDS address      │
│    Purpose: Receive 80% of block rewards │
│                                          │
│    Example: 1A2B3C4D5E6F...              │
│                                          │
└──────────────────────────────────────────┘
```

**Important:**
- This address receives your **80% block producer share**
- It should be generated from your **Quantum Native Wallet**
- It **cannot be changed after initialization**

### Step 3.2: Peer Discovery & Genesis Lock

Your node must connect to at least **one non-local bootstrap peer**.

```
Genesis Lock Check:
  ├─ Node auto-detects local peer connections
  ├─ Refuses to start if "localhost-only"
  ├─ Enforces connection to mainnet bootstrap peers
  └─ Prevents accidental test-network forking
```

**Bootstrap Peers:** Hard-coded in the engine; downloaded automatically.

### Step 3.3: Proof-of-Capacity (PoC) Plot Generation

The engine generates your initial plot file:

```
PoC Plotting:
  ├─ Initial plot: Small demo plot (100 MB)
  ├─ Configuration: Dashboard > Plotting tab
  ├─ Expansion: Allocate more storage (GB/TB) to increase production probability
  └─ Storage I/O: Replaces energy-intensive computation
```

**Plot Storage Tiers:**

| Allocation | Impact | Notes |
|-----------|--------|-------|
| **100 MB** (default) | ~0.1% block probability | Demo tier, learning purposes |
| **10 GB** | ~10% block probability | Serious participation |
| **100 GB** | ~100% block probability | Professional setup |
| **1 TB+** | Substantial advantage | High-end deployment |

---

## 4. Local Security Architecture

Once running, your node operates under **triple-hardened security**:

### Layer 1: Controller/Engine Split

```
┌─────────────────────────────────────────────┐
│  CONTROLLER/ENGINE ARCHITECTURE             │
├─────────────────────────────────────────────┤
│                                             │
│  ┌─────────────────┐   ┌──────────────┐   │
│  │ Flutter GUI     │   │ Go Engine    │   │
│  │ (Controller)    │   │ (Consensus)  │   │
│  │                 │◄─►│              │   │
│  │ Dashboard       │   │ Validator    │   │
│  │ Configuration   │   │ Block signing│   │
│  │ Monitoring      │   │ State updates│   │
│  └─────────────────┘   └──────────────┘   │
│         ▲                      ▲            │
│         │                      │            │
│    IPC Bearer Token        Local Unix Socket
│    Ephemeral               Hardened Comms
│    (renewed per session)                   │
│                                             │
└─────────────────────────────────────────────┘
```

**Benefit:** UI compromise doesn't compromise consensus logic.

### Layer 2: IPC Bearer Token

Local communication is secured via an **ephemeral bearer token**:

```
Environment Variable: RED_SHIELD_IPC_TOKEN
├─ Generated: On Controller start
├─ Lifetime: Session duration only
├─ Requirement: Required for all IPC calls
├─ Rotated: Every session
└─ Purpose: Prevent unauthorized local access
```

**Protection:**
- ✓ Unauthorized local apps cannot send commands to your node
- ✓ Only the Controller process has the valid token
- ✓ Token expires when Controller closes

### Layer 3: Integrity Pinning

Every time the Controller starts, it verifies the engine binary:

```
Startup Sequence:
  ├─ Controller launches
  ├─ Compute SHA-256 of SIMBA_PRIME_3.1.exe
  ├─ Compare against embedded hash
  ├─ If match: ✓ Safe to proceed
  └─ If mismatch: ✗ Self-halt (modified binary detected)
```

**Result:** Protects against:
- ✗ Malware binary replacement
- ✗ Supply-chain compromise
- ✗ Accidental corruption

---

## 5. Verification of Status

Monitor your **Progressive Trust Score (PTS)** on the Dashboard.

### Dashboard Indicators

```
┌─────────────────────────────────────────┐
│  RED SHIELD DASHBOARD                   │
├─────────────────────────────────────────┤
│                                         │
│  Status: Observer                       │
│  PTS: 0.0 / 100.0                       │
│  Blocks Processed: 47 / 100             │
│  Time Remaining: ~26 minutes             │
│                                         │
│  [Progress Bar: ████░░░░░░░░░░░░░░]    │
│                                         │
│  ℹ️  Bootstrap phase active. Observe    │
│     the network, build trust.           │
│                                         │
└─────────────────────────────────────────┘
```

### Phase 1: Bootstrap Observer (0–100 blocks)

**Duration:** ~50 minutes

**Activities:**
- Node listens to the network
- Processes blocks to sync chain state
- Builds initial Progressive Trust Score
- **Cannot produce blocks yet** (Observer status)

**Status Display:**
```
Status: 🔵 Observer
PTS: [building...]
```

### Phase 2: Active Validator (50.1+ PTS)

**When:** Upon reaching **50.1 PTS**

**What Happens:**
- ✓ Automatic promotion to **Active** status
- ✓ Eligible to win **PoC lottery** for block production
- ✓ Receiving **20% staking pool rewards**
- ✓ Participation in **finality voting** (PoN)

**Status Display:**
```
Status: 🟢 Active
PTS: 50.1+
Next Block Probability: 12.3%
```

### Expected Timeline

| Milestone | Time | Notes |
|-----------|------|-------|
| **Node Start** | 0 min | Bootstrap begins |
| **First Blocks** | ~2 min | Syncing network state |
| **50 blocks** | ~25 min | Building trust |
| **100 blocks** | ~50 min | Bootstrap complete |
| **Active Status** | ~55 min | Ready for block production |

---

## 6. Troubleshooting

### Issue: "Windows Protected Your PC" on Launch

**Solution:**
1. Click "More info" → "Run anyway"
2. Update Windows Defender: `MpCmdRun.exe -SignatureUpdate`
3. Whitelist the installer in Defender if needed

### Issue: Node Won't Connect to Peers

**Solution:**
1. Check firewall: Port `45507` open inbound/outbound
2. Restart Controller → Engine will re-attempt connection
3. Check network connectivity: `ping 8.8.8.8`

### Issue: PTS Not Increasing

**Solution:**
1. Ensure you're connected to at least 1 peer (Dashboard shows peers count)
2. Wait for block synchronization (~50 minutes)
3. Check logs: `Dashboard > Logs` tab

### Issue: Defender Still Blocks After Update

**Solution:**
1. Add to Exceptions: `Settings > Virus & threat protection > Manage settings > Add exceptions`
2. Add: `C:\Program Files\Red Shield\SIMBA_PRIME_3.1.exe`
3. Contact support: **redshield.pqc@gmail.com**

---

## 7. Next Steps

🎉 **Congratulations!** Your validator is running.

**What to do next:**
1. ✓ Monitor Dashboard for block production
2. ✓ Expand PoC plot storage if desired (Plotting tab)
3. ✓ Join the community: [Red Shield Discord]
4. ✓ Read SECURITY.md for advanced configurations

---

**© 2026 Red Shield — SIMBA PRIME v3.1**

*Security-first deployment. Production-ready validation.*