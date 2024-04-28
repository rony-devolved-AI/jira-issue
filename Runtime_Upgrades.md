
# Runtime Upgrades Guide

This guide explains how to perform runtime upgrades on a Substrate-based blockchain. Runtime upgrades enable the blockchain to introduce new features, fix bugs, and modify the chain's behavior without the need for node restarts or hard forks.

## Prerequisites

Before you begin, ensure you have:
- Administrative access to the blockchain.
- A prepared and tested new runtime Wasm binary.
- Access to the Substrate node's CLI or a user interface capable of interacting with the blockchain, such as Polkadot JS Apps.

## Steps for Runtime Upgrade

### Step 1: Prepare the New Runtime

1. **Develop and Test**: Develop the new runtime according to your blockchain's needs. Thoroughly test the new runtime in a test environment to ensure stability and compatibility.

2. **Compile to WASM**: Compile the updated runtime to a Wasm binary. This binary is what will be uploaded to the blockchain. Use the following command to compile:
   ```bash
   cargo build --release
   ```

### Step 2: Submit the Upgrade Proposal

#### Generate a Wasm file
Extract the Wasm file from your build target directory. It usually resides under:

`./target/release/wbuild/your-blockchain-name/your_runtime.compact.wasm`


#### Create a Proposal
Using a governance mechanism (like a council or a general assembly via a democratic process), submit a proposal for the runtime upgrade. The proposal should include the new Wasm file.

**Example using Polkadot JS Apps:**
1. Navigate to "Democracy".
2. Propose a "System.set_code" call.
3. Attach your Wasm file.


### Step 3: Vote on the Proposal

#### Community or Council Voting
Depending on your governance structure, the proposal will need to be approved by either the validator community or a council.

#### Monitor the Vote
Use your blockchain’s governance interface to monitor the voting process.

### Step 4: Applying the Upgrade

#### Automatic Execution
Once the proposal is approved and passes any additional governance hurdles (like a referendum, if applicable), the upgrade will automatically be applied at the block specified in the proposal.

#### Verify the Upgrade
After the block at which the upgrade was set to apply passes, verify that the new runtime is active. Check the version and ensure all new functionalities are operational.

### Post-Upgrade

After the upgrade, monitor the network for any unforeseen issues. Check logs, node health, and user feedback to ensure that the network operates as expected.




