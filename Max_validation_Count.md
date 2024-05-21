## Documentation: Validator Count Proposal for Substrate-Based Blockchain Network (PoS and BABE)

### Table of Contents
1. **Introduction**
2. **Factors Influencing the Number of Validators**
   - Consensus Mechanism
   - Decentralization Goals
   - Security Considerations
   - Network Throughput and Performance
3. **Proposed Validator Count**
   - Minimum Viable Network
   - Scaling the Network
4. **Research Analysis**
   - Existing Networks
   - Performance Studies
5. **Validation**
   - Simulation and Testing
   - Community Feedback
   - Iterative Approach
6. **Conclusion and Next Steps**

---

### 1. Introduction
Launching a Substrate-based blockchain network with Proof of Stake (PoS) and Blind Assignment for Blockchain Extension (BABE) consensus mechanisms involves critical decisions regarding the optimal number of validators. Validators are essential for maintaining the network's security, decentralization, and performance. This document outlines a comprehensive analysis and proposal for the initial number of validators required to start a Substrate-based blockchain network using PoS and BABE.

### 2. Factors Influencing the Number of Validators

#### Consensus Mechanism
Substrate-based networks utilizing PoS and BABE require careful consideration of the validator count:
- **Proof of Stake (PoS)**: Validators are chosen based on their stake in the network, promoting security and decentralization.
- **Blind Assignment for Blockchain Extension (BABE)**: A slot-based consensus protocol that determines block producers, working in tandem with PoS.

#### Decentralization Goals
- **Higher Number of Validators**: Enhances decentralization, reducing the risk of control by a few entities.
- **Lower Number of Validators**: Improves efficiency and simplifies coordination but may centralize control.

#### Security Considerations
- **More Validators**: Increases security through distributed trust and lowers the risk of collusion.
- **Initial Validator Count**: Must balance security needs with the ease of network management and scalability.

#### Network Throughput and Performance
- **More Validators**: Can lead to higher network latency and lower transaction throughput.
- **Balance**: Essential to maintain an optimal balance between validator count and network performance.

### 3. Proposed Validator Count

#### Minimum Viable Network
For a Substrate-based network with PoS and BABE, the initial validator count can be determined as follows:
- **PoS and BABE**: Starting with 10-20 validators ensures a balance between decentralization, security, and efficiency.

#### Scaling the Network
- **Initial Low Count**: Begin with 10-20 validators, scalable as the network matures and gains adoption.
- **Governance Mechanisms**: Implement mechanisms to dynamically add or remove validators based on network performance and governance decisions.

### 4. Research Analysis

#### Existing Networks
- **Polkadot**: Utilizes Nominated Proof of Stake (NPoS) and BABE, starting with a manageable number of validators and scaling up as needed. Started with `20 Validators` and plan to scale up to `1000 validators` . As of 2024, Polkadot has `372 active validators`
- **Kusama**: Experimental network for Polkadot, initially deploying fewer validators to test scalability and performance. Started with `50 validators` and planning to scale up to `1000 validators` . As of now it has  over `900 validators`

#### Performance Studies
- **PoS Networks**: Studies indicate performance degradation with too many validators, necessitating an optimal starting point.
- **BFT Networks**: (Byzantine Fault Tolerant)  Illustrate the trade-off between security and performance, with fewer validators typically offering better efficiency.

### 5. Validation

#### Simulation and Testing
- **Network Simulations**: Conduct simulations to test network performance and security with varying validator counts.
- **Analysis Metrics**: Focus on block time, transaction throughput, and network latency.

#### Community Feedback
- **Engagement**: Engage potential network participants to gather their preferences and willingness to become validators.
- **Feedback Incorporation**: Adjust the proposed validator count based on community input.

#### Iterative Approach
- **Initial Conservative Count**: Start with a lower number of validators and increase based on network stability and feedback.
- **Governance Framework**: Establish rules for dynamic adjustment of validator count through governance mechanisms.

### 6. Conclusion and Next Steps

#### Conclusion
Starting with `10-20 validators` for a Substrate-based blockchain network using PoS and BABE provides a good balance between decentralization, security, and performance. Adjustments can be made based on specific network needs, community feedback, and ongoing performance analysis.


By considering these factors and following a structured approach, the network can ensure a robust and scalable validator setup from the outset.