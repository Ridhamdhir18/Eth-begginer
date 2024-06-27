# Eth-begginer
for meta
# MyToken Smart Contract

## Overview

The `MyToken` contract is an implementation of a simple ERC-20 like token on the Ethereum blockchain. It allows the creation (minting) and destruction (burning) of tokens, and it keeps track of token balances for each address.

## Requirements

1. **Public Variables:**
   - `tokenName`: A string storing the name of the token.
   - `tokenAbbrv`: A string storing the abbreviation of the token.
   - `totalSupply`: An unsigned integer storing the total supply of tokens.

2. **Mapping:**
   - `accounts`: A mapping from addresses to account balances (`address => uint`).

3. **Mint Function:**
   - A function named `mintToken` that takes an address and a value. This function increases the total supply by the given value and also increases the balance of the specified address by that amount.

4. **Burn Function:**
   - A function named `burnToken` that takes an address and a value. This function decreases the total supply by the given value and also decreases the balance of the specified address by that amount.
   - The function includes a conditional check to ensure that the balance of the specified address is greater than or equal to the value to be burned.

## Contract Details

### Public Variables

- `tokenName`: Stores the name of the token ("Majestic Coin").
- `tokenAbbrv`: Stores the abbreviation of the token ("MC").
- `totalSupply`: Stores the total supply of tokens, initialized to 0.

### Mapping

- `accounts`: Maps each address to its corresponding token balance.

### Mint Function

```solidity
function mintToken(address _address, uint256 _value) public {
    totalSupply += _value;
    accounts[_address] += _value;
}
```
- Increases the `totalSupply` by the specified `_value`.
- Increases the balance of the specified `_address` by the specified `_value`.

### Burn Function

```solidity
function burnToken(address _address, uint256 _value) public {
    if (accounts[_address] >= _value) {
        totalSupply -= _value;
        accounts[_address] -= _value;
    }
}
```
- Decreases the `totalSupply` by the specified `_value`.
- Decreases the balance of the specified `_address` by the specified `_value`, only if the address has enough tokens to burn.

## Usage

To use this contract, deploy it on an Ethereum network. You can then interact with the public variables and functions using a web3 interface or any Ethereum wallet that supports smart contracts.

### Example Interactions

- **Minting Tokens:**
  Call the `mintToken` function with the desired address and value to mint new tokens.

- **Burning Tokens:**
  Call the `burnToken` function with the desired address and value to burn existing tokens, provided the address has enough tokens to burn.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
