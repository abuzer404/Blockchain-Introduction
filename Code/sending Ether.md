storing owner

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    address public owner;

    constructor() {
        owner = msg.sender;
    }
}

=================

''' Recieve Ether.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    receive() external payable {
        // This function is called when the contract receives Ether
        // without any calldata. You can add logic here if needed,
        // such as emitting an event.
    }
}
================
'''Tip Owner.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    receive() external payable {}

    function tip() public payable {
        (bool success, ) = owner.call{ value: msg.value }("");
        require(success, "Ether transfer failed");
    }
}

=================
'''Charity.

// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract Contract {
    address public owner;
    address public charityAddress;

    constructor(address _charityAddress) {
        owner = msg.sender;
        charityAddress = _charityAddress;
    }

    receive() external payable {
        // No specific action on receiving Ether, it just increases the contract balance.
    }

    function donate() public {
        uint contractBalance = address(this).balance;
        (bool success, ) = charityAddress.call{ value: contractBalance }("");
        require(success, "Donation failed");
    }
}
=================
'''Selfdestruct.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    address public owner;
    address public charityAddress;

    constructor(address _charityAddress) {
        owner = msg.sender;
        charityAddress = _charityAddress;
    }

    receive() external payable {}

    function donate() public {
        selfdestruct(payable(charityAddress));
    }
}