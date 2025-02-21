# 🚀 Crypto Savings Vault  

A simple Ethereum smart contract that allows users to **save and withdraw ETH**, keeping track of their balances securely on the blockchain.  

## 📌 Features  
- 📥 **Deposit ETH** securely into the vault  
- 💰 **Withdraw ETH** anytime  
- 📊 **Track your balance** easily  

## 🔗 Smart Contract Address  
`0xD034c429e80BB83bA1BF46bA77A518BE7460789a`  

## 🛠 How to Use  

### 1️⃣ Deposit ETH  
Send ETH to the contract using the `deposit()` function.  

### 2️⃣ Withdraw ETH  
Call the `withdraw()` function to retrieve your saved ETH.  

### 3️⃣ Check Balance  
Use `getBalance()` to see your stored ETH amount.  

## 📜 Smart Contract Code  
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SavingsVault {
    mapping(address => uint256) private balances;

    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }

    function withdraw() public {
        uint256 amount = balances[msg.sender];
        require(amount > 0, "No funds to withdraw");
        balances[msg.sender] = 0;
        payable(msg.sender).transfer(amount);
    }

    function getBalance() public view returns (uint256) {
        return balances[msg.sender];
    }
}
