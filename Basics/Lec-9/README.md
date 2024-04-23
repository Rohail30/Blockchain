```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_A {
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
