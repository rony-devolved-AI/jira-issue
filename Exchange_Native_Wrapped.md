### Understanding Native Tokens on Substrate-Based Blockchains

1. **Native Tokens vs. Smart Contract Tokens**:
   - **Native Tokens**: Managed by the blockchain itself (in your case, AGC on Argochain). They are represented directly in the runtime and ledger of the blockchain.
   - **Smart Contract Tokens**: These are tokens like ERC-20 on Ethereum that are represented by smart contracts with their own token logic and addresses.

2. **No Address for Native Tokens**:
   - On Substrate-based blockchains, there is no contract address for the native token (AGC). Instead, balances are stored directly in the runtime, associated with the user's account.

### How to Create a Liquidity Pool with a Native Token like AGC

To swap a native token like AGC with a token like WETH on a Substrate-based blockchain, you need to handle both types of tokens differently. Here’s how you can set up a liquidity pool:

### 1. **Understanding the Setup**

- **AGC (Native Token)**: Exists in the Substrate runtime, not as a smart contract.
- **WETH or Bridged WETH (`bWETH`)**: Exists as a smart contract token (likely an ERC-20 equivalent or similar) on your blockchain if brought over from Ethereum.

### 2. **Steps to Create a Liquidity Pool**

#### Step 1: **Ensure WETH or `bWETH` is Deployed**

1. **Deploy `bWETH` on Your Blockchain**:
   - Since your blockchain is Substrate-based, WETH cannot exist natively. You would need a wrapped version of WETH (`bWETH`) if it isn’t already deployed.
   - This could involve creating a bridge to Ethereum or deploying a smart contract on your blockchain that mints `bWETH` when WETH is locked on Ethereum.

#### Step 2: **Create a DEX Pallet or Use an Existing One**

1. **DEX Pallet**:
   - You need a DEX (decentralized exchange) pallet that supports native tokens and smart contract tokens. You might use an existing pallet like `pallet-xyk` (XYK stands for "constant product market maker", similar to Uniswap) or develop a custom pallet if needed.
   - This pallet will handle swaps between the native token (AGC) and smart contract tokens (`bWETH`).

2. **Add Liquidity Functionality**:
   - The DEX pallet must allow users to add liquidity using both the native token (AGC) and `bWETH`. Since AGC does not have a contract address, it is referenced by its existence in the runtime.

#### Step 3: **Initialize the Pool with Both Tokens**

1. **Initialize the Liquidity Pool**:
   - Set up the liquidity pool within the DEX pallet using AGC (native) and `bWETH` (smart contract token).
   - Users provide liquidity by depositing AGC and `bWETH` into the pool.

#### Step 4: **Enable Swaps**

1. **Activate the Pool**:
   - Once initialized, users can perform swaps between AGC and `bWETH`.
   - The DEX pallet will manage the trading logic and ensure the swaps adhere to the constant product formula (or any other liquidity formula being used).


### Summary

In Substrate-based blockchains like Argochain:
- Native tokens like AGC do not have contract addresses because they are managed by the blockchain's runtime.
- To create a liquidity pool with a native token and a smart contract token (like `bWETH`), use a DEX pallet that supports both token types.
- Deploy the DEX pallet, set up the liquidity pool with AGC and `bWETH`, and manage the pool to facilitate swaps.
