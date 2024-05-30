## Documentation: Validator Count Proposal for Substrate-Based Blockchain Network (PoS and BABE)

### Table of Contents
1. **Question**
2. **Existing Answer**
3. **Factors Influencing the Number of Validators**
   - Consensus Mechanism
   - Decentralization Goals
   - Security Considerations
   - Network Throughput and Performance
4. **Proposed Validator Count**
   - Minimum Viable Network
   - Scaling the Network
5. **Research Analysis**
   - Existing Networks
   - Performance Studies
6. **Validation**
   - Simulation and Testing
   - Community Feedback
   - Iterative Approach
7. **Conclusion**

---

### 1. Question
How many validators to be there to start the chain ?
____
### 2. Existing Answer
**False**
___

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
_____
### 3. Proposed Validator Count

#### Minimum Viable Network
For a Substrate-based network with PoS and BABE, the initial validator count can be determined as follows:
- **PoS and BABE**: Starting with 10-20 validators ensures a balance between decentralization, security, and efficiency.

#### Scaling the Network
- **Initial Low Count**: Begin with 10-20 validators, scalable as the network matures and gains adoption.
- **Governance Mechanisms**: Implement mechanisms to dynamically add or remove validators based on network performance and governance decisions.
____
### 4. Research Analysis

#### Existing Networks
- **Polkadot**: Utilizes Nominated Proof of Stake (NPoS) and BABE, starting with a manageable number of validators and scaling up as needed. Started with `20 Validators` and plan to scale up to `1000 validators` . As of 2024, Polkadot has `372 active validators`
- **Kusama**: Experimental network for Polkadot, initially deploying fewer validators to test scalability and performance. Started with `50 validators` and planning to scale up to `1000 validators` . As of now it has  over `900 validators`

#### Performance Studies
- **PoS Networks**: Studies indicate performance degradation with too many validators, necessitating an optimal starting point.
- **BFT Networks**: (Byzantine Fault Tolerant)  Illustrate the trade-off between security and performance, with fewer validators typically offering better efficiency.
___
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
___
### 6. Conclusion 

#### Conclusion
Starting with `10-20 validators` for a Substrate-based blockchain network using PoS and BABE provides a good balance between decentralization, security, and performance. Adjustments can be made based on specific network needs, community feedback, and ongoing performance analysis.


By considering these factors and following a structured approach, the network can ensure a robust and scalable validator setup from the outset.



### Initial Validator Counts for Substrate-Based Blockchains

Here is a summary of the initial number of validators for various Substrate-based blockchains:

1. **Polkadot**
   - **Initial Validators**: Polkadot started with around 20 validators and gradually increased this number as part of their scaling strategy. Over time, Polkadot has implemented programs such as the Thousand Validators Programme to increase decentralization and security by expanding the validator set.
   - **Details**: Validators are selected based on the Nominated Proof of Stake (NPoS) consensus mechanism, where both self-stake and nominations from other participants are considered.

2. **Kusama**
   - **Initial Validators**: Kusama, Polkadot’s canary network, began with about 25 validators.
   - **Details**: Similar to Polkadot, Kusama uses the NPoS consensus mechanism, allowing for rapid iteration and testing of new features before they are deployed on Polkadot.

3. **Acala Network**
   - **Initial Validators**: Acala started with approximately 20 validators.
   - **Details**: As a DeFi hub on Polkadot, Acala leverages the shared security and interoperability provided by the Polkadot relay chain.

4. **Phala Network**
   - **Initial Validators**: Phala Network began with about 10 validators.
   - **Details**: Phala focuses on providing secure and decentralized off-chain compute resources, using a Proof of Stake (PoS) consensus mechanism.

5. **Edgeware**
   - **Initial Validators**: Edgeware started with 15 validators.
   - **Details**: Edgeware is a smart contract platform that uses Substrate, starting with a manageable number of validators to ensure network stability.

6. **Centrifuge**
   - **Initial Validators**: Centrifuge initially used 10 validators.
   - **Details**: This network focuses on financial supply chain applications and uses a PoS consensus mechanism to secure transactions.

These initial validator counts were chosen to balance security, decentralization, and network performance. Starting with a smaller number of validators allows these networks to establish stability and gradually scale as they grow.

For more detailed information, you can visit their respective websites or refer to resources such as the Polkadot Wiki and other developer documentation.