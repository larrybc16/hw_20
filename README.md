# hw_20

pragma solidity ^0.5.0;

// lvl 1: equal split
contract AssociateProfitSplitter {
    // @TODO: Create three payable addresses representing `employee_one`, `employee_two` and `employee_three`.
    //creat 3 variables for each employee/their adress 
    
    address payable public employee_one;
    address payable public employee_two;
    address payable public employee_three;
    
    constructor(address payable _one, address payable _two, address payable _three) public {
        employee_one = _one;
        employee_two = _two;
        employee_three = _three;
    }

    function balance() public view returns(uint) {
        return address(this).balance;
    }

    function deposit() public payable {
        // @TODO: Split `msg.value` into three
        uint amount = msg.value/3; // Your code here! (balance value)

        employee_one.transfer(amount);
        employee_two.transfer(amount);
        employee_three.transfer(amount);
    
        // @TODO: Transfer the amount to each employee
        // Your code here!
    
        // @TODO: take care of a potential remainder by sending back to HR (`msg.sender`)
        // Your code here!
        msg.sender.transfer(msg.value-amount*3);
    }

  
        // @TODO: Enforce that the `deposit` function is called in the fallback function!
        // Your code here!
        
    
    function() external payable{
        deposit();
    }
}
