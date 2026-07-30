# 🚀 Installation Guide

**Official Website:** https://redshield.online

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
□ Downloaded MSI installer from official releases (see verification below)
```

---

## 1. Acquisition & Integrity Verification

The production node is delivered as a **signed Windows MSI installer** built via a hardened WiX pipeline.

### Official download sources
- Canonical website (primary): https://redshield.online
- GitHub Releases (mirrors/artefacts): https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases

**Important:** Always verify releases using checksums and detached signatures hosted on the official website before running installers.

### Step 1.1: Download the Installer

📥 **Primary Source:** https://redshield.online (look for the "Releases" or "Downloads" section)

📥 **Mirror/Backup:** GitHub Releases: https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases

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

Retrieve the canonical SHA256SUM file and its detached PGP signature from the official website:

- SHA256SUM file (canonical): https://redshield.online/releases/SHA256SUM.txt
- Detached PGP signature: https://redshield.online/releases/SHA256SUM.txt.sig

Verify the SHA256 matches the official file. Then verify the detached PGP signature using the project PGP key (PGP fingerprint is published on the official website). Example:

```bash
# Verify PGP signature (example using GPG)
gpg --keyserver hkps://keys.openpgp.org --recv-keys <PGP_KEY_ID>
gpg --verify SHA256SUM.txt.sig SHA256SUM.txt
```

**If you do not see matching hashes and a valid PGP signature from the official key, DO NOT INSTALL the binary.**

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

Our binaries are claimed to be **manually whitelisted by Microsoft Security Intelligence**. Always validate this independently by checking the Authenticode signature and scanning with multiple engines.

**To validate Authenticode signature:**

1. Right-click on the MSI → Properties → Digital Signatures tab
2. Verify the signer name and timestamp
3. Optionally use signtool:

```powershell
signtool verify /pa /v RedShield-SIMBA_PRIME_v3.1.0.0.msi
```

### Step 2.3: Machine-Binding (Key Initialization)

During installation, the system initializes your **master secret** using **Windows DPAPI**. Keys are machine- and user-bound as described in SECURITY.md.

---

## 3. The Onboarding Wizard

(unchanged; see original INSTALL.md for onboarding flows)

---

## 4. Local Security Architecture

(unchanged; Controller/Engine split, IPC bearer token, integrity pinning remain in effect)

---

## 5. Verification of Status

(unchanged)

---

## 6. Troubleshooting

(unchanged)

---

## 7. Next Steps

🎉 **Congratulations!** Your validator is running.

**What to do next:**
1. ✓ Monitor Dashboard for block production
2. ✓ Expand PoC plot storage if desired (Plotting tab)
3. ✓ Join the community: [Red Shield Discord] or visit https://redshield.online
4. ✓ Read SECURITY.md for advanced configurations

---

**© 2026 Red Shield — SIMBA PRIME v3.1**

*Security-first deployment. Production-ready validation.*
