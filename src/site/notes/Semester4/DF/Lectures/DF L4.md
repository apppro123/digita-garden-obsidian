---
{"dg-publish":true,"permalink":"/semester4/df/lectures/df-l4/"}
---

## Decentralised Exchange
(Example LOB Dex)
- **(Dis) advantages**:
	- \+ No KYC/AML
	- \+ no fees paid to the exchange
	- \+ no impermanent loss
	- \- fees for deposit, withdraw, trade creation/cancel
	- \- slow execution
	- \- not fully decentralised (mediating server)
- trading **volume**: around 70 billion (recent months)
- **Why?** ![Pasted image 20240322154927.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240322154927.png)
### Systems Architecture ![Pasted image 20240322155034.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240322155034.png)
### Automated market maker
#short AMM
- **Liquidity pool** idea: Let a smart contract do the market making. ![Pasted image 20240322155519.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240322155519.png) **liquidity provider (LP)** token: ![Pasted image 20240322155644.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240322155644.png)
- **formula** $x*y=k$ where $x$ = asset X quantity, $y$ = asset Y quantity, $k$ = constant
- properties
	- instant liquidity, irrespective of the trade size
	- purchase of asset X increases price of X and decreases the price of Y
	- ratio of asset X and Y sets the price
	- known as constant product ( #short CP) AMM
- **(dis)advantages**
	- + no order book maintenance: but arbitrage required
	- + simple implementation for CP AMM: low gas costs
	- - danger of impermanent loss/coin de-peg: total loss of funds possible
	- - high slippage for low liquidity markets
	- - users vulnerable to sandwich attacks
- Example: ![Pasted image 20240322160005.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240322160005.png)
#### Slippage
- (un)expected **increase or decrease** in price based on trading volume and available liquidity
- effects
	- worse/better execution price
- possible to introduce a slippage protection by configuring a threshold to prevent unacceptable slippage
#### Impermanent loss ![Pasted image 20240322160344.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240322160344.png)
#short IL
- impermanent == not permanet: realised upon withdraw only
- can result in total loss
	- trading fees may compensate
	- liquidity mining may compensate
	- similar to a de-peg of stablecoin
#### Exchange Transaction propagation ![Pasted image 20240323083048.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323083048.png)
#### Stablecoin AMM pros/cons
- + better prices for bigger volumes i.e. more liquidity 
	- example shows significant differences among exchanges ![Pasted image 20240323084451.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323084451.png)
- - potentially higher gas costs
- - danger of a de-peg of a stablecoin
- pegged/stablecoin prices move in expectation together ![Pasted image 20240323084533.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323084533.png)
	- exchange rate should ideally remain 1:1
	- default CP AMM is not optimised for such cases
#### What if a coin gets
- **de-pug**
	- as bank run in CeFi: no money returned
	- "bank run" in DeFi
		- pool may get **blacklisted**
		- first come, first served
		- pool formula penalises destabilising a pool
		- increasingly worse price for late-comers
- **blacklisted**
	- e.g. USDT and USDC have built-in code to
		- blacklist addresses
		- destroy coins
		- e.g. USDT blacklisted 500+ accounts, destroyed 50M+ USDT
#### AMM arbitrage
- beginning: **multiple markets** with 
	- the **same assets** X and Y
	- **different prices** for X and Y
- prices are **synchronised** by "arbitrageurs"
	- they gain profit from price difference: also referred to as "spread"
	- requires to perform at least one transaction
- e.g. ![Pasted image 20240323085059.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323085059.png)
	- arbitrageur can also do it with a flash loan
- how to **detect** arbitrage/profitable opportunities?
	- Bellman Ford Algorithm
		- Negative cycle detection
		- Works among multiple markets
		- Used in traditional finance and DeFi
	- Theorem Solver (SMT tools aim to solve the satisfiability modulo theories ( #short SMT) problem)
		- Needs to encode the DeFi model
		- Apply heuristics for path pruning
## Sandwich attacks
1. P1 changes X to Y (value of X decreases and of Y increases)
2. P2 changes also X to Y (value of X decreases even more and of Y increases more)
3. P1 changes Y to X (gets more X out bc. Y is more valuable then before)
### protection
- **optimised trade execution**
	- \+ simple
	- \- limited scope
- **trusted third party ordering**
	- \+ efficient
	- \- no decentralisation
- **committee ordering**
	- \+ fairly efficient
	- \- reduced decentralisation
- **commit & reveal**
	- \+ secure
	- \- costly & delay
## Quiz
- Which of the following properties is NOT a desired property for AMM?
	- no pool fees \[correct bc. AMM pool should have some fees]
	- instant liquidity, irrespective of the trade size
	- purchase of an asset decreases the asset supply in AMM, and increases its market price
	- the expected increase or decrease in price is based on the trading volume and available liquidity
- Which of the following is a property for a typical on-chain order book?
	- no fees for order placements
	- front running resistance
	- impermanent loss \[there is no impermanent loss in an order book bc. market makers can fill the orders and thus liquidity cannot just be removed; this is rather in an AMM]
	- non-custodian ( #german Verwalter/Aufseher) settlement \[correct bc. swapping of assets is non-custodial meaning you own your coins with your private key, there is no custodian doing the settlement]
- Which of the following statements is incorrect
	- Unexpected slippage can only cause a worse execution price \[correct]
	- unexpected slippage is caused by price change after a trade has been broadcast but before it has been confirmed
	- trades can configure a slippage protection threshold to limit the total slippage (expected + unexpected)
	- The concept of slippage is typically unavoidable in financial markets
- What is TURE about impermanent loss?
	- impermanent loss cannot result in the total loss of funds.
	- Trading fees can never compensate the impermanent loss.
	- Impermanent loss is impermanent bc. it's only realised upon a withdrawal from a liquidity pool. \[correct]
	- Impermanent loss is only a fictive accounting phenomenon and never materialises in a loss.
- Back-running describes the process where an adversary attempts to execute its own transaction immediately after the victim's transaction executes. For example, given two exchange markets A and B, both trading ETH/USD at a price of 1000. If a victim's trad (with a as price of 100GWei) is expected to push exchange A's price to 1100 ETH/USD, the adversay can attempt to back-run the victim to perform arbitrage between A and Ab. Which of the following method will have the highest back-running success rate?
	- Broadcast the back-running transaction immediately after the victim's transaction with 99GWei
	- Broadcast the back-running transaction immediately after the victim's transaction, with 100GWei
	- Send a private back-running transaction to private relayer services, and bribe the miners to perform the back-run
	- (i) broadcast the back-running transaction immediately after the victim with 100GWei, and also (ii) send the transaction to private relayer services and bribe the miners \[correct]