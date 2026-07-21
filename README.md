# Base Exploration Repository

Starting my journey with Base (L2 by Coinbase).

This repo will contain notes, code examples, and resources as I learn about Layer 2 scaling, Solidity, and building on Base.

### Key Concepts

- Layer 2 scaling solutions
- Low gas fees compared to Ethereum mainnet
- Optimism Stack technology
- Developer-friendly environment

This repo will serve as my personal knowledge base.

### Setting Up Tools for Base

- MetaMask or Coinbase Wallet
- Remix IDE for quick testing
- Blockscout explorer
- Base network configuration

Ready to start writing and deploying code.

### Basic Storage Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleStorage {
    string public data = "Learning Base";

    function updateData(string memory newData) public {
        data = newData;
    }
}

### UI for SimpleStorage Contract

```html
<input id="inputData" placeholder="Enter new data" />
<button onclick="updateData()">Save</button>
<p>Stored: <span id="storedData"></span></p>

### Events in SimpleStorage

```solidity
event DataUpdated(address updater, string newData);

function updateData(string memory newData) public {
    data = newData;
    emit DataUpdated(msg.sender, newData);
}

### Listening to Data Updates

```javascript
contract.on("DataUpdated", (updater, newData) => {
  document.getElementById("storedData").innerText = newData;
});

### Owner Control

```solidity
function clearData() public onlyOwner {
    data = "";
}

### Ownership Transfer

```solidity
function transferOwnership(address newOwner) public onlyOwner {
    owner = newOwner;
}

### Ownership Event

```solidity
event OwnershipTransferred(address previousOwner, address newOwner);

function transferOwnership(address newOwner) public onlyOwner {
    emit OwnershipTransferred(owner, newOwner);
    owner = newOwner;
}
