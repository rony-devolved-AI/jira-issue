# Conflic checking between Substrate and EVM Accounts

### Substrate Account 

| Feature                      | Substrate Account                                 | EVM-Compatible Account                              | Potential Conflicts                          |
| ---------------------------- | ------------------------------------------------- | --------------------------------------------------- | -------------------------------------------- |
| **Underlying Technology**    | Customizable blockchain framework.                | Runs Ethereum smart contracts; uses Ethereum tools. | Different base technologies limit direct interoperability. |
| **Account Format**           | Uses public-private key pair, SS58 address format. | Hexadecimal address format derived from public key. | Incompatible address formats can complicate cross-platform interactions. |
| **Compatibility**            | Customizable, can integrate EVM if configured.    | Directly compatible with Ethereum and its dApps.    | Default configurations may not support cross-chain functionality without modifications. |
| **Functionality and Use**    | Highly customizable, supports governance, staking. | Focused on smart contracts and dApps.               | Substrate's broader functionality may not be fully utilizable in EVM without specific adjustments. |
| **Security and Network**     | Additional security features can be designed.     | Depends on Ethereum's security and features.        | Security assumptions and features may differ, requiring careful integration planning. |



