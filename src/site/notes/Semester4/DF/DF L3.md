---
{"dg-publish":true,"permalink":"/semester4/df/df-l3/"}
---

## DF and CF ![Pasted image 20240312183404.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240312183404.png)
### DF stack![Pasted image 20240312183435.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240312183435.png)
- **Example** where smart contract on blockchain uses external data ![Pasted image 20240312183520.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240312183520.png)
## Oracle
- **Reasons** for need of oracles for blockchains
	- blockchain is isolated DB
	- blockchains lack
		- access to real-world data
		- no API-query possible
		- cannot browse the internet
- **Solution**: transactions
- **Defintion**
	- General: System that connects a blockchain with other systems.
	- Specific: Actors relaying data on-chain.
### Design
#### Challenges
- miners (provider of data) can lie/cheat
- network providing data for miners can lie/cheat
- source or oracle outage
=> have multiple miners and sources to prevent outage
=> have consensus so possibility of false data is minimised
## Censorship
- can happen on multiple layers e.g. application, transaction, consensus
### Tornados
- breaks connection to person who put it in => but observations/analysis of transaction can help with finding out who gave/took coins
### proposer/builder separation ![Pasted image 20240312184538.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240312184538.png)
### attack nodes who apply censorship
- for censorship, nodes have to put in work to extract information but then cannot do transactions and don't earn anything bc. transaction with a censored value is not allowed => DDoS attack possible to spam node with censored coins
## Quiz
- Which of the following DeFi applications is most likely to require external oracle data?
	- Token management contracts, such as ERC20
	- Betting on real world events \[correct]
	- Uniswap, Curve, and other Automated Market Maker Decentralised Exchanges
	- On-chain games that do not require randomness
- Is the context of blockchain oracles, which of the following statements is NOT TRUE?
	- Because block generation is centralised process, incorporating an oracle into the consensus protocol does not work because miners may lie or cheat.
	- Oracles have to receive very concise and short data representations to minimise blockchain fees.
	- For each oracle update, a minimum subset of all nodes in the oracle committee should send a report to the miner. \[correct bc. one node is enough]
	- Multiple sources /website (redundancy) are required due to website outages and data corruption possibilities
- What is the anonymity set of Tronado Cach pool with 1000 deposits
	- 100
	- 1000 \[correct]
	- 999
	- 1001
- What are the computational implications if a miner censors a transaction, what is correct?
	- No implication bc. the miner doesn't need to verify the transaction.
	- No implications bc. the miner doesn't need to execute the transaction.
	- The minder must spend computational resources to execute the transaction but cannot claim transaction fees. \[correct]
	- The miner must spend computational resources but is paid the regular transaction fees.
- Assumed an oracle committee has five nodes (A,B,C,D,E) and it's agreed to report the median value. Node E is a malicious node and E observes the following values from the other four nodes (A:1000, B: 1010, C: 1020, D: 1030). What are the upper and lower bounds of the aggregated value to which E can manipulate.
	- 1000 - 1005
	- 1010-1020 \[correct bc. median is middle number and you can choose a number between (including borders) 1010 to 1020 and it will be choosen]
	- 1000 - 1030
	- no upper/lower bounds