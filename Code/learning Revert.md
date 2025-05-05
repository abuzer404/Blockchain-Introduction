'''Constructor Revert.
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    constructor() payable {
        require(msg.value >= 1 ether, "Must deposit at least 1 Ether");
    }

    receive() external payable {}
}

===========================

''' Only owner

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Contract {
    address public owner;

    constructor() payable {
        owner = msg.sender;
    }

    function withdraw() public {
        require(msg.sender == owner, "Only owner can withdraw");
        payable(owner).transfer(address(this).balance);
    }
}

================

''' Owner Modifier

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Contract {
    uint public a; // slot 0
    uint public b; // slot 1
    uint public c; // slot 2

    address public owner; // slot 3

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner");
        _;
    }

    constructor() {
        owner = msg.sender;
    }

    function setA(uint _a) public onlyOwner {
        a = _a;
    }

    function setB(uint _b) public onlyOwner {
        b = _b;
    }

    function setC(uint _c) public onlyOwner {
        c = _c;
    }
}
