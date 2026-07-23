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

### Adding Pause

```solidity
function updateData(...) public whenNotPaused {
    // normal logic
}

### Pause Events

```solidity
event Paused(address account);
event Unpaused(address account);

### View Functions

```solidity
function getData() public view returns (string memory) {
    return data;
}

function getOwner() public view returns (address) {
    return owner;
}

### Receive Function

```solidity
receive() external payable {
    emit Received(msg.sender, msg.value);
}

event Received(address sender, uint256 value);

### Fallback Function

```solidity
fallback() external payable {
    emit Fallback(msg.sender, msg.value);
}

event Fallback(address sender, uint256 value);

### supportsInterface

```markdown
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Renounce Ownership

```solidity
function renounceOwnership() public onlyOwner {
    owner = address(0);
}

### Version Tracking

```solidity
string public version = "1.0";

function getVersion() public view returns (string memory) {
    return version;
}

### isOwner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### Get Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Owner Function

```solidity
function getOwner() public view returns (address) {
    return owner;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Version Function

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public view returns (string memory) {
    return version;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}
