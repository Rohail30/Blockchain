**J-09:**
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

**J-10:**
Array, receive, accept and withdraw
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

**J-11:**
Enum, Mapping, struct
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

- Lecture_09
- Data Types
- Variables
- Functions
- Operators
- Task (Calculator)
- Lecture_10
- Arrays
- Msg Object
- Payable Function
- Lecture_11
- Enum and Struct
- Mapping
- Task (Book Issue)
- Lecture_12
- Modifier
- Task (Bank)
- Lecture_13
- Constructor
- Events
- recieve() function
- Task (Locking Tokens)

## Solidity Basic Syntax and Explanation

## Version Pragma
Specifies the Solidity compiler version.
```solidity
pragma solidity ^0.8.0;
```
**Explanation:** This line ensures that the contract is compiled with a compatible version of the Solidity compiler, in this case, any version starting from 0.8.0.

## Contract Declaration
Defines a new contract.
```solidity
contract MyContract {
    // State variables, functions, etc.
}
```
**Explanation:** This is how you declare a new contract in Solidity. The contract can contain state variables, functions, and other contract-related elements.

## State Variables
Permanent storage in the contract.
```solidity
contract MyContract {
    uint public count;
}
```
**Explanation:** State variables are stored on the blockchain. The `public` keyword automatically creates a getter function for the `count` variable.

## Functions
Executable units of code within a contract.
```solidity
contract MyContract {
    uint public count;

    function increment() public {
        count += 1;
    }

    function getCount() public view returns (uint) {
        return count;
    }
}
```
**Explanation:** Functions contain the logic of the contract. The `increment` function increases the `count` by 1, and `getCount` returns the current value of `count`. The `public` keyword makes these functions accessible externally.

## Arrays
Dynamic and fixed-size arrays.
```solidity
contract MyContract {
    uint[] public numbers; // Dynamic array
    uint[10] public fixedNumbers; // Fixed-size array

    function addNumber(uint _number) public {
        numbers.push(_number); // Push to array
    }

    function removeLastNumber() public {
        numbers.pop(); // Pop from array
    }

    function getNumber(uint _index) public view returns (uint) {
        return numbers[_index];
    }
}
```
**Explanation:** Arrays store lists of elements. `numbers` is a dynamic array that can grow or shrink, while `fixedNumbers` has a fixed size. The `push` method adds an element to the end of a dynamic array, and `pop` removes the last element.

## Mapping
Key-value store.
```solidity
contract MyContract {
    mapping(address => uint) public balances;

    function updateBalance(address _address, uint _amount) public {
        balances[_address] = _amount;
    }

    function getBalance(address _address) public view returns (uint) {
        return balances[_address];
    }
}
```
**Explanation:** Mappings are used for key-value storage. Here, `balances` maps addresses to unsigned integers. The `updateBalance` function updates the balance for a given address, and `getBalance` returns the balance of a given address.

## Enum
User-defined type with a set of named values.
```solidity
contract MyContract {
    enum Status { Pending, Active, Inactive }

    Status public status;

    function setStatus(Status _status) public {
        status = _status;
    }

    function getStatus() public view returns (Status) {
        return status;
    }
}
```
**Explanation:** Enums are custom data types with a finite set of values. Here, `Status` can be `Pending`, `Active`, or `Inactive`. The `setStatus` function sets the status, and `getStatus` returns the current status.

## Events
Logging events on the blockchain.
```solidity
contract MyContract {
    event CountIncremented(uint newCount);

    uint public count;

    function increment() public {
        count += 1;
        emit CountIncremented(count);
    }
}
```
**Explanation:** Events are used for logging on the blockchain. The `CountIncremented` event is emitted whenever the `count` is incremented, allowing external applications to listen for this event.

## Structs
Custom data types.
```solidity
contract MyContract {
    struct Person {
        string name;
        uint age;
    }

    Person[] public people;

    function addPerson(string memory _name, uint _age) public {
        people.push(Person(_name, _age));
    }

    function getPerson(uint _index) public view returns (string memory, uint) {
        Person storage person = people[_index];
        return (person.name, person.age);
    }
}
```
**Explanation:** Structs allow you to define custom data types. Here, `Person` has `name` and `age` properties. The `addPerson` function adds a new person to the `people` array, and `getPerson` retrieves a person's details by index.

## Voting

```solidity
pragma solidity ^0.8.0;

contract Voting {
    // Structure to represent a voter
    struct Voter {
        bool voted;  // if true, that person has already voted
        uint vote;   // index of the voted proposal
    }

    // Structure to represent a proposal
    struct Proposal {
        string name;   // short name of the proposal
        uint voteCount; // number of accumulated votes
    }

    address public chairperson;
    mapping(address => Voter) public voters;
    Proposal[] public proposals;

    // Constructor to create a new voting contract
    constructor(string[] memory proposalNames) {
        chairperson = msg.sender;
        for (uint i = 0; i < proposalNames.length; i++) {
            proposals.push(Proposal({
                name: proposalNames[i],
                voteCount: 0
            }));
        }
    }

    // Function to give the right to vote to an address
    function giveRightToVote(address voter) public {
        require(
            msg.sender == chairperson,
            "Only chairperson can give right to vote."
        );
        require(
            !voters[voter].voted,
            "The voter already voted."
        );
        voters[voter].voted = false;
    }

    // Function to cast a vote for a proposal
    function vote(uint proposalIndex) public {
        Voter storage sender = voters[msg.sender];
        require(!sender.voted, "Already voted.");
        require(proposalIndex < proposals.length, "Invalid proposal index.");

        sender.voted = true;
        sender.vote = proposalIndex;

        proposals[proposalIndex].voteCount += 1;
    }

    // Function to get the winning proposal index
    function winningProposal() public view returns (uint winningProposalIndex) {
        uint winningVoteCount = 0;
        for (uint i = 0; i < proposals.length; i++) {
            if (proposals[i].voteCount > winningVoteCount) {
                winningVoteCount = proposals[i].voteCount;
                winningProposalIndex = i;
            }
        }
    }

    // Function to get the name of the winning proposal
    function winnerName() public view returns (string memory winnerName_) {
        winnerName_ = proposals[winningProposal()].name;
    }
}

```
**Explanation:** This complete example integrates all the elements discussed. It includes state variables, an enum, a struct, mappings, events, and functions. The `onlyOwner` modifier ensures that certain functions can only be called by the contract owner.



















