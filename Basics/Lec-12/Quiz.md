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

| Specifier | Accessible Within Same Contract | Accessible in Derived Contracts | Accessible Externally (Transactions/Other Contracts) |
|-----------|----------------------------------|---------------------------------|------------------------------------------------------|
| public  | Yes                              | Yes                             | Yes                                                  |
| private | Yes                              | No                              | No                                                   |
| external| No                               | No                              | Yes                                                  |
| internal| Yes                              | Yes                             | No                                                   |


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

#### Enum Syntax:
In Solidity, an enum (short for enumeration) is a user-defined type that allows you to create a collection of named constants. Enums are typically used to define a variable that can take one of a predefined set of values, improving code readability and reducing the likelihood of invalid values being assigned.

```solidity        
    // Enum is a user-defined data type that consists of a constant value
    enum status {failed, average, passed}

    status s;

    function setStatus() public {
        s = status.passed;
    }

    function getStatus() public view returns (status) {
        return s;
    }
```
#### Mapping Syntax:
In Solidity, a mapping is a reference type that is used to store key-value pairs. It works similarly to hash tables or dictionaries in other programming languages.

```solidity        
    // Mapping is used to store key-value pairs
    // mapping(keyType => valueType) variableName;
    mapping(address => uint) balances;
```

#### Struct Synax:
```solidity        
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
```

#### Modifier Syntax:
```solidity        
    // modifier are used to check the conditions before executing the function
    modifier onlyOwner() {
        require(msg.sender == owner, "Only Owner can call this function");
        _; // this is used to execute the function
    }
```

#### Event Syntax:
```solidity        
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
```















