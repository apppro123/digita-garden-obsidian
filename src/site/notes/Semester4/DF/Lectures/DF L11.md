---
{"dg-publish":true,"permalink":"/semester4/df/lectures/df-l11/"}
---

## JAM Protocol
- Graypaper: formal specification of JAM
- Yellowpaper: formal specification of Ethereum protocol
- **assumptions**
	- not more than 1/3 + 1 of nodes behave in a dishonest way
		- honesty not same as correctness (bc. correctness cannot/isn't controlled)
	- common clock: all nodes on the network have prior agreement on time
### Driving factors and Web3 maxims
- Resilience: run on its own
- Generality
- Performance: # actions per second and how efficient they can be done
- Coherency
	- system either coherent and not big OR big and not coherent
	- problem of size synchrony approached by divide (into subsystems) and conquer (synchronise in slower way)
	- every 6sec. system is fully coherent (done over central aggregator)
- Accessibility: make system that makes sense to practitioner 
### Data Topology
- flower structure where
	- **paddles** = one core of computation: do preprocessing (and some additional things)
		- can draw and push on data availability system ( #short DA system) (bigger/more data/states than centre has => data can be passed over time without going through centre)
		- fungible with own state
		- 341 of these cores: ![Pasted image 20240529093009.png](/img/user/Semester4/DF/Lectures/attachments/Pasted%20image%2020240529093009.png)
	- centre (similar to CPU core): as fast as fastest blockchain today's on it's own
		- access to highspeed database similar to other blockchains
### Other
- **Beefy & Grandpa** are finality algorithms i.e./e.g. discover latest state of JAM
- **Ratings**: rewards honest behaviour
	- validators and on-chain work rate (each other)
- **limit state growth** by enforcing having a deposit for every bit which can increase or decrease with the data growing or shrinking
- **work package**: some data with service to be fetched into
- cores can be **bought** probably in a monthly fashion and then split up and sold again where you can run code on it when a validator (code) by the main buyer returns true
- **biggest risk** for DeFi/Crypto (according to Gavin Wood): resilience risks where the failing of one chain has other failings as a consequence and so on (not direct connections but financial/trust connections between different blockchains)
## Quiz
no quiz