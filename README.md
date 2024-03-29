# TX Origin: A Security Exploration in Ethereum Smart Contracts

Welcome to this project where we explore the security implications of using `tx.origin` in Ethereum smart contracts. We have two Solidity contracts (`Good.sol` and `Attack.sol`) and a test script that illustrates a potential security vulnerability when using `tx.origin` for authorization checks.

## 📘 Contract Details

- `Good.sol`: A straightforward contract with an `owner` state variable. The contract permits the owner to change the contract's ownership. However, it uses `tx.origin` for authorization, opening up a potential security loophole.

- `Attack.sol`: This contract is designed to exploit the `Good` contract's vulnerability. It contains an `attack` function that alters the `Good` contract's owner to the `Attack` contract itself.

## 🔬 Testing the Vulnerability

The test script (`test.js`) examines if the `Attack` contract can successfully alter the owner of the `Good` contract. The script:

- Deploys the `Good` contract.
- Deploys the `Attack` contract, with the `Good` contract's address as a constructor argument.
- Invokes the `attack` function of the `Attack` contract.
- Checks if the `Good` contract's owner is now the `Attack` contract.

## 🛠️ Requirements

- Node.js
- npm
- Hardhat
- ethers.js
- chai

## 🚀 Test Execution

1. Install dependencies using `npm install`.
2. Run tests with `npx hardhat test`.

## ⚠️ Security Advisory

The use of `tx.origin` for authorization checks can be risky, and it's generally safer to use `msg.sender` instead. The `Good` contract in this project intentionally includes this security flaw for demonstration purposes. Please refrain from using this contract in a production environment
