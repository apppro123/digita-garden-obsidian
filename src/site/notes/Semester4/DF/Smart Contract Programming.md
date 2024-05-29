---
{"dg-publish":true,"permalink":"/semester4/df/smart-contract-programming/"}
---

## Ethereum
- **content**: address, balance, code, memory on the VM
- **transactions**
	- **direct transfer of Ether**: sender, receiver, amount/Ether, maybe some input (text saved to the blockchain), signed with private key of sender, gas price
		- to contracts: sender, receiver = contract address, amount/Ether, signed with private key of sender, gas price
	- **contract creation**: sender, receiver = 0x0..0, amound/Ether, input = code of the contract being created (bytecode), signed with the private key of the sender, gas price => creates new address for contract and stores code, memory, money at that address
	- **contract function call**: sender, receiver = contract address, possible some amount/Ether, input = functionName(input1, input2, ...), signed with private key of sender, gas price
### Solidity
- object(contract)-oriented language
- constructor function
#### Variables
- **visibility**: public, private
- **types**: int, uint, bytes32, string, address (20 bytes long)
	- arrays e.g. `uint[] public integers;`
		- insert item `integers.push(0);`
		- access item `integers[1];`
		- get length: `integers.length;`
	- structure e.g. `struct Point {uint x; uint y;}`
		- initialise `Point public origin = Point(0,1);
	- Tuples e.g. `(uint x, uint y) = (1,2);`
	- Enum for associating a number to a string e.g. `enum Directions { Top, Right, Bottom, Left }` where `uint(Directions.Top) == 0`
	- mapping is like a table but index can be any built-in type `mapping(builtin_type => value_type)` e.g. `mapping(address => uint) public ledger;`
		- accessing and writing is similar to an array `ledger[key];` and `ledger[key] = value;`
- **declaration**: `<type> <visibility> <name> = <value>;
#### Functions
- **visibility**: public, private, external (function can just be called from outside, not inside of contract), internal (not exposed to outside of contract, similar to private but differ in inheritance)
- **state mutability**: view (if function doesn't modify state), pure (if function doesn't modify nor access variables)
- **require** keyword allows to make assertion and if they fail, execution is stopped and contract state is restored `require(<boolean expression="">);`
- **modifier** is a pretreatment applied to a function code
```Solidity
// formal syntax
modifier <name>([arg1, arg2, ...]) {
  [require(<e>);]* // all the requirements

  _; // means that the function code will be inserted here

  // I didn't write anything here, but in the future you might see some useful applications
}

// example
modifier securityCheck(bytes32 _password) {
  require(_password == "Super Super Muffin");
  _;
}

function eat(bytes32 _password) public securityCheck(_password) {
  bite = bite + 1;
}
```
- **declaration**: `function <name> ([arg1, arg2, ...]) <visibility> [mutability] [modifier1, modifier2, ...] [returns ([ret1, ret2, ...])] ;`
```Solidity
pragma solidity
{ #0}
.4.24;

contract PichuMuffin {
  uint public fans = 0;

  // Now you know that this function is really simple
  function like() public {
    fans = fans + 1;
  }

  // welcome back, old friend
  function isBestMuffin() public pure returns (bool) {
    return true;
  }
  
  // I've already made this function for you ;)
  function notZero(uint number) internal pure returns (bool) {
    return number != 0;
  }
  
  // This function returns a boolean
  function isRecommended() public view returns (bool) {
    return ;
  }
}
```
#### objects
- **msg** stores information about caller/sender e.g. `msg.value` is amount of currency that was sent
- **address** e.g.
```Solidity
address a = 0x0
uint balanceA = a.balance
```