// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BasicDataTypesExample {
    // Boolean type
    bool public isActive = true;

    // Signed integer type
    int public signedNumber = -42;

    // Unsigned integer type
    uint public unsignedNumber = 100;

    // Address type
    address public owner = msg.sender;

    // String type
    string public greeting = "Welcome to Solidity!";

    // Bytes type (fixed size)
    bytes32 public fixedData = "SolidityBytes";

    // Dynamic bytes array
    bytes public dynamicData = "Hello";
} 

'''exercises


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Contract {
	bool public a = true;
    bool public b = false;
}
// unsigned integer
pragma solidity ^0.8.20;

contract Contract {
    uint8 public a = 200;
    uint16 public b = 300;
    uint256 public sum = a + b;
}

'''String literals
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract { // Renamed the contract to 'Contract'
    // Store "Hello World" in a bytes32 variable
    bytes32 public msg1 = "Hello World";

    // Store a longer string in a string variable
    string public msg2 = "This is a longer string that definitely requires more than 32 bytes to store.";
}

'''Enum

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Contract {
    enum Foods {
        Injera,
        Tibs,
        Shiro,
        Gomen
    }

    Foods public food1 = Foods.Injera;
    Foods public food2 = Foods.Tibs;
    Foods public food3 = Foods.Shiro;
    Foods public food4 = Foods.Gomen;
}