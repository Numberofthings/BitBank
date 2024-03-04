# BitBank Whitepaper

## Introduction
BitBank is a decentralized application (dApp) built on the Ethereum blockchain. It's designed to interact with eBTC, an ERC20 token. The contract allows users to enter and exit with their eBTC, while distributing dividends among the remaining participants.

## BITS: Not a Token, but a Mechanism
In BitBank, BITS is not a separate token. Instead, it's a mechanism within the contract that pegs the number of eBTC a user enters with to a 1:1 ratio. This is represented by the `bitsBalance` mapping in the contract, which tracks the balance of each user.

## Dividend Distribution
When a user enters or exits the BitBank, a 5% fee is deducted from the amount and distributed as dividends among the remaining participants. The dividends are proportional to the amount of eBTC each participant has in the contract. This is handled by the `distributeDividends` function.

The dividend for a user is calculated using the formula:

$$\text{{dividend}} = \text{{fee}} \times \frac{{\text{{user's bitsBalance}}}}{{\text{{totalBits}}}}$$

Where:
- `fee` is the 5% fee deducted from the entered or exited amount.
- `user's bitsBalance` is the amount of eBTC the user has in the contract.
- `totalBits` is the total amount of eBTC in the contract from all participants.

## Entry and Exit: Maximum Loss is the Fee
The only loss a user can incur from transactions is the 5% fee deducted when entering or exiting the contract. This fee is then distributed as dividends to the remaining participants. Therefore, a user cannot lose more than the entry and exit fee.

## Ethical Use of Blockchain and First Principles
BitBank uses blockchain technology to create a transparent and fair system for users to interact with eBTC. It adheres to the first principles of blockchain: decentralization, transparency, and security. There are no dev fees or admin functions, ensuring that the contract is fully autonomous and all users are treated equally.

## Example Scenario
Consider a scenario with four users: Alice, Bob, Charlie, and David. Alice enters with 100 eBTC, Bob with 200 eBTC, Charlie with 300 eBTC, and David with 400 eBTC. When each user enters, a 5% fee is deducted and distributed as dividends among the remaining users. If Bob decides to exit, his eBTC is returned, a 5% fee is deducted, and the fee is distributed as dividends to Alice, Charlie, and David. The dividends can be withdrawn or reinvested by each user.

In this scenario, Bob should have received approximately 16.67 eBTC in dividends when Charlie and David entered the BitBank. These dividends were added to Bob's `dividends` in the contract and could be withdrawn or reinvested by calling the `withdrawDividends` or `reinvestDividends` function.

Therefore, when Bob exited the BitBank, he should have received his `bitsBalance` of 200 eBTC plus his `dividends` of approximately 16.67 eBTC, minus the 5% exit fee of 10 eBTC. So, Bob should have exited with approximately 206.67 eBTC.

## Conclusion
BitBank provides a unique way for users to interact with the eBTC token. By leveraging the power of blockchain, it ensures transparency, fairness, and security for all users. As always, users should do their own research and consider seeking advice from professionals when dealing with cryptocurrencies and smart contracts.
