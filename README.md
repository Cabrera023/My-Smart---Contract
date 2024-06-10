# My-Smart---Contract
# Description 
It is feasible to implement comparable or identical contracts on both Ethereum and Avalanche because of the EVM compatibility. Assets can travel between Ethereum and Avalanche with the help of bridging technologies like Avalanche Bridge (AB), giving dApps smooth compatibility. Smart Contract Management for ETH (Ethereum) and AVAX (Avalanche) involves handling, deploying, interacting, and managing smart contracts on these blockchain platforms.

# Overview of Smart Contract Management
Smart contract management includes several key activities
* Development - writing the Solidity-based smart contract code
* Deployment - Deploying the smart contract to the blockchain
* Interaction - Engaging with the deployed contract (for example, reading information, carrying out operations)
* Maintenance - Monitoring and updating the contract, taking care of any problems or updates

 # Code Preview
 // SPDX-License-Identifier: UNLICENSED

pragma solidity ^0.8.9;

contract Assessment {

address payable public owner;

uint256 public balance;
 event Deposit(uint256 amount);
event Withdraw(uint256 amount);

constructor(uint initBalance) payable {
    owner = payable(msg.sender);
    balance = initBalance;
}

function getBalance() public view returns(uint256){
    return balance;
}

function deposit(uint256 _amount) public payable {
    uint _previousBalance = balance;

    require(msg.sender == owner, "You are not the owner of this account");

    balance += _amount;
    assert(balance == _previousBalance + _amount);
    emit Deposit(_amount);
}
error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

function withdraw(uint256 _withdrawAmount) public {
    require(msg.sender == owner, "You are not the owner of this account");
    uint _previousBalance = balance;
    if (balance < _withdrawAmount) {
        revert InsufficientBalance({
            balance: balance,
            withdrawAmount: _withdrawAmount
        });
    }
    balance -= _withdrawAmount;
    assert(balance == (_previousBalance - _withdrawAmount));
    emit Withdraw(_withdrawAmount);
}
}

# Author
Michaela Ariane B. Cabrera 
8214136@ntc.edu.ph
