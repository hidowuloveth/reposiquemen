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

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
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

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Receive Function

```solidity
receive() external payable {
    emit Received(msg.sender, msg.value);
}

event Received(address sender, uint256 value);

### Renounce Ownership

```solidity
function renounceOwnership() public onlyOwner {
    owner = address(0);
}

### Unpause Function

```solidity
function unpause() public onlyOwner {
    paused = false;
}

### Deposit Event

```solidity
event Deposited(address indexed user, uint256 amount);

function deposit() public payable {
    balances[msg.sender] += msg.value;
    emit Deposited(msg.sender, msg.value);
}

### Get User Balance

```solidity
function getUserBalance(address user) public view returns (uint256) {
    return balances[user];
}

### Deposit with Event and Limit

```solidity
event Deposit(address indexed user, uint256 amount);

function deposit() public payable {
    require(msg.value <= maxDeposit, "Too high");
    balances[msg.sender] += msg.value;
    emit Deposit(msg.sender, msg.value);
}

### Min and Max Deposit Checks

```solidity
function deposit() public payable {
    require(msg.value >= minDeposit, "Too low");
    require(msg.value <= maxDeposit, "Too high");
    balances[msg.sender] += msg.value;
}

### Owner Reset Cooldown

```solidity
function resetCooldown(address user) public onlyOwner {
    lastDeposit[user] = 0;
}

### Pause Status Event

```solidity
event DepositsPauseChanged(bool isPaused);

function toggleDepositsPause() public onlyOwner {
    depositsPaused = !depositsPaused;
    emit DepositsPauseChanged(depositsPaused);
}

### Blacklist Event

```solidity
event BlacklistUpdated(address indexed user, bool status);

function setBlacklist(address user, bool status) public onlyOwner {
    isBlacklisted[user] = status;
    emit BlacklistUpdated(user, status);
}

### Whitelist Event

```solidity
event WhitelistUpdated(address indexed user, bool status);

function setWhitelist(address user, bool status) public onlyOwner {
    isWhitelisted[user] = status;
    emit WhitelistUpdated(user, status);
}

### Fee Collected Tracking

```solidity
uint256 public totalFeesCollected;

function deposit() public payable {
    uint256 fee = (msg.value * depositFee) / 100;
    totalFeesCollected += fee;
    balances[msg.sender] += msg.value - fee;
}

### Total Fees from Withdraw

```solidity
function withdraw(uint256 amount) public {
    require(balances[msg.sender] >= amount, "Insufficient");
    uint256 fee = (amount * withdrawFee) / 100;
    totalFeesCollected += fee;
    balances[msg.sender] -= amount;
    payable(msg.sender).transfer(amount - fee);
}

### Fee Claim Event

```solidity
event FeesClaimed(address indexed owner, uint256 amount);

function claimFees() public onlyOwner {
    uint256 amount = totalFeesCollected;
    totalFeesCollected = 0;
    payable(owner).transfer(amount);
    emit FeesClaimed(owner, amount);
}

### Get Referrer

```solidity
function getReferrer(address user) public view returns (address) {
    return referrer[user];
}

### Get Pending Rewards

```solidity
function getPendingRewards(address user) public view returns (uint256) {
    return pendingReferralRewards[user];
}

### Total Referral Rewards Paid

```solidity
uint256 public totalReferralPaid;

function claimReferralRewards() public {
    uint256 reward = pendingReferralRewards[msg.sender];
    require(reward > 0, "No rewards");
    pendingReferralRewards[msg.sender] = 0;
    totalReferralPaid += reward;
    payable(msg.sender).transfer(reward);
}

### Referral Stats View

```solidity
function getReferralStats(address user) public view returns (uint256 count, uint256 pending) {
    return (referralCount[user], pendingReferralRewards[user]);
}

### Staking Reward Idea

```solidity
uint256 public rewardRate = 1; // example rate

function calculateReward(address user) public view returns (uint256) {
    uint256 timeStaked = block.timestamp - stakeTimestamp[user];
    return (stakedAmount[user] * rewardRate * timeStaked) / 1 days;
}

### Get Stake Info

```solidity
function getStakeInfo(address user) public view returns (uint256 amount, uint256 timestamp, uint256 pending) {
    return (stakedAmount[user], stakeTimestamp[user], pendingStakeRewards[user]);
}


### Lock Status View

```solidity
function isLocked(address user) public view returns (bool) {
    return block.timestamp < stakeTimestamp[user] + lockPeriod;
}


### Penalty Collected Tracking

```solidity
uint256 public totalPenaltiesCollected;

function unstake(uint256 amount) public {
    // ... existing logic
    if (penalty > 0) {
        totalPenaltiesCollected += penalty;
    }
}

### Get Compoundable Amount

```solidity
function getCompoundableAmount(address user) public view returns (uint256) {
    return calculateReward(user) + pendingStakeRewards[user];
}

### Get Total Staked

```solidity
function getTotalStaked() public view returns (uint256) {
    return totalStaked;
}

### Stake Event

```solidity
event Staked(address indexed user, uint256 amount);

function stake() public payable {
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
    emit Staked(msg.sender, msg.value);
}

### Reward Rate Event

```solidity
event RewardRateUpdated(uint256 newRate);

function setRewardRate(uint256 _rate) public onlyOwner {
    rewardRate = _rate;
    emit RewardRateUpdated(_rate);
}

### Combined Min and Max Stake Checks

```solidity
function stake() public payable {
    require(msg.value >= minStake, "Too low");
    require(stakedAmount[msg.sender] + msg.value <= maxStake, "Exceeds max");
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
}

### Get User Stake Stats

```solidity
function getUserStakeStats(address user) public view returns (uint256 amount, uint256 count, uint256 lastTime) {
    return (stakedAmount[user], stakeCount[user], lastStakeTime[user]);
}

### Staking Pause Event

```solidity
event StakingPauseChanged(bool isPaused);

function toggleStakingPause() public onlyOwner {
    stakingPaused = !stakingPaused;
    emit StakingPauseChanged(stakingPaused);
}

### Stake Blacklist Event

```solidity
event StakeBlacklistUpdated(address indexed user, bool status);

function setStakeBlacklist(address user, bool status) public onlyOwner {
    isStakeBlacklisted[user] = status;
    emit StakeBlacklistUpdated(user, status);
}

### Stake Whitelist Event

```solidity
event StakeWhitelistUpdated(address indexed user, bool status);

function setStakeWhitelist(address user, bool status) public onlyOwner {
    isStakeWhitelisted[user] = status;
    emit StakeWhitelistUpdated(user, status);
}

### Stake Fee Event

```solidity
event StakeFeeUpdated(uint256 newFee);

function setStakeFee(uint256 _fee) public onlyOwner {
    stakeFee = _fee;
    emit StakeFeeUpdated(_fee);
}

### Unstake Fee Event

```solidity
event UnstakeFeeUpdated(uint256 newFee);

function setUnstakeFee(uint256 _fee) public onlyOwner {
    unstakeFee = _fee;
    emit UnstakeFeeUpdated(_fee);
}

### Emergency Mode Flag

```solidity
bool public emergencyMode = false;

function setEmergencyMode(bool status) public onlyOwner {
    emergencyMode = status;
}

function emergencyWithdraw() public {
    require(emergencyMode, "Not in emergency");
    // existing withdraw logic
}
