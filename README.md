# Voting System Smart Contract 

This Solidity smart contract, named `VotingSystem`, is designed to create a basic voting system on the Ethereum blockchain.

## Description

This contract demonstrates the usage of `require()`, `assert()`, and `revert()` statements for error handling.

### Requirements

- Contract successfully uses `require()`
- Contract successfully uses `assert()`
- Contract successfully uses `revert()` statements

### Component and Functionality

`admin`: An address variable representing the administrator of the voting system.
`registeredVoters1`: A mapping that tracks whether a particular Ethereum address is registered as a voter.
`hasVoted`:  A mapping that tracks whether a registered voter has already cast their vote.
`votesReceived`: A mapping that keeps track of the number of votes received by each candidate.

### Events 

`VoterRegistered`: An event triggered when a new voter is registered.
`VoteCast`: An event triggered when a registered voter casts their vote for a candidate.

### Modifiers 

`onlyAdmin`: A modifier that restricts certain functions to be callable only by the contract's administrator.

### Functios
`registerVoter`: Allows the administrator to register a new voter by adding their address to the `registeredVoters` mapping.
`castVote`: Allows a registered voter to cast their vote for a specific candidate.
`getVoteCount`: Retrieves the number of votes received by a specific candidate.
`requireExample`, `assertExample`, `revertExample`: Example functions demonstrating the use of error handling mechanisms.

### Getting Started

To interact with this contract, you can deploy it on Remix Ethereum IDE or any Ethereum-compatible blockchain.
1. Open Remix Ethereum IDE.
2. Create a new file and paste the provided Solidity code.
3. Compile the code.
4. Deploy the contract.
5. Interact with the deployed contract by calling its functions.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VotingSystem {
    address public admin;
    mapping(address => bool) public registeredVoters;
    mapping(address => bool) public hasVoted;
    mapping(address => uint256) public votesReceived;

    event VoterRegistered(address indexed voter);
    event VoteCast(address indexed voter, address candidate);

    modifier onlyAdmin() {
        require(msg.sender == admin, "Only admin can perform this action");
        _;
    }

    constructor() {
        admin = msg.sender;
    }

    function registerVoter(address _voter) public onlyAdmin {
        require(!registeredVoters[_voter], "Voter already registered");
        registeredVoters[_voter] = true;
        emit VoterRegistered(_voter);
    }

    function castVote(address _candidate) public {
        require(registeredVoters[msg.sender], "You are not a registered voter");
        require(!hasVoted[msg.sender], "You have already cast your vote");
        require(_candidate != address(0), "Invalid candidate address");

        hasVoted[msg.sender] = true;
        votesReceived[_candidate]++;

        emit VoteCast(msg.sender, _candidate);
    }

    function getVoteCount(address _candidate) public view returns (uint256) {
        return votesReceived[_candidate];
    }

    function requireExample(uint256 _value) public pure returns (uint256) {
        require(_value > 0, "Value must be greater than zero");
        return _value;
    }

    function assertExample(uint256 _value) public pure returns (uint256) {
        uint256 result = _value * 2;
        assert(result >= _value); // Ensure no overflow
        return result;
    }

    function revertExample(uint256 _value) public pure returns (uint256) {
        if (_value == 0) {
            revert("Value cannot be zero");
        }
        return _value;
    }
}
```
This is the whole functionality within the code itself and the generalization of how the code will run.

### Authors

Wee, Jencen M. 
8212778@ntc.edu.ph
