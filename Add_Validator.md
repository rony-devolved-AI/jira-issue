# Adding New Validator


### Install Rust In Linux
> Go to *https://docs.substrate.io/install/linux/* 
### Or

```bash
1. sudo apt install build-essential
2. sudo apt install --assume-yes git clang curl libssl-dev protobuf-compiler
3. curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
4. source $HOME/.cargo/env
5. rustc --version
6. rustup default stable
7. rustup update
8. rustup update nightly
9. rustup target add wasm32-unknown-unknown --toolchain nightly
```

### Install Rust In Windows
> Go to *https://docs.substrate.io/install/windows/* 
### Or

```bash
1. wsl --install
```
This command enables the required WSL 2 components that are part of the Windows operating system, downloads the latest Linux kernel, and installs the Ubuntu Linux distribution by default.

> For More Info Go to *https://learn.microsoft.com/en-us/windows/wsl/setup/environment* 

```bash
1. sudo apt update
2. sudo apt install --assume-yes git clang curl libssl-dev llvm libudev-dev make protobuf-compiler
3. curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
4. source ~/.cargo/env
5. rustc --version
6. rustup default stable
7. rustup update
8. rustup update nightly
9. rustup target add wasm32-unknown-unknown --toolchain nightly
```

### Setup The Repo

```bash
1. git clone --branch chainspec-modified https://github.com/Devolved-AI/Argochain.git
2. cd Argochain
3. cargo build --release
```

### Run As Validator: 

```bash
 nohup ./target/release/argochain \
  --base-path /tmp/<Give path> \
  --chain customSpecRaw.json \
  --port <Give your desired Port Number> \
  --rpc-port <Give your desired Rpc Port Number> \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --unsafe-rpc-external \
  --rpc-cors all \
  --rpc-max-connections 15000 \
  --name <Validator Name> \
  --bootnodes /ip4/<Bootnode Ip>/tcp/30333/p2p/<Bootnode Local ID> &
```

#### Example 

```bash
nohup ./target/release/argochain \
--base-path /tmp/node07 \
--chain ./customSpecRaw.json \
--port 30345 \
--rpc-port 9955 \
--name MyNode06 \
--validator \
--rpc-methods Unsafe \
--unsafe-rpc-external \
--rpc-max-connections 15000 \
--rpc-cors all  &
```
#### Do Staking

1. Go to https://explorer.argoscan.net/ 
2. Network Section
3. Then Staking
4. Then Accounts section
5. Click on validator
6. Get Your rotatekeys  > Open terminal > Move to Argochain folder then Do this Command
`curl -H "Content-Type: application/json" --data '{"jsonrpc":"2.0", "method":"author_rotateKeys", "params":[], "id":1}' http://localhost:9950` 
> Here http://localhost:your rpc port

7. Example : 
`{"jsonrpc":"2.0","result":"0x53f1c4efcf83e0d80f44d49be724faa18998ec6ebed8b5c79f936af1bc16d31730c9adf49829c42333d6e32fe858b682bcc0dbe8f2ead6be4dd5ac85a400c12d12ec9ae40f71222c087f4eadede7086b5bbb5102676ce64eac8e1daf8499921d04ceb33b8c112517f8052ea2e4e0b7d9a1f291e054c831724ca9dd555fed4f77","id":1}ronnie
        `

8. Copy the `result` section and paste it to `rotatekeys` section 
9. Click On Bond & Validate
10. Wait for an Era (Approximate 1 hour) for the participation of block validation.
