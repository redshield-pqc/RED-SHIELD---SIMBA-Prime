### **SECURITY.md (Forensic Audit & Hardening Standards)**

This document outlines the security architecture and forensic standards enforced in the **Red Shield SIMBA PRIME v3.1** production release. The protocol is engineered with a **defense-in-depth** strategy to mitigate classical, quantum, and implementation-level vulnerabilities.

---

## **1. Cryptographic "Double-Signing" Fail-Safe**
Red Shield explicitly implements **Quantum-Resistant Hybrid Signatures** to neutralize the "ticking time bomb" of implementation bugs identified in recent cryptographic research.

*   **Standard Compliance:** Uses **ML-DSA-87** (NIST FIPS 204) and **Ed25519**.
*   **Formula 2 Requirement:** A block or transaction is only valid if **both** signatures verify over the same SHAKE-256 hash.
*   **Implementation Resilience:** This hybrid model ensures that even if a zero-day flaw (such as side-channel leakage or nonce-reuse errors) were discovered in an ML-DSA library, the ledger remains immutable because the **Ed25519 signature** remains a secondary barrier.
*   **Domain Separation:** Enforced using the context string `RED_SHIELD_V10_MAINNET_TRANS` to prevent cross-protocol replay attacks.

---

## **2. Machine-Bound Security (Hardware Tethering)**
To prevent secret key extraction via unauthorized software copying, the **SIMBA_PRIME_3.1** engine utilizes hardware-bound encryption.

*   **Windows DPAPI:** Signing keys are encrypted using the **Windows Data Protection API**, mathematically binding them to the specific hardware fingerprint and OS user.
*   **Trinity Identity Model:** Separates node roles into a **cold Mother Wallet** (identity), an **ephemeral Hot Key** (signing), and a **decoupled Reward Address** (payment).
*   **RAM Residency:** Signing keys live exclusively in encrypted RAM during runtime and are never stored in plain text on the local filesystem.

---

## **3. Local Environment Hardening**
The production node operates under a **Controller/Engine Split** to isolate the user interface from consensus-critical code.

*   **Integrity Pinning:** The Flutter-based Controller embeds the exact **SHA-256 hash** of the `RedShieldEngine.exe`. If the binary is tampered with or replaced, the system refuses to boot.
*   **Hardened Local IPC:** Communication between the Controller and Engine is secured via an ephemeral **IPC Bearer Token** (`RED_SHIELD_IPC_TOKEN`). This prevents other local applications from hijacking node control.
*   **Auto-Healing Configs:** The node includes a syntax-repair engine that automatically corrects configuration errors to prevent crashes and maximize uptime [Source 4].

---

## **4. Forensic Runtime Safety**
The core engine is built on a modern, memory-safe toolchain to eliminate common attack vectors found in legacy blockchain engines.

*   **Language Version:** Compiled with **Go 1.25.3**, providing inherent immunity to buffer overflows and use-after-free vulnerabilities.
*   **Hardened P2P:** Utilizes a bespoke override of **libp2p v0.44.0** with TLS 1.3/Noise encryption and **GossipSub** for flood-protected block propagation.
*   **Crash-Resilient DB:** Uses **BadgerDB v4**, a lock-free LSM-tree database that provides ACID compliance and resilience against ledger corruption during hardware failures.

---

## **5. Institutional Compliance & Clearance**
Red Shield has undergone manual review to ensure its advanced cryptographic behavior is recognized as benign by major security vendors.

*   **Microsoft Security Intelligence:** The production binaries have been **manually reviewed and whitelisted** by Microsoft to eliminate false-positive antivirus detections related to its DPAPI integration.
*   **Dependency Integrity:** The build pipeline enforces strict cryptographic checksumming via `go.sum`, ensuring zero critical vulnerabilities in the pinned module tree.

**MBITS © 2026 Red Shield — .\SIMBA_PRIME_3.1.exe .**

---