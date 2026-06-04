# Red Shield SIMBA Prime Node - V3.1.0.0 (Public Release)

We are thrilled to announce the public release of **Red Shield SIMBA Prime Node V3.1.0.0**! 

This major update brings significant hardening to our core Go engine, a beautifully updated Flutter-based dashboard, and a seamless MSI installer for Windows users. 

## 🚀 Key Highlights & Changes
* **Production-Hardened Engine:** The core node engine has been heavily optimized and compiled with advanced code protections.
* **Auto-Healing Configuration:** The node now automatically detects and heals common syntax errors in your `config.toml` (such as unquoted Peer IDs), ensuring maximum uptime and preventing crashes.
* **Streamlined UI:** Upgraded to the latest Flutter stable dependencies (including `flutter_local_notifications` 20+ and `share_plus` 12+), resolving all legacy deprecations and ensuring smooth, reliable system notifications.
* **Instant Status Updates:** The dashboard HUD now flawlessly transitions to display the active `V3.1.0.0` network version the moment the IPC layer handshakes with the background engine.
* **Hardware-Bound Security:** Upgraded cryptographic integration with the Windows Data Protection API (DPAPI) to securely bind node keys directly to your machine's hardware fingerprint.

## 📦 Assets & Installation
Please download the attached **MSI Installer** below. 

1. Run `RedShield-SIMBA_PRIME_v3.1.0.0.msi`
2. Follow the on-screen prompts to install the Node Controller.
3. Launch the **Red Shield Controller** from your Start Menu.

> **Note on Windows Defender:** 
> Our executable is signed and has been manually cleared by Microsoft Security Intelligence. However, if your local Windows Defender definitions are slightly out of date, it may occasionally flag the engine during installation due to aggressive machine learning heuristics on P2P software. If this happens, please simply update your Windows Defender signatures (`MpCmdRun.exe -SignatureUpdate`).

## 🔐 Verifying Your Download
We highly recommend verifying the integrity of your download. Compare the hash of your downloaded MSI file against the provided `SHA256SUM.txt`.

**Using PowerShell:**
```powershell
Get-FileHash -Algorithm SHA256 .\RedShield-SIMBA_PRIME_v3.1.0.0.msi
```
