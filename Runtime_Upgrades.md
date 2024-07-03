
# Runtime Upgrades Guide

This guide explains how to perform runtime upgrades on a Substrate-based blockchain. Runtime upgrades enable the blockchain to introduce new features, fix bugs, and modify the chain's behavior without the need for node restarts or hard forks.

## Prerequisites

Before you begin, ensure you have:
- Administrative access to the blockchain.
- A prepared and tested new runtime Wasm binary.
- Access to the Substrate node's CLI or a user interface capable of interacting with the blockchain, such as Polkadot JS Apps.

### Point to be Noted: 
   - Runtime Upgrade will happen from the next block of transaction submit .

```rust
#[sp_version::runtime_version]
pub const VERSION: RuntimeVersion = RuntimeVersion {
    spec_name: create_runtime_str!("node-template"),
    impl_name: create_runtime_str!("node-template"),
    authoring_version: 1,
    spec_version: 100,
    impl_version: 1,
    apis: RUNTIME_API_VERSIONS,
    transaction_version: 1,
    state_version: 1,
};

```

- Increment `spec_name` and `impl_name` accordingly cause both bear different meaning 
- `spec_name` specifies the name of the runtime.
- `impl_name` specifies the name of the outer node client.
- To upgrade the runtime, you must increase the spec_version



**Spec Version:**

**When to Use:** Increment the `spec_version` whenever there is a change in the runtime logic or the way transactions are processed.

**Example Scenarios:**
- Adding or removing pallets (runtime modules).
- Changing the behavior of existing pallets.
- Updating the parameters or types of dispatchable functions.
- Modifying the format of transactions.

**Reason:** Nodes will not attempt to use their native runtime in place of the on-chain Wasm runtime unless the `spec_version` matches. This ensures that all nodes agree on the same runtime logic and maintain consensus.

---

**Impl Version:**

**When to Use:** Increment the `impl_version` when there are changes to the implementation that do not affect the runtime logic.

**Example Scenarios:**
- Refactoring code for better readability or maintainability.
- Applying optimizations that do not alter the behavior of the runtime.
- Fixing bugs that do not change the runtime's logic.

**Reason:** This version indicates that the implementation has changed. It allows developers to track changes in the code without affecting the consensus or compatibility of the nodes. Nodes can ignore this version for runtime compatibility checks as long as `spec_version` and `authoring_version` match.


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

`./target/release/wbuild/your-blockchain-name/your_runtime.compact.compressed.wasm`


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

![Screenshot from 2024-04-28 15-42-19](https://github.com/rony-devolved-AI/jira-issue/assets/157959679/100bfe73-0954-429c-8726-9e2da0b800cd)

#### Automatic Execution
Once the proposal is approved and passes any additional governance hurdles (like a referendum, if applicable), the upgrade will automatically be applied at the block specified in the proposal.

#### Verify the Upgrade
After the block at which the upgrade was set to apply passes, verify that the new runtime is active. Check the version and ensure all new functionalities are operational.

### Post-Upgrade

After the upgrade, monitor the network for any unforeseen issues. Check logs, node health, and user feedback to ensure that the network operates as expected.

## Manually

![Runtime_upgrade](https://github.com/rony-devolved-AI/jira-issue/assets/157959679/cc0bbae2-218f-4a67-baad-f98d9499079d)

- Click On `Submit Sudo`
- In this Only `Sudo Account` have the permission to do forkless upgrade .






- For more info visit the official substrate docs *https://docs.substrate.io/tutorials/build-a-blockchain/upgrade-a-running-network/*
