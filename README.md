# FunctionAndErrors

## Description

This contract demonstrates the usage of `require()`, `assert()`, and `revert()` statements for error handling.

### Requirements

- Contract successfully uses `require()`
- Contract successfully uses `assert()`
- Contract successfully uses `revert()` statements

### Functionality

#### `requireExample(uint256 _value) : uint256`

- This function checks whether the input `_value` is less than or equal to 120 using `require()`.
- If the condition is met, it returns the input value; otherwise, it reverts with an error message.

#### `assertExample() : uint256`

- This function calculates the sum of `x` and `y` and asserts that the result equals 125 using `assert()`.
- If the assertion fails, the transaction reverts.

#### `revertExample() : uint256`

- This function performs division and reverts the transaction if the denominator is zero.
- It demonstrates the usage of `revert()` to trigger a revert with a custom error message.

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

contract FunctionAndErrors {
    // State variables
    uint256 public x = 120;
    uint256 public y = 5;

    // Function to check and return input value if less than or equal to 20
    function requireExample(uint256 _value) public pure returns (uint256) {
        require(_value <= 120, "Input value must be less than or equal to 120");
        return _value;
    }

    // Function to calculate sum of two state variables and ensure it equals 25
    function assertExample() public view returns (uint256) {
        uint256 result = x + y;
        assert(result == 125);
        return result;
    }

    // Function to perform division and revert transaction if denominator is zero
    function revertExample() public pure returns (uint256) {
        uint256 a = 120;
        uint256 b = 0;
        if (b == 0) {
            revert("Value must be non-zero");
        }
        return a / b;
    }
}

```

This is the whole functionality within the code itself and the generalization of how the code will run.

### Authors

Wee, Jencen M. 
8212778@ntc.edu.ph
