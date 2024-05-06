# Becoming a Validator on a Substrate-based Blockchain

This guide provides step-by-step instructions on how to become a validator on a Substrate-based blockchain. It covers the installation of necessary tools, generation of cryptographic keys, and configuration of a blockchain node.

## Prerequisites

- **Rust:** Ensure that Rust and `rustup` are installed on your system. You can check your current Rust version by running `rustc --version`.
- **Substrate Node:** A compiled Substrate node ready to be configured for your specific blockchain (in this example, named `argochain`).

## 1. Update Rust Toolchain

To compile `subkey` and other blockchain-related tools, your Rust toolchain needs to be up to date:

```bash
rustup update stable
rustc --version
```
# 2. Install Subkey

`subkey` is a tool for generating and managing cryptographic keys used in Substrate and Polkadot networks:

```bash
cargo install subkey --force --locked
```

# 3. Generate Cryptographic Keys

You need to generate several types of keys for different roles within the network. Here are the commands to generate keys using `subkey`:



### BABE (Block Production)

```bash
subkey generate --scheme Sr25519 --password-interactive
```


### GRANDPA (Finality Gadget)


```bash
subkey generate --scheme Ed25519 --password-interactive
```


### IM Online

```bash
subkey generate --scheme Sr25519 --password-interactive
```

### Authority Discovery

```bash
subkey generate --scheme Sr25519 --password-interactive
```


# 4. Configure Your Node

After generating your keys, use them to configure your blockchain node. Replace <seed-phrase> with your actual generated seed phrase.

### Insert BABE Key

```bash
./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri <seed-phrase> \
--password-interactive \
--key-type babe
```


### Insert GRANDPA Key
```bash
./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Ed25519 \
--suri <seed-phrase> \
--password-interactive \
--key-type gran
```

### imonline Keys
```bash
./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri <seed-phrase> \
--password-interactive \
--key-type imon
```

### Authority-discovery keys
```bash
./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri <seed-phrase> \
--password-interactive \
--key-type audi
```

# 5. Start Your Node as a Validator

#### Finally, start your node with the following command to act as a validator:

```bash 
./target/release/argochain \
--base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--port 30335 \
--rpc-port 9947 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--rpc-methods Unsafe \
--rpc-max-connections 2500 \
--name MyNode03 \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/<local-identiry>
```

`This command includes parameters for networking, RPC configuration, and telemetry among others. Adjust these settings based on your network setup and requirements.`