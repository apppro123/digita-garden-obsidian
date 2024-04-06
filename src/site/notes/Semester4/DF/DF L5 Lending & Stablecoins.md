---
{"dg-publish":true,"permalink":"/semester4/df/df-l5-lending-and-stablecoins/"}
---


- added multiple things in [[Semester4/DF/DF Definitions\|DF Definitions]]
## How economic machine works
#video [How The Economic Machine Works by Ray Dalio](https://www.youtube.com/watch?v=PHe0bXAIuk0)
- **Transaction**: money, credit <=> goods, services, financial assets
	- transactions **drive economy**
	- needs buyers and sellers
- **special actors**
	- central bank: 
		- can print money
		- sets interest rates
	- state: greatest buyer
- **credit**
	- most important part bc. biggest and **most volatile** part
	- needs lenders and borrowers
		- principal: amount lend
		- interest: additional amount to pay back for principal
	- debt is created with it
	- credit creates spending => drive economy
	- **without** credit: growth can just come from more productivity
	- **with** credit: growth can come from more productivity and more spending through borrowing/credit => creates cycle
	- **bad** when it supports overconsumption and cannot be paid bad e.g. big TV
	- **good** when it efficiently allocates resources e.g. tractor to harvest more crops
- **economic growth** due to cycle of: (more) income => borrowing => spending => productivity => ...
- **inflation** when prices rise
	- too much inflation causes problems => central bank rises interest rates => fewer people can borrow money => borrow less => less spending => prices go down => deflation => recession => decrease interest rates => more borrowing => inflation => ...
- **deflation** when prices decrease
- **deleveraging**
	- worse than recession bc. lowering interest rates doesn't work (not rly. possible to go under 0%)
	- beautiful deleveraging through properly applying counter actions => debt declines same as income
		- deflationary (cut spending and dept + redistribution) and inflationary (printing money) actions are in balance
		- income needs to grow faster than debt grows => people are creditworthy again
		- growth is slow but debt shrinks
	- possible counter actions
		- **cut spending**: has opposite effects bc. less spending => less income (for another person) => lower wages and unemployment => can pay back less
			- and lenders notice that borrowers probably cannot pay back everything => don't lend anything anymore
		- **cut dept**
			- lenders don't want that and "alternatives" are: less paid back, over longer time frame, reduced interest rate
			- also deflationary bc. everything loses value and so borrowers still, also with less debt, won't have enough to pay back (even less)
		- **redistribution**: government has to pay for unemployment and want's to set economic stimulus => needs more money generally tries to raise taxes for wealthy (bc. wealth is concentrated), but wealthy don't like that too much...
			- revolution/class conflict evolves => maybe army and/or (strong) political change e.g. Hitler after 1930s in Germany
		- **print money**: last alternative bc. interest rates are already lowered as much as possible
			- inflationary and stimulates economy
			- to buy financial assets and government bonds
				- just helps those who own financial assets bc. central bank can only buy financial assets
			- central bank can cooperate with central government through buying government bonds to spend money on goods and services => money for people
				- very risky
			- doesn't have to result in inflation, when credit shrinks the same amount and thus spending is not higher
	- **reflation** (after deleveraging) 
		- ca. 7-10 year (lost decade) (maybe just after a "beatauiful" deleveraging)
### Lecture (graphics)
- effects one-by-one ![Pasted image 20240323152523.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323152523.png)
- effects combined ![Pasted image 20240323152543.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323152543.png)
## Lending
### On-Chain lending & borrowing
- ![Pasted image 20240323152612.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323152612.png)
### Flash loan
- flash loan should be taken and repaid in one single transaction ![Pasted image 20240323154417.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323154417.png)
	- not directly time bound rather has to happen within one block building process
	- if it cannot be paid back => entire transaction is invalid
		- lender is secure
#### Use cases
- DeFi attacks
	- price oracle manipulation
	- pump and dump (buy another coin to make them look like as more valuable/have more transactions for a short amount of time)
- (risk-free) arbitrage
- washtrading
- flash mining
- collateral swapping ![Pasted image 20240405230801.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405230801.png)
- liquidation
	- when liquidator doesn't have cryptocurrency upfront to repay
	- only works when liquidation completes in one transaction
	- e.g. ![Pasted image 20240405231019.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405231019.png) ![Pasted image 20240405231027.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405231027.png)![Pasted image 20240405231038.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405231038.png)
## Liquidation
### in traditional finance ![Pasted image 20240405231219.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405231219.png)
- pass resolution for voluntary liquidation can be done by board of executives
- administration of liquidation are e.g. the not paid electricity bills
- **takes a long time** maybe even years
### Fixed spread liquidation
- can be completed in **1 transaction** 
- **repays debts** of borrowing position
- acquires collateral at a **discounted price** from the position in return
	- typically discounts are e.g. 5-15% (called **fixed spread**) in Aave ( #disclaimerN probably meant average with it)
- ![Pasted image 20240405231741.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405231741.png)
- price oracles for getting prices: on and off chain oracles possible/depending on currency

## Quiz
- How long does a flash loan last?
	- During one block
	- During one transaction \[correct]
	- From transaction signature until the transaction is mined
	- as long as you want
- What is TRUE?
	- Liquidations are typically done optimally.
	- The close factor is the minimum proportion of debt that can be repaid in a liquidation. \[false bc. it's the maximum proportion... and you can also liquidate less]
	- A flash loan has no fees
	- Transaction fees for a flash loan are on the order of 100 USD, even if the loan amounts can grow beyond 1B USD. \[correct]
- What can flash loans be used for?
	- Washtrading \[correct]
	- pumping a coin \[false bc. you can just do pumping and dumping together, not individually]
	- dumping a coin
	- forking a blockchain
- Which of the following liquidation strategies best describes an optimal fixed spread liquidation strategy?
	- the liquidation first performs an oracle price update, and then atomically performs the liquidation
	- the liquidator liquidates the position up to the close factor (when the close factor drops below 1, the position becomes available for liquidation)
	- perform two liquidations. The first one keeps the close factor below 1, such that the second liquidation can also successfully execute \[correct ]
	- perform three liquidations, two keeping the CF below 1, while the last one also successfully executes
- We define a borrowing position as a bad debt if it is financially rational for neither the borrowers nor the lending platform to close the position. Which of the following is not a cause for bad debt?
	- if the collateral value falls below the value of the debt.
	- if the value of excess asset used for over-liquidation cannot cover the liquidation transaction fee. 
	- if the debt has not been repaid for a long time. \[correct bc. time component has no impact on bad dept]
	- if the value of the debt grows more than the value of the collateral.