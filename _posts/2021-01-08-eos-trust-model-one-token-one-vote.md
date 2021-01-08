---
title: EOS Trust Model under One-Token One-Vote
desc: The EOS community will need to reconsider its trust model if it switches to one token one vote.
image: /assets/img/timemoney.jpg
tags: eos blockchain etheruem government 
---


As we consider moving EOS to one token one vote, there are several security considerations that the community should be aware of. The existing governance system of EOS relies upon approval voting to elect block producers. This means that every single active block producer must gain the approval of multiple “whales” and exchanges. Under a one token one vote model, it is likely that multiple block producers could be elected by a single whale.



For instance, under one token one vote, block.one could unilaterally vote in at least 2 and likely 4 or more different block producers; however, under approval voting block.one lacks the power to unilaterally vote in even a single block producer.



The implication is that the amount of tokens “securing” each producer slot is dramatically reduced and therefore more people are being promoted to a level of trust. While this increases decentralization of the producer set by ensuring more token holders are represented by a producer, it makes the network vulnerable to abuse by the least voted for producers.



Producers are given the power to arbitrarily bill users for subjective CPU resources (up to the maximum billing per block).  While over billing might be bad enough, under-billing could potentially deadlock the network. For example, a block could be produced that results in an infinite loop that is “billed” as being 100 microseconds.



There are several ways to curb this potential abuse:



1.  Objective CPU Measurement
2.  Whitelist Producers
3. Representative Governance



**Objective CPU Measurement**



EOS currently uses a subjective, wall-clock, measurement of transaction execution time. Every computer takes a different amount of time to process the transactions, but users are only billed for the time the block producer measured. This requires trusting the block producer to run honest code.



Ethereum uses objective measurement of CPU known as the GAS. This has pros and cons. When everything works properly this means that no trust is needed to prevent abuse; however, there is potential for hackers to find places where the GAS cost is out of alignment with the real time used. This would allow an attacker to create an “objectively valid block” that takes a “really long time” to validate. Fortunately, infinite loops are not an issue.



Calculating an objective measure of CPU time also introduces extra CPU overhead which reduces the total transaction throughput of a blockchain.



**Whitelist Producers**



Every full node could manually whitelist honest producers. This would mean that getting elected as a block producer is not sufficient. Full nodes, including other producers, would have to consent as well. From a certain perspective this adds an extra layer of security and confirmation, but it could create extra instability due to manual intervention required every time the token holders change the producer set.



**Representative Governance**



Instead of having the top 21 elected accounts produce blocks directly, they could be viewed as a committee that would appoint 7 producers with the approval of 14 of 21 elected producers. This committee would also have control over the system contracts. Under this model, a single untrusted/unvetted actor would never be in a position to produce a poison block.



The downside to this approach is that there are now just 7 people who can unanimously collude to censor transactions. That said, this is far better than the two or three Ethereum or Bitcoin mining pools which are able to do the same.



Of the three options, objective CPU billing may be the best solution to keeping EOS stable while increasing the diversity of the block producer set.
