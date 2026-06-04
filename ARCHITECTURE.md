### **ARCHITECTURE.md (Forensic Framework & The SIMBA PRIME Model)**

This document details the mathematical and structural framework of the Red Shield protocol. It defines how the **SIMBA PRIME** model replaces legacy capital-concentration risks with a merit-based authority engine designed for the post-quantum era.

---

## **1. The SIMBA PRIME Pillars**
Red Shield operates on five architectural pillars that decouple network influence from financial wealth:

*   **[S] Self-Sovereign Node Identity:** Validators generate their own cryptographic identities via the **Trinity Model**. No central authority issues keys or certificates.
*   **[I] Identity-to-Authority Binding:** Authority is not bought; it is bound to identity through a **Progressive Trust Score (PTS)**. Influence is a direct result of verifiable work.
*   **[M] Merit-Based Validator Promotion:** Nodes ascend through status tiers automatically based on historical uptime and honest participation.
*   **[B] Behavioural Attestation (PoN):** Block finality requires a "Proof of Network"—a multi-validator behavioral endorsement of the state root.
*   **[A] Adaptive Consensus Scaling:** The network scaling requirement is logarithmic rather than linear, ensuring high performance as the validator set grows.

---

## **2. The Trinity Identity Model**
To minimize the attack surface, a node’s identity is split into three mathematically distinct roles:

1.  **Mother Wallet (Cold):** Derived from a machine-bound master secret. It serves as the registered identity but **never signs at runtime**, keeping the bulk of validator assets isolated.
2.  **Hot Key (SSNI) (Ephemeral):** A hybrid key pair (ML-DSA-87 + Ed25519) generated on boot. It resides in RAM to sign live attestations and blocks. It holds zero funds.
3.  **Reward Address (Decoupled):** A separate destination for block rewards. This ensures that even a total compromise of the operational node environment cannot lead to the theft of accumulated revenue.

---

## **3. Tri-Layer Consensus Engine**
Red Shield prevents single-axis dominance by requiring every block to satisfy three distinct proofs:

### **Layer 1: Proof of Authority (PoA) — Scheduling**
Leader selection is deterministic to prevent proposal spam.
*   **Logic:** `Leader = Height (mod ActiveValidatorCount)`.

### **Layer 2: Proof of Capacity (PoC) — Proposal**
Validators use pre-computed **SHAKE-256** plot files to "mine" for the lowest deadline. This replaces energy-intensive computation with efficient storage I/O.

### **Layer 3: Proof of Network (PoN) — Finality**
Finality is achieved through an **Adaptive Threshold** that ensures Byzantine fault tolerance:
$$\text{Threshold} = \min\left(67\%, \max\left(51\%, \frac{4.45}{\log_2(N)}\right)\right)$$
*   **Cap (67%):** Ensures safety in small validator sets.
*   **Floor (51%):** Guarantees a strict majority is always required.

---

## **4. Cryptographic Anchors**
Red Shield is "Quantum-Native from Block Zero," utilizing a hybrid stack to protect against both algorithmic and implementation-level failures:

*   **Primary Signature:** **ML-DSA-87** (NIST FIPS 204), providing Security Level 5 protection.
*   **Secondary Signature:** **Ed25519**, providing a high-speed classical fail-safe against zero-day implementation bugs in post-quantum libraries.
*   **Universal Hashing:** **SHAKE-256** (NIST FIPS 202) used for all state commitments and identifiers, providing a 128-bit post-quantum security margin.

---

## **5. The "Never Halt" Protocol**
Red Shield treats network partitions as temporary states to be healed, rather than catastrophic events. During a partition recovery, the network executes a **6-step resolution algorithm**:
1.  **Harvest** orphaned transactions from the abandoned fork.
2.  **Compare** chain trust based on cumulative PTS (merit) rather than height.
3.  **Rollback** to the common ancestor.
4.  **Sync** the winning branch.
5.  **Resubmit** orphaned transactions to the mempool.
6.  **Reconcile** via a **Commutative Transaction Union**, ensuring zero user value is lost.

**MBITS © 2026 Red Shield — .\SIMBA_PRIME_3.1.exe .**

---