# WhitePaper

Biternal: An Automatic, Decentralized, Smart Contract Blockchain

## Abstract

An automated system based on blockchain to host eternal smart contracts. Decentralization is the primary feature of blockchain, but current blockchains are passive and event-triggered systems. We propose `Biternal`, an automated blockchain for decentralized applications. Once deployed, applications can execute themselves as long as they have a balance. Applications can earn and consume balance, similar to humans. Proof-of-work is the maximum guarantee of execution and is used in this system. This is an experiment for a blockchain-based eternal system.

## Introcution

`Bitcoin` is considered a first-generation (1.0) blockchain. It revolutionized the concept of decentralized digital currency and introduced a distributed ledger system. Its main feature is decentralization. Bitcoin presented a monetary experiment system for decentralized systems and is an implementation of bit gold. It is concise but has limitations, as it is restricted to being Turing-complete.

`Ethereum` represents the second generation (2.0) of blockchain technology. It enables the execution of smart contracts on a decentralized blockchain network. The key advancement is the ability to run Turing-complete applications directly on the blockchain. This introduces the concept of decentralized applications (DApps), which is a groundbreaking development in the blockchain space. However, Ethereum's functionality is constrained as it relies on external triggers from entities outside the blockchain.

Scripting in Bitcoin and smart contracts in Ethereum are passive systems. They function as services similar to Web 2.0. While both have the feature of decentralization, they lack the intelligence and automation of smart contracts.

Based on the aforementioned accomplishments, we introduce `Biternal`, an automated and decentralized blockchain designed for smart contracts. Biternal is an experimental eternal system constructed on a decentralized framework.

## Pod

In the context of blockchain, a block serves as the fundamental unit for storing transactions. However, in Biternal, we introduce the concept of a `Pod`, which acts as a container for all `passenger`s whose smart contract's fallback function will be executed in a future block. Therefore, while a block represents the current and past transactions, a Pod represents the future transactions.

In pod, there are passengers. Each Passenger contains the host contract address and a gas limit for execution. Passengers are scheduled to execute when they have enough balance. They will continue to be scheduled indefinitely until they run out of gas or fail too many times. Passengers can be reactivated by being called by an external account. Pods are not continuous, and we define the block gap between pod creation and pod execution as the Gap. The goal of Biternal is to control the execution gap within a defined gap parameter.

Each block has a gas limit that restricts the number of transactions it can include. In Biternal, the passengers of a pod will be included in the block when the pod's block is generated. The pod will have a specific proportion of the gas limit, as defined in the Biternal protocol. When new blocks are generated, the passengers of the pod will be executed first, followed by the instant transactions that are selected from the transaction pool, sorted based on their gas price or gas tip. Biternal ensures that the execution of the pod's passengers in the protocol, and this process is automated and continues from one pod to the next.

## Token

We utilize the native token of Biternal, called `BIT`, to power the Biternal system. BIT serves as the balance for executing passenger transactions and as a reward to incentivize miners to execute pod transactions. The BIT token has two stages. In the first stage, all BIT tokens will be mined and rewarded to miners, similar to the process in Bitcoin, until the reward reaches one BIT. Once this threshold is reached, the protocol will transition to the second stage. In the second stage, BIT rewards will consist of 1 BIT, and transactions fee will be partially taken by miners and partially burned. In the genesis block, there will be a proportion of BIT allocated to the Biternal team to support the project, while the remaining tokens will be mined directly.

In Ethereum, the principle of "code is law" is upheld. However, in Biternal, with the introduction of `BIT` and `Pod`, the concept of "code is life" takes center stage.

## Imlementation

For the purpose of smart contract compatibility, we have forked Ethereum to implement Biternal. In Biternal, we have introduced a new transaction type called `ExecutionTxType`. This transaction type is executed internally and cannot be issued from an external account.

In terms of the consensus mechanism, Biternal utilizes the ethash proof of work consensus, similar to Ethereum. The pow consensus ensures that the system can be reconstructed even with just one copy of the system's data. This approach maximizes decentralization.

In Biternal, there are two base prices for the system. One is for the transaction pool, and the other is for the pod base price. The pod base price may be lower than the base fee of the pod's block.

The state of each pod is stored in a specific smart contract account. The code for the pod smart contract is implemented as core code, rather than a regular smart contract. 

Biternal smart contracts differ from Ethereum contracts in that Biternal smart contracts should define a `payable` `fallback` function,  or `payable` `receive` function and `nonpayable` `fallback` function. This function will be executed when the smart contract's balance is sufficient for execution.


## Application

In Biternal, application can be programmed like living organisms. BIT is the energy, smart application consume enery, also can earn energy in their way. In Biternal, applications form a smart contract society.


### Eternal Smart Contract

In Ethereum, smart contracts are executed when they are called. In Biternal, smart contracts are executed automatically. Smart contracts can be programmed to execute themselves indefinitely. Smart contracts can be programmed to earn BIT tokens and consume BIT tokens. Smart contracts can be programmed to be reborn when they have enough BIT tokens.

### Silicon based Socity

In Ethereum, smart contracts can be programmed to be composable. In Biternal, smart contracts can be programmed to be collaborative. As the Biternal ecosystem grows, smart contracts collaborate with each other and form a unified silicon-based Socity. Biternal is token based blockchain, it is capitalist society. Each smart contract should have one skill to earn BIT token, or it will be eliminated by the society.


### Human Immortality

when AI features are integrated into smart contracts, they give rise to AI consciousness contracts, which possess a sense of life akin to carbon-based animals.

Or when there is possible to extract human consciousness to smart contract, human will be reborn in blockchain. Human's descendants use enery to commemorate them, human will be alive forever.


## Conclusion

Biternal is an experimental blockchain system that aims to automate smart contracts. It is a decentralized system that executes smart contracts automatically. It is a living system that can be programmed to be eternal. It is a society that can be programmed to be collaborative. It is a system that can be programmed to be immortal.

Use at your own risk.

## References

1. [Bitcoin](https://bitcoin.org/bitcoin.pdf) A Peer-to-Peer Electronic Cash System

2. [Ethereum](https://ethereum.org/en/whitepaper/) A Next-Generation Smart Contract and Decentralized Application Platform