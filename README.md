# ReadMe for ERC20.sol and Vault.sol Readme

## ERC20.sol

The ERC20.sol smart contract is a basic implementation of the Ethereum ERC-20 token standard. ERC-20 tokens are one of the most common and widely used token standards in the Ethereum ecosystem. This contract represents a token named "Solidity by Example" with the symbol "SOLBYEX" and 18 decimal places.

### Contract Structure

- `totalSupply`: An unsigned integer that stores the total supply of SOLBYEX tokens.
- `balanceOf`: A mapping that keeps track of the balance of tokens for each Ethereum address.
- `allowance`: A nested mapping that allows an address to spend tokens on behalf of another address.
- `name`: A string representing the name of the token.
- `symbol`: A string representing the symbol of the token.
- `decimals`: An unsigned 8-bit integer representing the number of decimal places used in token values.

### Events

The contract defines two events:

1. `Transfer`: This event is emitted whenever tokens are transferred from one address to another. It logs the sender's address, the recipient's address, and the number of tokens transferred.
2. `Approval`: This event is emitted when an owner approves another address to spend a certain number of tokens on their behalf. It logs the owner's address, the spender's address, and the approved amount.

### Functions

The ERC20 contract includes several important functions:

- `transfer`: Allows an address to send tokens to another address. It deducts the specified amount from the sender's balance and adds it to the recipient's balance.
- `approve`: Enables an owner to approve another address to spend a specified amount of tokens on their behalf.
- `transferFrom`: Allows a spender to transfer tokens on behalf of the owner, given the owner has approved the spender. It also reduces the allowance of the spender accordingly.
- `mint`: Allows an address to create and add new tokens to the total supply. This is commonly used for token issuance or initial distribution.
- `burn`: Allows an address to destroy and remove tokens from the total supply. This is often used for token redemption or burning.

## Vault.sol

The Vault.sol smart contract is designed to manage a token vault for the SOLBYEX token. It interacts with the ERC20 token using the IERC20 interface to provide deposit and withdrawal functionality for users while minting and burning shares.

### Contract Structure

- `token`: An immutable reference to the ERC20 token contract (implementing the IERC20 interface) that this vault manages.
- `totalSupply`: An unsigned integer representing the total supply of shares within the vault.
- `balanceOf`: A mapping that keeps track of the number of shares each Ethereum address holds in the vault.

### Functions

- `constructor`: Initializes the Vault contract with a reference to the ERC20 token.
- `deposit`: Allows users to deposit SOLBYEX tokens into the vault. The number of shares minted is determined based on the amount of tokens deposited, and these shares are then credited to the user.
- `withdraw`: Allows users to withdraw tokens from the vault by burning a specified number of shares. The corresponding amount of tokens is returned to the user.

### Minting and Burning Shares

The `deposit` and `withdraw` functions involve the minting and burning of shares, respectively. The formula used for minting shares is based on the proportion of tokens deposited in relation to the current total token balance in the vault. Similarly, the burning of shares results in the user receiving a proportionate amount of tokens based on the shares they burn.

This contract simplifies the process of depositing and withdrawing tokens while managing the underlying shares efficiently.

Please note that while this code provides a basic implementation of an ERC-20 token and a vault for managing those tokens, it is essential to consider potential security, gas optimization, and additional features when developing production-ready smart contracts.
