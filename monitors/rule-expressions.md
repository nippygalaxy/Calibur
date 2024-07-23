# Rule Expressions

## Supported Variables

* Parameters of the monitored event or function (only supports parameters that appear in the selected event or function)
  * Note: Parameters include anonymous parameters, i.e., parameters in functions or events without parameter names, mainly seen in function return values or event parameters.
  * In this system, anonymous function inputs or event parameters are represented as $arg\[idx], where idx is the index position of the parameter, starting from 0; anonymous function return values are represented as $out\[idx]. This notation is only applicable to parameters without parameter names and cannot be used for parameters with names.
  * For example, if a function is defined as function fa(int8, int8 a, int8 b, int8) public returns (int8, int8) (this function is only for illustrative purposes, generally there are no cases of missing parameter names), then the parameter before input a and the parameter after b can be represented as $arg0 and $arg3 respectively, while the return values can be represented as $out0 and $out1.
* Variables related to the storage of the monitored contract (supports private variables of the contract)
* Variables related to transactions
  * '`$status`': (Boolean type) The execution status of the transaction
  * '`$from`': (Address type) The initiator of the transaction
  * '`$to`': (Address type) The recipient of the transaction (the address of the contract being called or EOA)
  * '`$nonce`': (Integer) The nonce of the transaction initiator's account
  * '`$gas_limit`': (Integer) The gas limit of the transaction
  * '`$gas_used`': (Integer) The gas used in the transaction
  * '`$gas_price`': (Integer) The gas price of the transaction (wei)
  * '`$value`': (Integer) The value of the transaction (wei)
  * '`$max_fee_per_gas`': (Integer) The maximum gas price willing to be paid in an EIP1559 transaction (wei)
  * '`$max_priority_fee_per_gas`': (Integer) The maximum gas price that can exceed the base fee in an EIP1559 transaction (wei)
*   Variables related to specific calls in function calls (limited to function call types)

    * '`$$status`': (Boolean type) The status of the internal transaction
    * '`$$type`':
    * '`$$from`': (Address type) The initiator of the internal transaction
    * '`$$to`': (Address type) The recipient of the internal transaction (the address of the contract being called or EOA)
    * '`$$value`': (Integer) The value of the internal transaction (wei)
    * '`$$gas_limit`': (Integer) The gas limit of the internal transaction
    * '`$$gas_used`': (Integer) The gas used in the internal transaction



## Built-in system functions

'`balanceOf(addr)`': Returns the balance of Native Token for a specified address, in wei.

* If the current transaction is in pending status, then balanceOf gets the balance based on the previous block;
* If the current transaction is in executed status, then it gets the balance based on the current block;
* Where 'addr' can be a variable of address type or a literal.



## Supported Operators

* Address type (address)
  * Supports "==" and "!=".
  * Address type literals in expressions need to be enclosed in single ('') or double ("") quotes, for example: "0x6eaee1475603aa4fa240fc311857819abac02e12" != add1.
  * Addresses do not need checksum.
* Boolean type (bool)
  * Supports "==" and "!=".
  * Boolean type literals are true or false, for example: a != true.
* Integer type (int\* | uint\*)
  * Supports "+", "-", "\*", "/", ">", "<", ">=", "<=", "==", "!=".
  * Supports decimal and hexadecimal.
  * In decimal form, supports scientific notation (1e18) and power notation (10\*\*18).
* Floating-point type
  * Supports "+", "-", "\*", "/", ">", "<", ">=", "<=", "==", "!=".
  * Only supports decimal.
  * Supports scientific notation (1.1e10), but does not support power notation.
  * Floating-point types may have precision loss issues.

## Expression Standards

* The expressions supported by the system must result in a Boolean value. That is, the expression must contain at least one relational operator (">", "<", ">=", "<=", "==", "!="). Expressions like a + b are not valid in this system.
* Expressions support the connection of multiple relational expressions through logical operators ("&&", "and", "||", "or").
* Each expression must contain at least one parameter variable, system built-in variable, or system built-in function. Expressions composed purely of literals, like 1 + 2 == 3, are not valid in this system.
* All parameters, variables, functions, and logical operators are case-sensitive, such as and, or, true, false must all be lowercase.

## Example Expressions&#x20;

Here are some examples of valid expressions:

```
balanceOf("0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045") >= 1e18
```

```
10**19 >= balance0f($from）&& balance0f($from) >= 1018
```

```
( _amount > 1e19 and $status == false ) or ( _amount > 1e18 and $status == true )
```

```
_amount <= $value and $status == true
```
