---
{"dg-publish":true,"permalink":"/semester4/df/lectures/df-l9-central-bank-digital-currencies/"}
---


- [To look at blockchains](https://etherscan.io)

- #remarkN probably not done in this lecture but don't remember when we've done it [[Semester4/DF/Decentralised autonomous organisation\|Decentralised autonomous organisation]]
## Central Bank Digital Currencies
#short CBDC
- Trends
	- digitalisation reduces cash demand
	- more DeFi (applications)
- possible actions by governments/central banks
	- regulation of privately issued digital currencies
	- introduction of a central bank digital currency
- forms of CBDC ![Pasted image 20240527115633.png](/img/user/Semester4/DF/Lectures/attachments/Pasted%20image%2020240527115633.png)
### Money
- #Def money from an economist's perspective: any (financial) asset that functions as unit of account, medium of exchange and store of value.
- public has access to two monies: cash and bank deposits
	- cash: issued by central bank ( #short CB), physical, legal tender, more private, created by CB
	- bank deposits: commercial banks, generally bear default risk of the issuing bank, digital, claim (against bank), generally subject to interest payments, created by commercial banks (mainly when granting loans)
### reserves
- CB provides banks with **electronic central bank money** so-called reserves
- used to **settle interbank deposit flows** which arise when depositors transfer their funds from one bank to another
- **wholesale CBDC** would essentially be a technologically advanced version of reserves
### retail CBDC
#short rCBDC
is an electronic form of the national currency available to the public
- available to everyone
- new: "digital cash"
	- physical cash can still exist
- **motivation**: different ones e.g. financial inclusion, payments efficiency, payments safety/robustness, financial stability
- potential **implications** where CB has to find out proper balance
	- economic efficiency: more efficient, robust payment system, higher financial inclusion, tighter competition by banks for deposits
	- financial stability: faster, more frequent bank runs, less risk-taking by banks, CBDC flows as financial stability indicator
	- monetary policy: direct interest rate pass-through to the real economy, bank disintermediation and/or increase in banks' funding costs
	- higher demand for domestic currency
- **design questions**
	- Access: Who can hold rCBDC?
	- Availability: How much can individual hold?
	- Remuneration (store of value): Interest on it and if so how?
	- payment functionalities (medium of exchange): What transactions are executable?
	- Privacy: What information can CB see?
	- Infrastructure: How is access provided by CB?
- monetary system with retail CBDC ![Pasted image 20240527115743.png](/img/user/Semester4/DF/Lectures/attachments/Pasted%20image%2020240527115743.png)
	- different types of CBDC (with multiple tiers) ![Pasted image 20240528081915.png](/img/user/Semester4/DF/Lectures/attachments/Pasted%20image%2020240528081915.png)
### wholesale CBDC
- only for financial institutions
- similar to current system as technologically advances reserves
- potentially enhances (cross-border) payments-efficiency
#### together with tokenised deposits
possible created of a "unified ledger"
- eliminates transaction risks (immediate final settlement)
- faster and cheaper (cross-border) transactions
- introduces programmable money ("smart contracts")
- less disruptive to today's system than a (full-scale) retail CBDC
### tokenised deposits
is a form of traditional bank deposits with rules (e.g. what asses can(not) do) and information (e.g. where it comes from, who owns it...)
### Distributed ledger technology
#short DLT
## Quiz
- What is the purpose of the SELFDESTRUCT opcode in the EVM?
	- to create a new smart contract
	- to call a function in another smart contract
	- to remove a smart contract and send its remaining balance to a designated address \[correct]
	- to pause the execution of a smart contract
- How do you hide smart contract calls in a transaction?
	- call functions with private modifiers only
	- call into the targeted smart contract from another smart contract (internal transaction)
	- use a public layer 2 system
	- not possible to hide \[correct]
- Which of the following is NOT a valid type in the EVM?
	- uint256
	- bytes32
	- string
	- float64 \[correct]
- What happens when a smart contract runs out of  gas during execution in the EVM?
	- transaction is reverted and the gas is refunded to the send
	- transaction is reverted but gas is consumed \[correct]
	- transaction continues executing with the remaining gas
	- transaction is put on hold until more gas is provided
- What is the maximum stack size of the EVM?
	- 1024 #remark like a normal stack of any programming language
- What is the target gas limit (unit of gas) for a block in the Ethereum EVM?
	- 15'000'000
- The voting power in most DAOs is controlled by how many addresses
	- 10isch \[correct]
	- 100isch
	- 1000isch
	- even more
- Accepted proposals in a DAO are always
	- executed immediately
	- executed fully on-chain
	- voted for by a majority of existing governance tokens 
	- none of the above \[correct]