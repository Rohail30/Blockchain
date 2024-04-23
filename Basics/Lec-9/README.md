## Solidty
This Solidity smart contract, named smartContract, provides functions for various purposes:

- `printString()`: Returns a string "Hello World".
- `mod(uint256 a, uint256 b)`: Computes the modulus of two unsigned integers.
- `compareInt(int256 a, int256 b)`: Compares two signed integers and returns a boolean result.
- `multipleReturns(int x, int y, int z)`: Returns three integers as multiple return values.
- `printArray()`: Creates and returns an array of unsigned integers.
- `acceptEthers()`: Allows the contract to accept incoming ether and transfers it to a predefined owner address.
- `withdrawEthers()`: Allows the contract owner to withdraw the contract's balance in ether.
- `getBalance()`: Returns the current balance of the contract in ether.

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract smartContract {
    function printString() public pure returns (string memory) {
        return "Hello World";
    }

    function mod(uint256 a, uint256 b) public pure returns (uint256) {
        return a % b;
    }

    //Cannot compare strings
    function compareInt(int256 a, int256 b) public pure returns (bool) {
        return a == b;
        // return a>b;
        // return a<b;
        // return a!=b;
    }

    function multipleReturns(int x, int y, int z) public pure returns (int, int, int)
    {
        return (x, y, z);
    }

    function printArray() public pure returns (uint256[] memory) {
        uint256[] memory arr = new uint256[](5);    //Creating an array of size 5

        for (uint256 i = 0; i < 5; i++) {   //Assigning values to the array
            arr[i] = i;
        }

        return arr;
    }

    function acceptEthers() public payable {
        address _owner = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4;
        payable(_owner).transfer(address(this).balance); //Transfer the ethers to the owner
    }

    function withdrawEthers() public {
        address owner = payable(msg.sender);
        payable(owner).transfer(address(this).balance);
    }

    function getBalance() public view returns (uint256) {
        return address(this).balance;
    }
}

```
