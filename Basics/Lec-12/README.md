
// contract lecture13{
//     uint public  a;
//     uint public b;
//     event inc(address wallet, uint _a,string message);
//     constructor(uint _b){
//         b = _b;
//     }
//     // receive() external payable {
//     //     increment();
//     //  }
//      function increment() public {
//         a++;
//         emit inc(msg.sender,a,"done");
//      }
// }

// contract lecture13{
//     mapping(address => uint256) public balances;
//     mapping(address => uint256) public lockTimestamp;
   
    
//     function deposit() public payable {
//         balances[msg.sender] += msg.value;
//         lockTimestamp[msg.sender] = block.timestamp;
        
//     }

//     function withdraw() public {
//         require(balances[msg.sender] > 0, "No balance to withdraw");
//         require(block.timestamp >= lockTimestamp[msg.sender] + 5, "Funds are locked");
        
//         payable(msg.sender).transfer(balances[msg.sender]);
//         balances[msg.sender] = 0;
//         lockTimestamp[msg.sender] = 0;
     
//     }
// }


pragma solidity ^0.8.0;

contract HotelSystem {
    bool public roomAvailable;
    uint256 public pricePerDay;
    address public guest=msg.sender;
    uint256 public reservationDays;

    constructor(uint256 _pricePerDay) {
        roomAvailable = true;
        pricePerDay = _pricePerDay;
    }

    function reserveRoom(uint256 _reservationDays) public payable {
        require(roomAvailable, "Room not available");
        uint256 totalCost = _reservationDays * pricePerDay;
        require(msg.value >= totalCost, "Insufficient payment");

        roomAvailable = false;
        guest = msg.sender;
        reservationDays = _reservationDays;

        // Refund excess payment
        if (msg.value > totalCost) {
            payable(msg.sender).transfer(msg.value - totalCost);
        }
    }
}
