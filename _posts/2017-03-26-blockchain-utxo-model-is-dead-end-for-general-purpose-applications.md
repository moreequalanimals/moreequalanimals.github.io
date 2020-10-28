---
title: Blockchain UTXO model is a Dead End for General Purpose Applications
desc: An analysis of the UTXO (Unspent Transaction Output) model used by bitcoin and why it isn't appropriate for decentralized applications.
image: /assets/img/deadend.jpg
tags: blockchain bitcoin 

---

Bitcoin was the first cryptocurrency to introduce the UTXO (Unspent Transaction Output) model for tracking database state. Every Bitcoin transaction consumes (spends) outputs from prior transactions and produces new outputs to be consumed by future transactions. Each output can only be consumed once. This structure has many very nice mathematical properties, including structurally proving that the same tokens can never be spent twice provided every transaction proves that the sum of its inputs is greater than the sum of its outputs.

Today many of the thought leaders at organizations such as R3, Blockstream, BOSCoin, and Qtum continue to advance the notion of the UTXO model. In some cases, they are pitching it superior to other approaches and their entire business is focused around this model. The main reason UTXO is presented as superior is because it has natural parallelism as every transaction can be processed in parallel because they all refer to independent / non-conflicting outputs. From a theoretical computer science perspective, UTXO is elegant and easy to prove. In the real world however, things are very different.

## Limited Application of UTXO

The UTXO model is only suitable for applications where each output is owned by exactly one individual. This fits the currency model perfectly and is why it works with Bitcoin. However, if there ever exists an output that could potentially be consumed by two or more people at the same time, then the entire process breaks down.

A prime example would be an exchange limit order. In the UTXO world this would be represented by an output that could be claimed provided the claimer paid the prior owner the price they demanded. If there was no competition over this output then everything works perfectly; however, as soon as two people wish to claim the output at the same time problems occur.

Alice and Bob both construct a transaction to consume the order, a few seconds later Bob finds out that Alice’s transaction won and his failed. So Bob attempts to construct a new transaction to take the next available order. Unfortunately, this also fails because someone else claimed it first. Bob is forced to loop in a tight script that will produce and sign transactions until one of them succeeds. This problem is made more complicated on blockchains where short-term chain reorganizations are common (proof of work).

This problem is amplified even further if one wishes to construct an exchange that enforces the requirement that orders are filled from highest to lowest on a first come, first serve basis. Instead of the order book being represented as a hundreds of individual outputs, it becomes one giant output that contains the entire state of the order book. All transactions take the current order book as their input and produce a new order book as their output. Rather than Alice and Bob fighting over a single output, you have every market participant fighting over it.

From an information theory perspective, this pure functional approach to the order book is extremely elegant, but once you consider the cost of duplicating and verifying the content, broadcasting it over and over, and lock contention it is clear that an elegant mathematical model is not enough.

## Simplest Possible Example

Imagine a smart contract that implements a counter that can be incremented by anyone. Imagine that there is some economic incentive to be increment the counter before as many people as possible and that there are 1000 people actively attempting to increment this counter as soon and as frequently as possible.

The UTXO model would represent this as an output with a single number that can be claimed provided the transaction produces a new output with that same number incremented by 1. How fast could the counter increment?

If we assume a 3 second block interval, then it would increment once every 3 seconds. If we assume that people speculative build on pending UTXO then it would increment once every 250ms (global latency for peers around the world). Of course, allowing people to build off of unconfirmed UTXO would create a combinatorial explosion as everyone attempts to build off of every pending UTXO until a block producer finally picks some and rejects others.

To prevent network spam, peers would be forced to block transactions that build off of too many speculative transaction chains.

## UTXO forces a Synchronization Point

The UTXO model forces exactly one person to grab a lock on the output, perform some transformation, and produce a new output. In computer science this pattern is known as  [Compare and Swap](https://en.wikipedia.org/wiki/Compare-and-swap)  and it is normally used in tight loops to synchronize parallel access to data.

The difference between a CPU level compare-and-swap, and a UTXO level compare-and-swap is in how long the operation takes. A UTXO is limited by network latency and two peers on opposite sides of the globe would be lucky to achieve 5 successful operations per second. It is well known that heavy contention on a CPU compare and swap can cause multi-threaded performance to be far slower than a single-threaded alternative. This property applies even more so to UTXO.

## UTXO forces State into Transactions

Every transaction explicitly includes its new output state. This state includes everything that must be modified in an atomic manner. If the UTXO were an exchange order book, then the state would be the entire order book. What works for Bitcoin currency (a short script and a balance), doesn’t work for anything that is even slightly more complex or that refers to more data.

Lets consider the counter again, only this time lets assume that the counter is attached to a 1 MB databuffer whose value changes deterministically every time the counter changes. Now the network and blockchain end up processing 1MB of data per transaction. This is exactly what would happen if exchanges, social media content, and other applications were implemented as a UTXO.

## UTXO forces unnatural Designs

Because of these drawbacks, people who build applications based upon UTXO are forced to limit the amount of state impacted by each output. This means exchanges without rules on the order in which things are filled. This means anything that is the result of aggregating input from multiple parties is likely not viable.

## Alternative Message Based Approach

Steem and Bitshares adopt a message based approach. In this case, the blockchain represents a consensus over the order of messages and the state is deterministically derived from these messages.

To implement a counter, each user would simply sign a message requesting to increment the counter by 1. The message would not need to know the current state of the counter in order to be a valid message. This means that 1000 people could submit the request at the same time and that the block producer could aggregate all requests into a block and 3 seconds later the counter will have gone from 0 to 1000.

## Conclusion

What we can conclude from this article is that any blockchain that is building on a UTXO model is inherently limiting their applications to those involving a single owner per output. Any multi-owner output would be restricted by latency due to the speed of light to just a couple transactions per second. What works great for a currency like Bitcoin, does not work at all for general purpose applications.
