# Voting System Smart Contract 

This Solidity smart contract, named `Voting`, is designed to manage the candidate setup for various positions in an election on the Ethereum blockchain.

## Description

This contract demonstrates the usage of `require()`, `assert()`, and `revert()` statements for error handling in the context of setting and validating candidate numbers for different election positions.

### Requirements

- Contract successfully uses `require()`.
- Contract successfully uses `assert()`.
- Contract successfully uses `revert()` statements.

### Components and Functionality

`presidentCandidates`: A uint256 variable representing the number of candidates for the president position.
`vicePresidentCandidates`: A uint256 variable representing the number of candidates for the vice president position.
`secretaryCandidates`: A uint256 variable representing the number of candidates for the secretary position.

### Functios

`requireCandidates`: Sets the number of candidates for each position and uses `require()` to ensure at least one candidate is set for any position.
`assertTotalCandidates`: Returns the total number of candidates and uses `assert()` to ensure the total number of candidates is greater than zero.
`revertIfNoCandidates`: Reverts the transaction if no candidates are set for any position.

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

contract Voting {
    uint256 public presidentCandidates;
    uint256 public vicePresidentCandidates;
    uint256 public secretaryCandidates;
    // Add other positions here if needed

    // Function to set the number of candidates for each position with a requirement
    function requireCandidates(uint256 _president, uint256 _vicePresident, uint256 _secretary) public {
        require(_president > 0 || _vicePresident > 0 || _secretary > 0, "Need at least 1 candidate");

        presidentCandidates = _president;
        vicePresidentCandidates = _vicePresident;
        secretaryCandidates = _secretary;
        // Add other positions here if needed
    }

    // Function to assert and return the total number of candidates
    function assertTotalCandidates() public view returns (uint256) {
        uint256 totalCandidates = presidentCandidates + vicePresidentCandidates + secretaryCandidates;
        // Add other positions here if needed
        assert(totalCandidates > 0);  // Ensure the total number of candidates is greater than 0
        return totalCandidates;
    }

    // Function to revert if no candidates are set
    function revertIfNoCandidates() public view {
        if (presidentCandidates == 0 && vicePresidentCandidates == 0 && secretaryCandidates == 0) {
            revert("Need at least 1 candidate");
        }
    }
}

```
This is the whole functionality within the code itself and the generalization of how the code will run.

### Authors

Wee, Jencen M. 
8212778@ntc.edu.ph
