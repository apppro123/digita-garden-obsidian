---
{"dg-publish":true,"permalink":"/semester4/df/lectures/df-l10/"}
---

## Decentralised Finance security
- multiple layers can be affected ![Pasted image 20240516183831.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516183831.png)
- e.g. sandwich attacks against taker ![Pasted image 20240516184053.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516184053.png)
### Attacker
- for attacker (to see transactions earlier) on a P2P network it's better to ![Pasted image 20240516184219.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516184219.png)
	- be closer (physically) to victim
	- wallet provider
- accelerated & front-run attacks ![Pasted image 20240516184421.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516184421.png)
- but attackers are quite vulnerable (when transactions are not executed atomically) bc. if these transactions are not executed in this order, the attack fails
### attack
- **attack lifecycle** ![Pasted image 20240516185402.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516185402.png)
### Defense
- incident response time (of whitehat hackers) are still very slow ![Pasted image 20240516185630.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516185630.png)
- in some protocols, it's possible to trigger emergency pauses => would be good to do these automatic e.g. on the basis of analysis
	- here some bytecode similarity analysis on adversarial/victim contracts ![Pasted image 20240516185806.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516185806.png)
## Random
- probably ETH community aggreed that white hat hacker gets around 10% of bounty
- DeFi-attacks make around 1000M+ USD/year
- arbitrage, liquidation, sandwich attacks make around 500M USD/year
- research on (preventing) attacks is quite different of  different layers ![Pasted image 20240516185309.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516185309.png)
- **misbehaving** of nodes **loses** them
	- in proof of work: investments made in electricity (don't earn anything)
	- in proof of stake: investments made in tokens
- if network merge (e.g. a computer runs two blockchains) it's possible to define that they always loose the "bigger"/more valuable token ![Pasted image 20240516190746.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240516190746.png)
## Staking
- **liquid staking**
	1. Send tokens to LST smart contract (Lido, RocketPool) and get LST in return (stETH, rETH)
	2. LST smart contract will stake on Ethereum and anoint operators from its “blessed pool”
	3. Blessed operators run Ethereum nodes with the stake from step #2
	4. Ethereum rewards are given back to LST smart contract (Ethereum doesn’t know about actual stakers)
	5. LST smart contract gives rewards back to stakers
- **liquid restaking**
	1. Enter Liquid Restaking Tokens (Ether.fi, Puffer, KelpDAO, RIO, Renzo, Inception, Swell)
	2. Restaking smart contract will stake on EigenLayer and anoint operators from its “blessed pool”
	3. Blessed operators run AVS nodes with the stake from step #2
	4. AVS rewards are given back to restaking smart contract (AVS’s doesn’t know about actual restakers)
	5. LRT smart contract gives rewards back to restakers
## Platypus
- privacy-preserving central bank digital currency
- no blockchain
### Requirements
- **privacy**: anonymous sender, recipient, private amount
- **scalability**: throughput, latency, light clients
- **regulation**: e.g. anonymous receiving limits ($10k per month)
#### Examples ![Pasted image 20240528122945.png](/img/user/Semester4/DF/Lectures/attachments/Pasted%20image%2020240528122945.png)
- Zcash (2014): strong privacy (e.g. zero-knowledge proofs for show correctness of payments), but bad scalability due to client side computation and download
- E-cash (1983): good scalability, but limited privacy
### What does platypus do (better)?
- **zero-knowledge proofs**: proof a statement regarding a secret without revealing the secret
- **commitments**: commit to a value and hen reveal value
	- binding: once committed, value cannot be changed
	- hiding: commitment doesn't reveal the value
	- publish both committed value and blinding factor -> verification
- **central unit** (e.g. CB) can then verify and proof such transactions (with **privacy** in mind) where
	- sender, recipient, value are hidden e.g. bc. content doesn't reveal it and serial number is pseudorandomly chosen
	- but transaction is unlinkable
- **scalability** bc. 
	- bank: little computations and can be parallelised (care when multiple users interact with one entry, but nothing new compared to other databases)
	- user: just need to state things over own balance
### guest lecturer argument on central bank digital currencies
where bad = false/bad argument and fair = true/some truth in argument
- Against
	- Big brother money”, tool of mass surveillance (bad)
	- Perfect way to conduct crime, launder money (bad)
	- High complexity, difficult to implement, communicate to the public (fair)
	- Current payments and financial system work — “if not broken, don’t fix it” (fair)
- In support
	- Sovereign solution for central banks (fair)
	- Improved payment privacy for users, less fees for merchants (fair)
	- Financial innovation, e.g., “programmable money” (?)
## Quiz
- What are all the actions that a P2P attacker can do against a P2P transaction?
	- front-run
	- back-run
	- front- and back-run \[correct]
	- nothing
- What are all the actions that a P2P attacker can do against a PBS transaction?
	- front-run
	- back-run \[correct]
	- front- and back-run 
	- nothing
- How much USD is lost to DeFi attacks every year (in M USD)?
	- 1'000