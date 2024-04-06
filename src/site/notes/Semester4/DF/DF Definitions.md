---
{"dg-publish":true,"permalink":"/semester4/df/df-definitions/"}
---

- more definition in [[Ethereum and DeFi Glossary.pdf]]
- **pegged** cryptocurrency: cryptocurrency whose value is linked to a specific bank-issued currency, financial instrument or tradable commodity
	- e.g. pay back to buy BTC and holds it for you
- **Know your customer** ( #short KYC): means verifying who you are when joining a crypto exchange
- **Anti-money laundering** ( #short AML): helping to break criminal networks and minimise the impact of illicit transactions on affected economies.
- **washtrading**: occurs when an investor buys and sells the same or a similar security investment at the same time (e.g. can be done by using flash loans)
- **(Fractional) reserve**: bank's reserve ratio = (money held by bank) / (money deposited by bank customers)
- **Exchange traded fund** ( #short ETF): security/asset![Pasted image 20240405223919.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240405223919.png)
	- tracking an index/sector/commodity
	- tradable on an exchange
	- typically, lower fees than buying individual stocks
	- EFT types: bond, stock, industry, commodity, currency, inverse, etc
	- e.g. SPDR S&P 500 ETF tracks the S&P 500 index
### Lending
- **collateral**: assets that serve as a security deposit
- **Over-collateralisation**: Borrower has to provide value(collateral assets) > value(granted loan)
- **Under-collateralisation**: value(collateral) < value(debt)
- **Liquidation**: selling collateral from the borrower
	- E.g., if value(collateral) <= 150% x value(debt)
	- Anyone can liquidate the debt position
- **Health factor** ![Pasted image 20240323154018.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323154018.png)
	- 0 < liquidation threshold < 1
	- liquidation threshold provides a "secure" margin
	- when health factor < 1 => borrowing position becomes liquidatable
	- e.g. ![Pasted image 20240323154201.png](/img/user/Semester4/DF/attachments/Pasted%20image%2020240323154201.png)
- **Liquidation Spread** #short LS: bonus, or discount, that a liquidator can collect when liquidating collateral
	- 𝑉𝑎𝑙𝑢𝑒 𝑜𝑓 𝐶𝑜𝑙𝑙𝑎𝑡𝑒𝑟𝑎𝑙 𝑡𝑜 𝐶𝑙𝑎𝑖𝑚 = 𝑉𝑎𝑙𝑢𝑒 𝑜𝑓 𝐷𝑒𝑏𝑡 𝑡𝑜 𝑅𝑒𝑝𝑎𝑦 × (1 + 𝐿𝑆)
- **Close Factor** #short CF: the maximum proportion of the debt that is allowed to be repaid in a single fixed spread liquidation
	𝑉𝑎𝑙𝑢𝑒 𝑜𝑓 𝐷𝑒𝑏𝑡 𝑡𝑜 𝑅𝑒𝑝𝑎𝑦 < 𝐶𝐹 × 𝑇𝑜𝑡𝑎𝑙 𝑉𝑎𝑙𝑢𝑒 𝑜𝑓 𝐷𝑒𝑏𝑡𝑠