# Constructor 

A **constructor** in Solidity is a special function that runs **only once**, when a contract is **deployed**. It is used to **initialize state variables** or set up access control (e.g., owner or initial members).

---

# Syntax

```solidity
constructor() {
    // initialization logic
}
```

---

# Key Points

* Runs **automatically** at deployment.
* Cannot be called again after deployment.
* Can be used to set the contract owner or initial values.
* Can accept parameters like a regular function.

---

# Example

```solidity
contract MyContract {
    address public owner;

    constructor() {
        owner = msg.sender; // sets the deployer as the owner
    }
}
```

---


