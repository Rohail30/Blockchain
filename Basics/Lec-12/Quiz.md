#### Function Syntax:
```solidity
function getInt() public view returns (int256) {
        return value;
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
```
#### function modifiers
- **View:** do not modify the state but can read the state
- **Pure:** do not read or modify the state

#### access specifiers / visibility specifiers

#### Array Syntax:
```solidity
   function printArray() public pure returns (uint256[] memory) {
        uint256[] memory arr = new uint256[](5);    //Creating an array of size 5

        for (uint256 i = 0; i < 5; i++) {   //Assigning values to the array
            arr[i] = i;
        }

        return arr;
    }

```

#### Transaction Syntax:
```solidity
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
```



