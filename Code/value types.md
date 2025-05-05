// 1. uint (Unsigned Integer)
pragma solidity ^0.8.0;

contract ValueTypes {
    uint public positiveNumber;

    // Set an unsigned integer value
    function setPositiveNumber(uint _num) public {
        positiveNumber = _num;
    }

    // Get the unsigned integer value
    function getPositiveNumber() public view returns (uint) {
        return positiveNumber;
    }
}

// 2. int (Signed Integer)
pragma solidity ^0.8.0;

contract ValueTypes {
    int public balance;

    // Set a signed integer value
    function setBalance(int _balance) public {
        balance = _balance;
    }

    // Get the signed integer value
    function getBalance() public view returns (int) {
        return balance;
    }
}

// 3. bool (Boolean)
pragma solidity ^0.8.0;

contract ValueTypes {
    bool public isActive;

    // Set a boolean value
    function setActive(bool _status) public {
        isActive = _status;
    }

    // Get the boolean value
    function getActiveStatus() public view returns (bool) {
        return isActive;
    }
}

// 4. enum (Enumerated Type)
pragma solidity ^0.8.0;

contract ValueTypes {
    enum Status { Pending, Active, Inactive }

    Status public currentStatus;

    // Set an enum value
    function setStatus(Status _status) public {
        currentStatus = _status;
    }

    // Get the current status
    function getStatus() public view returns (Status) {
        return currentStatus;
    }
}
