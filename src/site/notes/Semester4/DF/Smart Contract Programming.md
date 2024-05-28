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
- public, private