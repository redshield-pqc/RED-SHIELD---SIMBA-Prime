### **INSTALL.md (Technical Onboarding & Security Verification)**

This document provides the authoritative instructions for deploying a **Red Shield SIMBA PRIME v3.1** node. Unlike legacy "one-click" miners, the Red Shield deployment is a security-first process that tethers your node identity to your hardware via **Machine-Bound Encryption**.

---

## **📋 Prerequisites**
*   **Operating System:** Windows 10/11 (64-bit).
*   **Hardware:** Minimum 4GB RAM; 10GB disk I/O availability for PoC plot files.
*   **Network:** Open inbound/outbound ports (Default: `45507`) for **libp2p** gossip and DHT discovery.
*   **Identity:** A valid 64-character **REDS Reward Address** (generated via the Quantum Native Wallet).

---

## **📥 1. Acquisition & Integrity Verification**
The production node is delivered exclusively as a **signed Windows MSI installer** built via a hardened WiX pipeline.

1.  **Download:** Obtain `RedShield-SIMBA_PRIME_v3.1.0.0.msi` from the [Official Releases](https://github.com/redshield-pqc/RED-SHIELD---SIMBA-Prime/releases/tag/SIMBA_PRIME_3.1).
2.  **Verify Checksum:** Open PowerShell and run the following command to ensure the binary has not been tampered with:
    ```powershell
    Get-FileHash .\RedShield-SIMBA_PRIME_v3.1.0.0.msi -Algorithm SHA256
    ```
3.  **Compare:** Match the output against the values in the provided **SHA256SUM.txt**.

---

## **🛠️ 2. Installation Procedure**
1.  **Run Installer:** Execute the MSI. The installer will deploy the **Red Shield Controller** (GUI) and the **Red Shield Engine** (Go-based Core).
2.  **Security Clearance:** Our binaries are whitelisted by **Microsoft Security Intelligence**. If a "Windows Protected Your PC" prompt appears, ensure your Defender definitions are updated (`MpCmdRun.exe -SignatureUpdate`).
3.  **Machine-Binding:** During installation, the system utilizes **Windows DPAPI** to initialize your master secret. This secret is mathematically encrypted to your specific OS user and hardware fingerprint; **it cannot be moved to another machine by copying files**.

---

## **🚀 3. The Onboarding Wizard**
Upon first launch, the Controller will initiate a mandatory security handshake to prevent accidental network fragmentation.

*   **Reward Wallet:** Enter your REDS address. This is where your 80% share of block rewards will be sent.
*   **Peer Discovery:** You must connect to at least one **non-local bootstrap peer**. The node is hard-coded with a **Genesis-Lock**; it will refuse to start if it detects a "localhost-only" environment to prevent unintended forks.
*   **PoC Plotting:** The engine will generate a small initial plot file. You can configure larger storage allocations (GB/TB) through the **Dashboard > Plotting** tab to increase your block production probability.

---

## **🔒 4. Local Security Architecture**
Once running, your node operates under a **Triple-Hardened Local Environment**:
1.  **Controller/Engine Split:** The UI and Core are separate processes.
2.  **IPC Bearer Token:** Local communication is secured via an ephemeral `RED_SHIELD_IPC_TOKEN`. Unauthorized local apps cannot send commands to your node.
3.  **Integrity Pinning:** Every time the Controller starts, it verifies the **SHA-256 hash** of the `SIMBA_PRIME_3.1.exe` engine. If the binary is modified, the system will self-halt.

---

## **📊 5. Verification of Status**
Monitor your **Progressive Trust Score (PTS)** on the Dashboard.
*   **Bootstrap Phase:** Your node will remain in "Observer" status for the first **100 blocks** (~50 minutes).
*   **Promotion:** Upon reaching **50.1 PTS**, your node is automatically promoted to **Active** status and can begin winning the PoC lottery for block production.

**MBITS © 2026 Red Shield — .\SIMBA_PRIME_3.1.exe .**

---