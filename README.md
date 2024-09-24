# AVAX-PROOF-Advanced-Avalanche-Module-1
This repository contains two Solidity smart contracts:

1. **ERC20 Contract**: A basic ERC20 token implementation.
2. **Vault Contract**: A contract that allows users to deposit and withdraw ERC20 tokens while managing shares of the total supply in the vault.

## Contracts Overview

### 1. ERC20 Token Contract

The `ERC20` contract is a simplified implementation of the ERC20 token standard. It provides the core functionalities such as token transfers, approval, minting, and burning.

#### Features

- **Token Information**:
  - `name`: "DEFIEMP"
  - `symbol`: "DEF"
  - `decimals`: 18 (standard for ERC20 tokens)
  
- **Functions**:
  - `transfer(recipient, amount)`: Transfers tokens from the sender to the recipient.
  - `approve(owner, spender, amount)`: Approves a spender to spend a specific amount of tokens on behalf of the owner.
  - `transferFrom(sender, recipient, amount)`: Transfers tokens from one address to another, using the allowance mechanism.
  - `mint(amount)`: Mints new tokens to the caller's account.
  - `burn(amount)`: Burns tokens from the caller's account.

#### Events

- **Transfer**: Emitted on token transfers, including minting and burning.
- **Approval**: Emitted when an allowance is set via the `approve` function.

### 2. Vault Contract

The **Vault** contract is a smart contract built on Ethereum (or any EVM-compatible chain) that allows users to deposit ERC20 tokens and receive shares in return. These shares represent the user’s ownership of the tokens in the vault, and users can redeem their shares to withdraw their portion of the vault's assets.

## Features

- **Deposit Tokens**: Users can deposit ERC20 tokens into the vault and receive a proportional amount of shares in return.
- **Withdraw Tokens**: Users can burn their shares to withdraw a corresponding amount of tokens from the vault.
- **Share-based System**: The vault uses a share system to track the proportional ownership of each user relative to the total token balance in the vault.

## Mathematical Model

- **Deposit Formula**:
  - Shares minted (`s`) = `(amount * totalSupply) / token balance before deposit`
  - If the vault is empty (`totalSupply == 0`), shares minted are equal to the deposited amount.

- **Withdrawal Formula**:
  - Amount withdrawn (`a`) = `(shares * token balance before withdraw) / totalSupply`

## How It Works

1. **Install Avalanche CLI**
   - Install avalanche-cli on your UNIX system.
   - Copy ERC20.sol and Vault.sol from this repository.
   - Create you custom subnet on Ubuntu Terminal.
   - In a terminal, run: ```avalanche subnet create <any-subnet-name>```
   - Select the desired options , go with defaults if new.
   - Create chain ID (any positve digits).
   - Deploy you subnet using the command ```avalanche subnet deploy <your-subnet-name>```.
   - Details such as RPC URL , Funded address ,Network name, Chain ID ,Currency Symbol,private key will appear . Use these information to add a new network on Metamask .
   - Switch to the newly created network and import new account using the private key dispalyed in the network information box.

2. **Deploy Contract:**
   - In Remix IDE, select "Injected Web3" as the environment.
   - Deploy ```ERC20.sol``` first.
   - Then deploy ```Vault.sol```, using the deployed address of ```erc20.sol``` as the constructor parameter.

3. **Mint and Deposit Tokens:**
   - Mint some tokens to your address using the mint function in ```ERC20.sol```.
   - Deposit some tokens and receive shares in return using ```Vault.sol```.
  
   ## Author
Aashish Bhambri
## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
