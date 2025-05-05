# Mappings 

Mappings are one of the most important and frequently used data types in Solidity. They allow you to store and retrieve values associated with unique keys, similar to hash maps or dictionaries in other languages.

#### Syntax

```solidity
mapping(KeyType => ValueType) myMapping;
```

* `KeyType` must be a value type like `uint`, `address`, or `bool`. Complex types such as arrays, mappings, or structs cannot be used as keys.
* `ValueType` can be any type, including structs and other mappings.

#### Key Points

* Mappings are not iterable, meaning you cannot loop through them or retrieve all keys.
* All possible keys exist by default and return the default value of the value type.
* Mappings are commonly used for:

  * Tracking user balances: `mapping(address => uint)`
  * Managing permissions: `mapping(address => bool)`
  * Recording votes: `mapping(address => Vote)`

#### Example

```solidity
mapping(address => bool) public isMember;

function addMember(address _addr) external {
    isMember[_addr] = true;
}
```

This example demonstrates how to mark an address as a member using a mapping.

Mappings provide an efficient way to associate and access data by key, making them essential for many smart contract applications.
