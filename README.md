# Solidity Smart Contracts - ERC20 Token and Vault

This repository contains two Solidity smart contracts: `ERC20` and `Vault`. The `ERC20` contract implements the ERC-20 token standard, allowing users to create and interact with tokens on the Ethereum blockchain. The `Vault` contract is used to deposit and withdraw ERC-20 tokens in a way that issues shares to users based on their deposit, and allows them to withdraw shares for an equivalent amount of tokens.

## Contents

- `ERC20` contract: A basic implementation of an ERC-20 token.
- `Vault` contract: A contract that allows users to deposit and withdraw tokens, issuing and burning shares accordingly.

## ERC20 Contract

The `ERC20` contract is a simple implementation of the ERC-20 standard with additional features for minting and burning tokens.

### Key Features:

- **Total Supply**: The total amount of tokens in circulation.
- **Balances**: Tracks the token balance for each address.
- **Allowances**: Allows token owners to approve a third party (spender) to transfer tokens on their behalf.
- **Minting**: Allows the contract owner to mint new tokens and increase the total supply.
- **Burning**: Allows users to burn their own tokens and decrease the total supply.

### Functions:

- **`transfer(address recipient, uint amount)`**: Transfers `amount` tokens from the caller's account to the recipient.
- **`approve(address spender, uint amount)`**: Approves the `spender` to transfer up to `amount` tokens on behalf of the caller.
- **`transferFrom(address sender, address recipient, uint amount)`**: Transfers `amount` tokens from `sender` to `recipient`, based on the caller's allowance.
- **`mint(uint amount)`**: Mints `amount` tokens to the caller's account, increasing the total supply.
- **`burn(uint amount)`**: Burns `amount` tokens from the caller's account, decreasing the total supply.

### Events:

- **Transfer**: Emitted when tokens are transferred between addresses.
- **Approval**: Emitted when an allowance is granted to a spender.

---

## Vault Contract

The `Vault` contract allows users to deposit and withdraw ERC-20 tokens, issuing shares in return. The amount of shares issued is proportional to the amount of tokens deposited. Similarly, when withdrawing, shares are burned and an equivalent amount of tokens is returned to the user.

### Key Features:

- **Deposits**: Users deposit tokens and receive shares in return. The number of shares is proportional to the amount of tokens being deposited.
- **Withdrawals**: Users can withdraw tokens based on the shares they hold. The number of tokens returned is proportional to the number of shares burned.
- **Shares Management**: The contract maintains the total supply of shares and the balance of shares for each user.

### Functions:

- **`deposit(uint _amount)`**: Allows the caller to deposit tokens into the vault. In return, the caller receives shares based on the amount of tokens deposited.
- **`withdraw(uint _shares)`**: Allows the caller to withdraw tokens from the vault by burning the equivalent number of shares.

### Internal Functions:

- **`_mint(address _to, uint _shares)`**: Mints new shares for the recipient.
- **`_burn(address _from, uint _shares)`**: Burns shares from the sender.

### Mathematical Formula for Deposit:

When depositing tokens, the number of shares issued is calculated using the following formula:

