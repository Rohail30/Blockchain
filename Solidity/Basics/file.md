**J-09**
Variables and Function
```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

// 0.8.2 compatible with this version only
// ^0.8.2 compatible with this version and above
// >=0.8.2 <0.9.0 compatible with version greater than or equal to 0.8.2 and less than 0.9.0

contract Part_A {
    //State Variables (permanently stored in contract storage)
    //Data Types
    int256 value = -100; //int (int8 to int256)
    uint256 number = 10; //uint (uint8 to uint256)
    bool isTrue = true; //bool (true or false)
    string name = "Hello World"; //string (sequence of characters)
    bytes data = "hello-world"; //bytes (dynamically-sized byte sequence)
    address Address = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4; //address (20-byte value)

    //Modifiers
    //View: do not modify the state but can read the state
    //Pure: do not read or modify the state

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
        return data; //Returns in bytes32 format
    }

    function getAddress() public view returns (address) {
        return Address; //Returns the address of the contract
    }

    // Function to get the balance of the contract
    function getBalance() public view returns (uint256) {
        return Address.balance; //Returns the balance of the contract
    }
}
```
```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_B {
    int256 a;
    int256 b;

    function setA(int256 x) public {
        a = x;
    }

    function setB(int256 y) public {
        b = y;
    }

    function Addition() public view returns (int256) {
        return a + b;
    }

    function Subtraction() public view returns (int256) {
        return a - b;
    }

    function Multiplication() public view returns (int256) {
        return a * b;
    }

    function Division() public view returns (int256) {
        return a / b;   //return integer only (no decimal points)
    }

    function Modulus() public view returns (int256) {
        return a % b;
    }

    function IncrementA() public view returns (int256) {
        int256 x = a;
        return ++x;
    }

    function DecrementB() public view returns (int256) {
        int256 y = b;
        return --y;
    }

    function Comparison() public view returns (bool) {
        return a == b ? true : false;
    }
}
```
Array, receive, accept and withdraw
**J-10**

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

**J-11**

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_A {
    
    // Enum is a user-defined data type that consists of a constant value
    enum status {failed, average, passed}

    status s;

    function setStatus() public {
        s = status.passed;
    }

    function getStatus() public view returns (status) {
        return s;
    }

    // Mapping is used to store key-value pairs
    // mapping(keyType => valueType) variableName;
    mapping(address => uint) balances;

    function setBalance(uint value) public {
        balances[msg.sender] = value;
    }

    function getBalance(address addr) public view returns (uint) {
        return balances[addr];
    }
}
```

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_B {
    //Struct is a user-defined data type that groups related data together
    struct Student {
        string name;
        uint regNo;
        bool isPresent;
    }

    Student s; //Declaring a struct variable
    Student[] studentsArray; //Declaring an array of struct

    function setStudent() public {
        //Setting single student
        s = Student("Ali", 123, true);
    }

    function getStudent() public view returns (Student memory) {
        return s;
    }

    function addStudent(string memory _name, uint _regNo, bool _isPresent) public {
        studentsArray.push(Student(_name, _regNo, _isPresent)); //Setting multiple students
    }

    function getStudentArray() public view returns (Student[] memory) {
        return studentsArray;
    }
}
```

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_C {
    
    struct Book {
        uint bookId;
        address issuer;
        bool isIssued;
        uint issuedAt;
    }

    Book b;

    function issueBook(uint _bookId) public {
        b = Book(_bookId, msg.sender, true, block.timestamp);
    }

    function getBook() public view returns (Book memory) {
        return b;
    }

    function isFineApplicable() public view returns (bool) {
        return block.timestamp - b.issuedAt > 7 days; 
        //Accepted time units are seconds, minutes, hours, days, weeks
    }
}
```

**J-12**

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_A {
    mapping(address => uint256) public balance;
    mapping(address => uint256) public counter;
    uint256 count = 0;
    address owner = msg.sender;

    // modifier are used to check the conditions before executing the function
    modifier onlyOwner() {
        require(msg.sender == owner, "Only Owner can call this function");
        _; // this is used to execute the function
    }

    function addBalance() public payable {
        balance[msg.sender] += msg.value;
        counter[msg.sender] = ++count;
    }

    // modifier used in a function
    function getCounter(address add) public view onlyOwner returns (uint256) {
        return counter[add];
    }
}
```
```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_B {
    mapping(address => uint256) public balances;

    function deposit(uint256 amount) public payable {
        require(amount > 0, "Amount should be greater than 0");
        balances[msg.sender] += amount;
    }

    function withdraw(uint256 amount) public {
        require(amount > 0, "Amount should be greater than 0");
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
    }

    function getBalance() public view returns (uint256) {
        return balances[msg.sender];
    }

    function getBalance(address addr) public view returns (uint256) {
        return balances[addr];
    }

    function transfer(address reciever, uint256 amount) public payable {
        require(amount > 0, "Amount should be greater than 0");
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        balances[reciever] += amount;
    }
}
```

**J-13**

```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_A {
    uint256 public a;
    uint256 public b;

    // Creating an event to log the increment
    event inc(address wallet, uint256 _a, string message);

    // Constructor to initialize value before deployment
    constructor(uint256 _b) {
        b = _b;
    }

    receive() external payable {
        increment();
    }

    function increment() public {
        ++a;
        emit inc(msg.sender, a, "Incremented"); // Calling the event
    }
}
```
```solidity
// SPDX-License-Identifier: MIT

pragma solidity >=0.8.2 <0.9.0;

contract Part_B {
    mapping(address => uint256) public balances;
    mapping(address => uint256) public depositTimestamp;

    function deposit() public payable {
        balances[msg.sender] = msg.value;
        depositTimestamp[msg.sender] = block.timestamp;
    }

    function withdraw() public {
        require(balances[msg.sender] > 0, "No balance to withdraw");
        require(block.timestamp >= depositTimestamp[msg.sender] + 5, "Funds are locked");

        // payable(msg.sender).transfer(balances[msg.sender]);
        balances[msg.sender] = 0;
        depositTimestamp[msg.sender] = 0;
    }
}
```
















