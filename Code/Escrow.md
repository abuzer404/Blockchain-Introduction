# Setup

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Escrow {
    address public arbiter;
    address public depositor;
    address public beneficiary;
}

# constructor

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Escrow {
    address public arbiter;
    address public depositor;
    address public beneficiary;

    constructor(address _arbiter, address _beneficiary) {
        arbiter = _arbiter;
        beneficiary = _beneficiary;
        depositor = msg.sender;
    }
}
# Funding

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Escrow {
    address public arbiter;
    address public depositor;
    address public beneficiary;

    constructor(address _arbiter, address _beneficiary) payable {
        arbiter = _arbiter;
        beneficiary = _beneficiary;
        depositor = msg.sender;
    }
}

# Approval

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Escrow {
    address public arbiter;
    address public depositor;
    address public beneficiary;

    constructor(address _arbiter, address _beneficiary) payable {
        arbiter = _arbiter;
        beneficiary = _beneficiary;
        depositor = msg.sender;
    }

    function approve() external {
        require(msg.sender == arbiter, "Only arbiter can approve");
        payable(beneficiary).transfer(address(this).balance);
    }
}

# Security

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Escrow {
    address public arbiter;
    address public depositor;
    address public beneficiary;

    constructor(address _arbiter, address _beneficiary) payable {
        arbiter = _arbiter;
        beneficiary = _beneficiary;
        depositor = msg.sender;
    }

    function approve() external {
        require(msg.sender == arbiter, "Only arbiter can approve");
        payable(beneficiary).transfer(address(this).balance);
    }
}

# Events

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Escrow {
    address public arbiter;
    address public depositor;
    address public beneficiary;

    event Approved(uint256 amount); // <-- Add this

    constructor(address _arbiter, address _beneficiary) payable {
        arbiter = _arbiter;
        beneficiary = _beneficiary;
        depositor = msg.sender;
    }

    function approve() external {
        require(msg.sender == arbiter, "Only arbiter can approve");
        uint256 balance = address(this).balance;
        payable(beneficiary).transfer(balance);
        emit Approved(balance); // <-- Emit here
    }
}
