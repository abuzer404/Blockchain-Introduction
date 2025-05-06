// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Ownable {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner {
        require(msg.sender == owner, "Only owner can call this function");
        _;
    }
}

contract Transferable is Ownable {
    function transfer(address newOwner) external onlyOwner {
        require(newOwner != address(0), "Invalid new owner address");
        Ownable.owner = newOwner;
    }
}