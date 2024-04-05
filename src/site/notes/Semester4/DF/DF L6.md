---
{"dg-publish":true,"permalink":"/semester4/df/df-l6/"}
---

## Economic models
- **represents** (often simplifies) an economic process
- **contains** [[Semester4/DF/DF L6#Variables\|#Variables]]
- logical/quantitative **relationships** between variables
- example: inflation
	- measuring inflation requires a behaviour model bc. it depends on behaviour of individuals e.g. what/how much food they buy => how money is used
	- differentiate relative vs. inflation price change
### Variables
- Interest rate(s) in CeFi and DeFi
- cryptocurrency price
- collateral ratio
- DeFi protocol fees
- blockchain transaction fees
- number of users
- blockchain transaction throughput
- ...
#### Exogenous vs. endogenous
- **Exogenous** variable == **outside** force
	- determined outside model, imposed on model
	- e.g. in MakerDAO, asset price of collateral (e.g. ETH), is independent of the MakerDAO system
- **Endogenous** variable == **inside** the model
## Stablecooins
### Types
- **Types**
	- **Reserved-based** e.g. USDC by a bank
	- **collateral-based**: e.g. MakerDAO
	- **algorithmic** e.g. AMPL
#### MakerDAO ![Pasted image 20240405232329.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405232329.png)
- to be profitable: assumption that ETH goes up and you can get even more with this DAI => with drawn DAI get even more ETH => later change back and have more in all
#### Ampleforth
#short AMPL
- ![Pasted image 20240405232646.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405232646.png)
- systemic implications
#### USDC and USDT
- destroys coins ![Pasted image 20240405232749.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405232749.png)
[[Semester4/DF/Decentralised Finance#Bank run\|Decentralised Finance#Bank run]]
## Quiz
- Which stable coin is the most stable? ( #remarkN atm)
	- USDC \[correct]
	- DAI
	- AMPL
	- ETH
- Which of the following statements is False?
	- Several algorithmic stablecoins have depegged.
	- DAI is a collateral based stablecoin, where e.g. ETH is used as collateral
	- WBTC token prices should be pegged to BTC price
	- ETH is more stable than USDC \[correct]
- What happens in AMPL system when 1 AMPL is worth less than 1 USD
	- The supply of AMPL is increase (expansion) 
	- The supply of AMPL is decreased (contraction) \[correct: if AMPL is more scarce, it should be worth more => less difference to USD]
	- no action is taken (equilibrium)
	- additional collateral is required
- How does the AMPL stablecoin reduce or increase the account balances of the token holders?
	- The ERC20 contract controls the balances and can modify them. \[correct]
	- The ERC71 contract controls the balances and can modify them.
	- every user must individually approve each account balance change before rebalancing
	- AMPL rebalances the token supply through arbitrage with USDC.
- If the reserve ratio of a bank is 0.2 and the total money deposited by bank customers is $500,000, how much money is held by the bank?
	- $100,000 \[correct bc. 0.2 = 100'000/500'000 or 0.2 * 500'000 = 100'000] 
	- $250,000
	- $400,000
	- $1,000,000