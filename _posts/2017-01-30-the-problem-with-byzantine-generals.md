---
title: The Problem with Byzantine Generals
desc: Bitcoin and DPOS don't solve the byzantine generals problem and that is a good thing.
image: /assets/img/byzantine.jpg
tags:  blockchain dpos bitcoin
---

There are many different blockchain consensus algorithms being promoted these days. Academics like to evaluate these algorithms to see if they solve the byzantine generals problem. This particular problem is how to get a group of lieutenants to agree on whether to retreat or advance when up to ⅓ of them may be dishonest. In terms of blockchains, the challenge is to get the entire world to agree on a particular blockchain.

One of the aspects of byzantine fault tolerance (BFT) is that an algorithm always reaches a conclusion and never ends up in an indeterminate state. In other words, at some point people need to know with certainty that everyone is in agreement and that a minority of bad actors cannot halt the process completely. In all systems an assumption that ⅔ of the generals are honest is a mathematical requirement.

## Proof of Work does not Solve Byzantine Generals

Bitcoin and other Proof of Work algorithms define the best chain as the one with the most difficult proof of work. A problem with proof of work, from byzantine perspective, is that it is always possible for the blockchain to be reversed, it just becomes increasingly unlikely and uneconomical. In order to consider Bitcoin and similar blockchains to have BFT you must assume that 99.999% certainty is the same as 100%. Someone with 10% of the hash power can pull off a double spend against someone waiting for 6 confirmations once per month or 0.02% of the time.

## Cosmos White Paper

The  [cosmos](https://cosmos.network/ "This link will take you away from steemit.com")  white paper claims a working byzantine fault tolerance algorithm whereby a group of block producers can unanimously agree on the next block. They claim their process guarantees the network to advance as long as more than ⅔ are honest. The rest of the world never has to consider blockchain forks because they are “impossible” under their algorithm.

I was thoroughly impressed at the thoroughness of their approach and the robustness of their algorithm. I was also very appreciative that some of their team took the time to evaluate my own algorithm, Delegated Proof of Stake (DPOS). See [[DPOS Consensus Algorithm - The Missing White Paper]].

## Delegated Proof of Stake (DPOS)

DPOS is an algorithm whereby stakeholders elect an odd number of block producers. Each round the block producers are shuffled and assigned a time slot in which they should produce a block. With this process in place, the longest chain is considered the best chain. It is impossible for a minority of block producers to create a longer chain because they would be producing fewer blocks per minute than the majority blockchain.

Like Bitcoin, under this model alone you never have 100% certainty because the majority could suddenly switch to a minority fork and stop producing on their own. Eventually the minority fork would become longer and global consensus would necessarily change.

We then introduced a new concept known as the Last Irreversible Block (LIB). This is a block which has been confirmed by ⅔ or more of the elected block producers. No node will automatically switch to a fork that isn’t built on top of the LIB.

Members of Cosmos community recently discovered a particular sequence of events that could cause the LIB algorithm to break down by causing the network to split on two different LIB. This vulnerability in the LIB algorithm does not constitute a breakdown of DPOS because the LIB algorithm was an optional addition designed to identify the number of confirmations required before an exchange has sufficient guarantees that a block will not get orphaned. The LIB algorithm is similar to the 6 confirmation algorithm used by Bitcoin. It works 99.9999% of the time. In over 2 years of operation and 10’s of millions of blocks it has not yet experienced the kind of deadlock condition that is theoretically possible.

## The Real Problem - Who are the Generals?

A problem with Cosmos is an in implicit assumption that the set of generals is fixed. At least for a given block. If at any time over ⅓ of the generals goes rogue, then the network halts and there is no process for resuming the network.

Under DPOS, if a large minority of generals goes bad then the network still operates in a “pending” state. Blocks are produced, votes are cast, and new generals can be elected. Eventually the stakeholders can reach a point where 100% of the generals are honest and the network resumes normal operation. In theory, if 95% of the generals fail the remaining 5% can still hold an election to replace them.

From this we can conclude that Cosmos has a  _different_  deadlock condition. DPOS is robust due to its ability to continue operating at a reduced capacity / confidence level even when the majority of the generals are down.

## Trade Offs

Every algorithm makes certain tradeoffs. Cosmos has 100% guarantee of no forks and can produce blocks every 5 to 10 seconds on a distributed network. To achieve this with the same number of generals as Steem (21), they consume network bandwidth similar to a sustained 5 transactions per second.

On the other hand, Steem rarely has any missed blocks and even more rarely has an orphaned block. Statistically speaking, a block produced while there is 100% participation of generals (producers) has a 99.9999% chance of being the final block. After two blocks (6 seconds) the probability being orphaned falls further. Anyone relying on the last irreversible block algorithm (40 seconds) is protected against almost every conceivable scenario with a worst-case (purely theoretical) being stuck in a pending state on a minority fork until manual intervention. This means that it fails “safe”, in a state where you do not accept a bogus transactions.

There is one additional level of confirmation that could be implemented in DPOS: require 100% participation and 21 blocks. With 63 seconds of confirmation and 100% participation then you can be certain that you will never get “stuck” and that every transaction you receive is truly irreversible and globally accepted.

What you should notice with these numbers is that extra time buys insurance for the last 0.00001% of byzantine cases. This is a level of confidence that takes far more than 6 confirmations in Bitcoin to reach, especially with an attacker that has 33% of the hash power.

## Conclusion

Due to the law of diminishing returns (economic marginal utility), the value of increased confidence from 99.9999% to 100% is unmeasurable for the vast majority of real world transactions. People lose more from transaction fees than they would if 1 out of every 1 million transactions were to be randomly reversed. Meanwhile, the cost of gaining that last 0.0001% of confidence is significant network overhead, slower per-block times, and complete failure if more than ⅓ of the nodes go down.

Both algorithms have their place, but I am very happy with the design tradeoffs made for DPOS compared to the other algorithms available.
