# Arrays 

Arrays in Solidity are used to store collections of elements of the same data type. They are a fundamental data structure that lets you group and manage related values under one variable.

There are two types of arrays in Solidity:

1. **Fixed-size arrays** – have a predefined length and cannot grow or shrink.

   ```solidity
   uint[3] numbers = [1, 2, 3];
   ```

2. **Dynamic arrays** – can grow or shrink in size during runtime.

   ```solidity
   uint[] public values;
   ```

You can add elements to a dynamic array using `.push()`, access elements using an index (`values[0]`), and get the array's length with `.length`.

Arrays can be stored in **storage**, **memory**, or **calldata**, depending on use:

* **Storage**: Persistent between function calls.
* **Memory**: Temporary and cheaper, used in functions.
* **Calldata**: Read-only and used for external function inputs.

Arrays are powerful for managing lists of items like user addresses, balances, or records in contracts.


