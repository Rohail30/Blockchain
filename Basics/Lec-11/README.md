```contract lecture12{
    mapping (address => uint) public balance;
    function addBalance(uint amount) public   {
        balance[msg.sender] = amount;
    }
}

contract lecture12{
    mapping (address => uint) public balance;
    function addBalance() public payable  {
        balance[msg.sender] = msg.value;
    }
}

msg value is a global value which holds ether
payable gets modified so that it can accept ether values

contract lecture12{

    mapping (address => uint) public balance;
    mapping (address => uint) public counter;
    uint count;
    address owner = msg.sender;
    modifier onlyOwner(){
        require(msg.sender == owner,"Not an Owner");
        _;
    }

    function addBalance() public payable  {
        balance[msg.sender] = msg.value;
        counter[msg.sender] = count++;
    }

    function getCounter(address add) public view onlyOwner returns(uint) {
        return counter[add];
    }
}

mappiny modifier require

contract lecture12{

    mapping (address => uint) public balance;
    mapping (address => uint) public counter;
    uint count;
    address owner = msg.sender;
    uint public contractBalance;

    modifier onlyOwner(){
        require(msg.sender == owner,"Not an Owner");
        _;
    }

    function addBalance() public payable  {
        require(msg.value >= 2 ether, "incuffient payment");
        require( contractBalance <= 10 ether,"limit Reached");
        balance[msg.sender] = msg.value;
        counter[msg.sender] = count++;
        contractBalance = address(this).balance;
    }

    function getCounter(address add) public view onlyOwner returns(uint) {
        return counter[add];
    }

```
// mappiny modifier require

contract lecture12{

    mapping (address => uint) public balance;
    mapping (address => uint) public counter;
    uint count;
    address owner = msg.sender;
    uint public contractBalance;

    // modifier onlyOwner(){
    //     require(msg.sender == owner,"Not an Owner");
    //     _;
    // }

    // function addBalance() public payable  {
    //     require(msg.value >= 2 ether, "incuffient payment");
    //     require( contractBalance <= 10 ether,"limit Reached");
    //     balance[msg.sender] = msg.value;
    //     counter[msg.sender] = count++;
    //     contractBalance = address(this).balance;
    // }

    // function getCounter(address add) public view onlyOwner returns(uint) {
    //     return counter[add];
    // }

    function deposit(uint amount) public {
        balance[msg.sender] = amount;
    }
    function transfer(address sender,address receiver,uint amount)public {
        require(amount <= balance[sender],"lower balance");
        balance[sender] -=amount;
        balance[receiver] +=amount;

    }
}

