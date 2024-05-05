# Solidity

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
