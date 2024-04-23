```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

// 0.8.2 compatible with this version only
// ^0.8.2 compatible with this version and above
// >=0.8.2 <0.9.0 compatible with version greater than or equal to 0.8.2 and less than 0.9.0

contract Part_A {
    // State Variables (permanently stored in contract storage)
    // Data Types
    int256 value = -100; // int (int8 to int256)
    uint256 number = 10; // uint (uint8 to uint256)
    bool isTrue = true; // bool (true or false)
    string name = "Hello World"; // string (sequence of characters)
    bytes data = "hello-world"; // bytes (dynamically-sized byte sequence)
    address Address = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4; // address (20-byte value)

    // Modifiers
    // View: do not modify the state but can read the state
    // Pure: do not read or modify the state

    // Function to store a number
    function storeValue(uint256 num) public {
        number = num;
    }

    // Function to retrieve the stored number
    function getNumber() public view returns (uint256) {
        return number;
    }

    function getInt() public view returns (int256) {
        return value;
    }

    function getBool() public view returns (bool) {
        return isTrue;
    }

    function getString() public view returns (string memory) {
        return name;
    }

    function getBytes() public view returns (bytes memory) {
        return data; // Returns in bytes32 format
    }

    function getAddress() public view returns (address) {
        return Address; // Returns the address of the contract
    }

    // Function to get the balance of the contract
    function getBalance() public view returns (uint256) {
        return Address.balance; // Returns the balance of the contract
    }
}
```
