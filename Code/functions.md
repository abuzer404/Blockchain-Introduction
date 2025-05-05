// SPDX-License-Identifier: MIT
"""Arguments
pragma solidity ^0.8.0;

contract Contract {
    uint public x;

    constructor(uint _initialX) {
        x = _initialX;
    }
}

-----
""" increement
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    uint public x;

    constructor(uint _initialX) {
        x = _initialX;
    }

    function increment() external {
        x = x + 1;
    }
}

------------
'''VIEW ADDITION
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    uint public x;

    constructor(uint _initialX) {
        x = _initialX;
    }

    function increment() external {
        x = x + 1;
    }

    function add(uint _y) external view returns (uint) {
        return x + _y;
    }
}
======
DOUBLE OVERLOAD
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    function double(uint num) external pure returns (uint) {
        return num * 2;
    }

    function double(uint num1, uint num2) external pure returns (uint, uint) {
        return (num1 * 2, num2 * 2);
    }
}