# Fixed Sum

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    function sum(uint256[5] memory arr) public pure returns (uint256) {
        uint256 total = 0;
        for (uint256 i = 0; i < arr.length; i++) {
            total += arr[i];
        }
        return total;
    }
}

# Dynamic sum

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    function sum(uint256[] memory arr) public pure returns (uint256) {
        uint256 total = 0;
        for (uint256 i = 0; i < arr.length; i++) {
            total += arr[i];
        }
        return total;
    }
}

# Filter to storage

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    uint256[] public evenNumbersStorage;

    function filterEven(uint256[] memory arr) public {
        delete evenNumbersStorage; // Clear previous values
        for (uint256 i = 0; i < arr.length; i++) {
            if (arr[i] % 2 == 0) {
                evenNumbersStorage.push(arr[i]);
            }
        }
    }
    

    function evenNumbers(uint256 index) public view returns (uint256) {
        return evenNumbersStorage[index]; // Will revert if index is out of bounds
    }
}

# Filter to memory

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    function filterEven(uint256[] memory arr) public pure returns (uint256[] memory) {
        uint256[] memory temp = new uint256[](arr.length);
        uint256 count = 0;

        for (uint256 i = 0; i < arr.length; i++) {
            if (arr[i] % 2 == 0) {
                temp[count] = arr[i];
                count++;
            }
        }

        // Create result array of correct size
        uint256[] memory result = new uint256[](count);
        for (uint256 i = 0; i < count; i++) {
            result[i] = temp[i];
        }

        return result;
    }
}

# Stack club

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract StackClub {
    mapping(address => bool) private members;

    function addMember(address _member) public {
        members[_member] = true;
    }

    function isMember(address _member) public view returns (bool) {
        return members[_member];
    }
}

