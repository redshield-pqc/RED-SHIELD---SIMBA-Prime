# Red Shield Security & Architecture

Red Shield is designed from the ground up to address the two most critical existential threats to modern blockchain networks: **Quantum Computing** and **Network Partitioning**.

---

## 1. Post-Quantum Cryptography (PQC)

Current blockchain networks rely heavily on Elliptic Curve Cryptography (ECDSA) or RSA for securing digital signatures. As quantum computers advance, specifically with the implementation of Shor's algorithm, these traditional cryptographic methods will be easily broken, rendering modern wallets and identities completely insecure.

### The Red Shield Solution: ML-DSA
Red Shield is a "Quantum Native" ecosystem. We have abandoned legacy ECDSA entirely in favor of the NIST-standardized **ML-DSA (Module-Lattice-Based Digital Signature Algorithm)**, formally.

- **Lattice-Based Security:** ML-DSA relies on the hardness of finding short vectors in lattices, a mathematical problem that is provably resistant to both classical and quantum algorithms.
- **Future-Proof Identity:** Every wallet generated on the Red Shield network, and every SIMBA Prime node identity, uses ML-DSA. Your assets are secure today, and will remain secure against the supercomputers of tomorrow.

---

## 2. SIMBA Protocol (Synchronized Intelligent Multi-node Blockchain Architecture)

The second existential threat to decentralized networks is hardware failure, censorship, or geographical network partitioning. Traditional chains often halt, fork destructively, or lose transactions when nodes go offline.

### The SIMBA Mandate
The SIMBA protocol enforces three core rules across the network:
1. **Never Halt:** The system NEVER stops. If nodes are isolated, they adapt, queue, and continue operating within their local shard.
2. **Zero Loss:** Every valid transaction is preserved through any event. Txs are queued locally when isolated and broadcasted immediately upon reconnection.
3. **Intelligent Resolution:** When diverging chains reconnect, SIMBA does not simply discard the shorter chain. It finds the common ancestor and intelligently UNIONS all valid transactions from both chains, applying the chain with the higher PoN (Proof of Network) trust score, while automatically replaying orphaned transactions atomically.

---

## 3. Trinity Identity Logic & Progressive Trust Score (PTS)

To prevent Sybil attacks and ensure only dedicated hardware secures the network, Red Shield utilizes a dual-layer identity and trust system.

### Trinity Identity Architecture
Every SIMBA Prime node operates using three distinct keys:
1. **The Mother Wallet (Identity Sink):** The on-chain representation of the node.
2. **The Hot Key (Consensus Sink):** An ephemeral key stored only in local memory, used for rapidly signing block proposals and attestations without exposing the Mother Wallet.
3. **The Reward Wallet (Financial Sink):** A completely decoupled wallet where all block production and staking pool rewards are routed. This prevents any single point of financial compromise on the node machine.

### Progressive Trust Score (PTS)
Nodes are not granted voting power merely by existing or staking capital. In Red Shield, nodes **earn** their authority.
- **Bootstrapping:** New nodes begin as Candidates.
- **Earning Trust:** By consistently proposing valid blocks, maintaining uptime, and participating in Proof of Network (PoN) cycles, nodes earn points towards their Progressive Trust Score.
- **Promotion:** Once a node proves its reliability over time (Conviction), it is automatically promoted to a **Guardian** status, granting it full consensus rights. 

This ensures that the network is governed exclusively by proven, historically reliable actors, rather than simply whoever has the most money.
