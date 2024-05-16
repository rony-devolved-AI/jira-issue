### This will build json config file for our blockchain based on staging configuration

```bash
./target/release/argochain build-spec --disable-default-bootnode --chain staging > customSpec.json
```

```bash
./target/release/argochain build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json
```

### For running with local Config

```bash
./target/release/argochain build-spec --disable-default-bootnode --chain local > customSpec.json
```

```bash
./target/release/argochain build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json
```

#### Need to purge if we have already ran a node, Or will conflict with database

```bash
./target/release/argochain purge-chain --base-path /tmp/node01 --chain customSpecRaw.json
rm -rf /tmp/node01 # Replace node01 with your --base-path /tmp/<?>
```

___
## Add validator keys


##### validator 1

```bash 
./target/release/argochain key insert --base-path /tmp/node01 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x202641b917fbf0286b9042cf2b7b8669146b6b73607990bf99e177e4867228b0 \
--password-interactive \
--key-type babe

./target/release/argochain key insert --base-path /tmp/node01 \
--chain ./customSpecRaw.json \
--scheme Ed25519 \
--suri 0xc912ef91d7fcaf8cd73d11d637f74680ec0cbd32cba50bbb5e45a272b3cda43a \
--password-interactive \
--key-type gran

./target/release/argochain key insert --base-path /tmp/node01 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x6edca157aaf7764c9d5b1d9128fd05a1661372f91687085131d04646118cce7e \
--password-interactive \
--key-type imon

./target/release/argochain key insert --base-path /tmp/node01 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0xe020a42d9084762730a768c1ba2254186770b77d39e82899206429b050f7cc19 \
--password-interactive \
--key-type audi
```
###### Key password: ****** `Any password you like` 

##### No Need to use `nohup, &` if you do not want to make it running in background

```bash
nohup ./target/release/argochain \
--base-path /tmp/node01 \
--chain ./customSpecRaw.json \
--port 30333 \
--rpc-port 9944 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--rpc-methods Unsafe \
--rpc-max-connections 15000 \
--rpc-cors all \
--name MyNode01 &
```
___

> `Save your local Identity` 

##### validator 2

```bash 
./target/release/argochain key insert --base-path /tmp/node02 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x7d37ea3331962daa1f6abb7e5743c4e3bd4cd5b976819151fac674dc884618d1 \
--password-interactive \
--key-type babe

./target/release/argochain key insert --base-path /tmp/node02 \
--chain ./customSpecRaw.json \
--scheme Ed25519 \
--suri 0xc8e2d366c7d28161b194f225d0278120812319c329fbfc9043ea517e0b2da129 \
--password-interactive \
--key-type gran

./target/release/argochain key insert --base-path /tmp/node02 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x685d8f16de5fb38ae202b7ae80ef72ae46a26d7f624bd1bb18d0fcfd7c06919a \
--password-interactive \
--key-type imon

./target/release/argochain key insert --base-path /tmp/node02 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x3feeda2930f647927e9f7c91091735581d3fd90150b936c7432885ac9aeb49a8 \
--password-interactive \
--key-type audi
```
###### Key password: ****** `Any password you like` 


##### No Need to use `nohup, &` if you do not want to make it running in background

```bash
nohup ./target/release/argochain \
--base-path /tmp/node02 \
--chain customSpecRaw.json \
--port 30334 \
--rpc-port 9946 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--rpc-methods Unsafe \
--unsafe-rpc-external \
--rpc-cors all \
--rpc-max-connections 15000 \
--name MyNode02 \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/<Local Identity> &

```
___


##### validator 3

```bash 
./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0xdeea43096c89a250f2066e630930b6526190afed744e1084510863a18e26ea4f \
--password-interactive \
--key-type babe

./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Ed25519 \
--suri 0xa9425b499cd82b5e01f23a85221090235921445ce6d60cac640717a8351f2701 \
--password-interactive \
--key-type gran

./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x27abdb874f0a6ad9a1478ad41f2d3ebb1b566dd5ebc71d9478c89b3bd9607647 \
--password-interactive \
--key-type imon

./target/release/argochain key insert --base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--scheme Sr25519 \
--suri 0x1a12b0c6c5f5e59e38d6acf9e08da442d346322aba6a23dd3761be5002898ae1 \
--password-interactive \
--key-type audi
```
###### Key password: ****** `Any password you like` 


##### No Need to use `nohup, &` if you do not want to make it running in background

```bash
nohup ./target/release/argochain \
--base-path /tmp/node03 \
--chain ./customSpecRaw.json \
--port 30335 \
--rpc-port 9947 \
--telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
--validator \
--rpc-methods Unsafe \
--rpc-max-connections 2500 \
--name MyNode03 \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/<Local Identity> &

```
___




