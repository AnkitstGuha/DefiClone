# DefiClone

# ERC20 and Vault Smart Contracts

This repository contains two Solidity smart contracts: `ERC20` and `Vault`. The `ERC20` contract implements a basic ERC20 token, while the `Vault` contract allows users to deposit and withdraw these tokens in exchange for shares.

## Contracts

### ERC20.sol

The `ERC20` contract implements the ERC20 token standard with basic functionality including minting and burning of tokens.

#### Features

- **Minting:** Allows users to mint new tokens.
- **Burning:** Allows users to burn their tokens.
- **Transfer:** Allows users to transfer tokens between addresses.
- **Approval and TransferFrom:** Implements the standard ERC20 approval mechanism for delegated transfers.

#### Functions

- `transfer(address recipient, uint amount)`: Transfers tokens from the sender to the recipient.
- `approve(address spender, uint amount)`: Approves a spender to spend a specified amount of tokens on behalf of the sender.
- `transferFrom(address sender, address recipient, uint amount)`: Transfers tokens from a sender to a recipient using an approved allowance.
- `mint(uint amount)`: Mints new tokens and assigns them to the sender.
- `burn(uint amount)`: Burns tokens from the sender's balance.

### Vault.sol

The `Vault` contract allows users to deposit ERC20 tokens into the vault in exchange for shares and withdraw tokens by burning shares.

#### Features

- **Deposit:** Allows users to deposit ERC20 tokens and mint vault shares based on the amount of tokens deposited.
- **Withdraw:** Allows users to withdraw ERC20 tokens by burning vault shares.

#### Functions

- `deposit(uint _amount)`: Deposits tokens into the vault and mints shares.
- `withdraw(uint _shares)`: Withdraws tokens from the vault by burning shares.

## Deployment on Avalanche Subnet

Avalanche Subnets are customizable blockchain networks that run on the Avalanche platform. You can deploy these smart contracts on an Avalanche Subnet by following these steps:

### Prerequisites

1. **Avalanche C-Chain Node**: Set up an Avalanche C-Chain node or use an Avalanche provider service.
2. **Avalanche Development Tools**: Install tools like Hardhat or Truffle for smart contract deployment.
3. **Metamask**: Install Metamask and configure it to connect to the Avalanche network.

### Deployment Steps

1. **Compile Contracts:**

   Ensure you have the Solidity compiler installed. Use Hardhat or Truffle to compile your smart contracts:

```bash
   npx hardhat compile
 ```
```bash
// scripts/deployERC20.js
async function main() {
    const [deployer] = await ethers.getSigners();
    console.log("Deploying contracts with the account:", deployer.address);

    const ERC20 = await ethers.getContractFactory("ERC20");
    const erc20 = await ERC20.deploy();
    console.log("ERC20 contract deployed to:", erc20.address);
}

main().catch((error) => {
    console.error(error);
    process.exitCode = 1;
});
```
npx hardhat run scripts/deployERC20.js --network avalanche

### Usage
#### Minting and Burning Tokens:

- Interact with the ERC20 contract to mint and burn tokens. Use the contract functions via a web interface or through a script.

#### Depositing and Withdrawing Tokens:

- Use the Vault contract to deposit tokens and receive shares, or withdraw tokens by burning shares.
