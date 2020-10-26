---
title: Decentralizing in spite of Pareto Principle
desc: An exploration of ways to overcome the pareto principle (aka the 80/20 rule) which forces most systems into control of the of 1%. 
image: /assets/img/pareto.png
tags: blockchain dpos eos bitcoin crypto government decentralization
---

Bitcoin was created with the intent of  decentralizing control over block production  so that there is  no single point of failure or control. The idea is to randomly select people from the population to produce blocks and reward them for their contribution. To  prevent  gaming the selection process by creating “fake machines”, Satoshi introduced proof of work. Each computer had to perform a computational lottery that cannot be faked.

Under the assumption that computational power is evenly distributed among the population, the result is a truly decentralized system where no one is in control and it requires 51% of the population to collude to censor data.  Unfortunately for Satoshi and society, the assumption of evenly distributed computational power is fundamentally invalid and therefore everything built upon it is invalid.

Most things in life and nature are distributed according to the Pareto Principle where the majority of the resources, skills, efficiencies, and capabilities are in possession of the minority.  In many cases this can be as extreme as 51% owned by 1%. With proof of work, only a small percentage of people have access to cheap power, efficient chips, and technical skills required.

To make things worse, proof of work is something that is easily delegated / outsourced; therefore, mining pools have taken over. Economies of scale mean that only a small number of mining pools make sense and ultimately 51% of block production is performed by just a handful of people and this handful is selected by a slightly larger, but still quite small, group of professional miners. It would not be unreasonable to assume that 99.99% of blocks are produced by 0.01% of the Bitcoin using population.

<center>
<img src="/assets/img/bitcoinhashpower.png"/>
Bitcoin Hashpower Distribution
</center>

## Proof of Stake is also limited by Pareto Principle

Stake in any system is also distributed according to the Pareto Principle. This means that proof of stake networks, including delegated proof of stake networks, are also “centralized” by the natural distribution of the underlying resource. While more people have the opportunity to vote, the small stake holders are less coordinated than the large stake holders and have less incentive to participate in voting. The result is a situation where only the top active token holders are in control, often these top holders are exchanges holding other peoples. So  while there may be “21” producer slots on blockchains like EOS, they are potentially selected by fewer than 21 parties.

It seems that for any given objective metric that a blockchain could choose, the Pareto Principle will act to centralize the control into a handful of individuals.  If we want to engineer something that increases the number of unique parties in control (and therefore decentralizes control), then we must account the the Pareto principle.

## Decentralize via Multiple Independent Pareto Distributions

Each Pareto distribution centralizes control into a few parties who have natural strengths; however, if you utilize multiple independent or ideally mutually exclusive measurements, then you can multiply the level of decentralization by the number of Pareto distributions.

Imagine for a moment that you had an ASIC-optimized algorithm, a GPU-optimized algorithm, a CPU-optimized algorithm, a stake-weighted algorithm, a stake-time weighted algorithm and ensured that all such algorithms are resistant to the creation of mining pools. Under such a model it is unlikely that the same people can be equally advantaged in all metrics; therefore, there are many more people involved.

## Decentralizing EOS Governance 

There has been considerable concern over the 21 block producers being selected by the asian community. This community has the advantage of major exchanges and cooperation via accusations of vote buying. The reality is that the asian community is controlling delegated proof of stake like they control bitcoin mining. Even if it were possible to implement  oone-person-one-vote without centralized identity validation, the asian centralization would continue.

The challenge of decentralizing blockchain governance is to combine multiple metrics. For example, if it were possible to allocate block producers on a one-per-country basis, then the network could be decentralized on a global scale regardless of concentrations of  population  or wealth in any given country. This is the basis of the Senate and House in the United States, which prevents New York and California from controlling the other 48 states.

While we can not utilize subjective metrics to decentralize blockchain, we can use multiple objective metrics to decentralize control.

## Preventing Sybil Attacks

One of the first things a decentralized network must do is discourage people from gaming the system by dividing their resources among multiple accounts. When it comes to stake voting this means that we want to encourage users to consolidate their own resources rather than divide. The easiest way to do this is to bias the influence to scale by calculating the vote weight for an account to be STAKE raised to 1.x. Under this model one account with 2 tokens has more influence than 2 accounts with 1 token.

Then give each account the option to vote for only one block producer. Someone with 2 tokens can have more influence supporting one producer than dividing their tokens and supporting 2 producers.

From the perspective of provable decentralization, we must assume that all stake that votes for a producer is owned by that producer. While one producer may have 1000 supporters, we don’t know whether they are “real” or merely “rented” via vote buying. Therefore, we must assume that a producer has either begged, borrowed, stolen, or purchased the stake that is used to get them elected.

Under this “conservative” assumption, we can model DPOS as electing the top 21 stake holders to control the network. The Pareto distribution is recursive, so the top 4 stake holders would have 80% of the stake owned by top 21 and that the top stake holder will have over 51% of the stake. If this stake holder were to divide their stake among 21 accounts, then under a linear voting weight they could likely produce 21 accounts each of which has more votes than any of the others. Under non-linear vote weight, the influence penalty for dividing their tokens neutralizes their advantage created by having more tokens than everyone else.

So the first step toward decentralizing is to ensure that at the very least, the top 21 slots are controlled by the 21 richest people and not 15/21 sock puppets owned by the richest person while everyone else fights over the last 7 slots which is not enough to prevent byzantine failure.

It should be obvious that there are various degrees of Pareto distribution and that EOS stake distribution isn’t as extreme as used above; however, it is not unreasonable to assume that with a linear vote weight that fewer than 21 real unique parties will end up in control. It would probably mirror the centralization seen in Bitcoin mining pools with just a handful of people controlling all 21 slots.

## Economies of Scale

The reason vote buying results in centralization is due to economies of scale. While the blockchain may know about 21 producers, it has no way to enforce that those producers are operating on independent hardware. Therefore, a party who can capture enough votes to buy two sock puppets has twice the revenue with fixed expenses and can afford to pay more for votes than a party that can only capture 1 of 21 slots.

The same is also true for Bitcoin mining pools. While there may be 2 different “pools of record”, there is no way to know for certain that there isn’t a single node behind it all.

Decentralization requires solutions that can counteract economies of scale because it is economies of scale that creates the Pareto distributions in the first place. To do this we must implement multiple independent economies that define scale differently.

## Giving RAM Voting Weight

Imagine if RAM holders got to elect several block producers. Holding RAM has economic cost as the network scales and RAM supply increases. Unless you really need RAM buying RAM just to gain influence is a very expensive trade over the long-term. Someone cannot hold their wealth in both EOS and RAM at the same time; therefore, they must choose and the result of dividing their wealth also reduces their total influence in the system because of the super linear vote weighting system proposed above.

RAM holding is a proxy for those who are actually using the network and giving these parties influence over some of the block producers is useful in decentralizing the interests of voters between those who care about token price (EOS) and those who care about utility (RAM) holders.

## Giving Stake-Time Voting Weight

Those who  are  have a large stake are divided into two camps, those who need liquidity (exchanges), and those who are in it for the long-haul, and don’t need liquidity. We  can increase decentralization by allowing those who stake their tokens for longer time more influence. Give each user vote weight proportional to stake-days*(stake²). Someone who stakes 1 token for 1000 days will have 1000x the influence to someone who stakes 1 token for 1 day. If stake-time voting users can elect some producers then we can guarantee that the wealthiest cannot control all the positions unless they are also the most-long-term committed. Furthermore, a wealthy individual would have to divide their stake if they wanted to use stake-time and stake-weighted voting which would make their influence weaker overall.

Clearly there are diminishing returns to staking time. Clearly staking 1 token for a trillion years shouldn’t outweigh everything. Therefore, there should be a maximum staking period of a couple of years.

## Infinite Stake-Time Voting Weight

Imagine if someone could lock up their tokens forever. This is equivalent to burning tokens or out-right buying a position in top 21. Those who do this are benefiting all other token holders through their burning and can gain a seat at the table. To maintain this position you must continuously burn more tokens than everyone else. This is the economic equivalent of proof-of-work where instead of burning electricity to the economic benefit of power companies, you burn tokens for economic benefit of token holders. This method has the benefits of proof-of-work without biasing influence toward those with access to specific resources and skills.

## Rewarding Non-Voting Users

Paying people who don’t vote is the best way to remove disinterested parties and uninformed opinions from the governance equation. Under this system those who take cash transfer control voluntarily to those who want it. To discourage people from just taking the cash without risk, the voting rewards should be distributed proportional to stake-time commitment. Someone who commits to 1000 days would get a larger share of non-voting rewards than someone staking for 1 day. In this way non-voters are rewarded for their commitment to the network and must trust the long-term governance is in good hands. Limits must be placed on the length of time one can stake to prevent monopoly by long-term holders.

## Summary

To summarize the proposal my suggestion for community to review is to divide the 21 producers into 4 categories:

1.  8 — STAKE²
2.  8 — DAYS * STAKE²
3.  3 — RAM
4.  2 — (AVG BURN/DAY)²

**Electoral College**

Rather than producers having to choose one of these categories and limiting the number of slots to 21, the network could select 100 delegates and then use approval voting of 1-vote per delegate to select 21 block producers. This added level of indirection gives people more voice without sacrificing blockchain performance and prevents producers from having to pick a category.

The primary challenge with this governance structure is complexity. We could say the simplest governance structure is a centralized king. I believe that there is a  continuum between complexity and decentralization and that any simple system will be centralized due to Pareto Principle.  Complexity can be dangerous if it enables complex hard-to-follow gaming of the rules.

## Proof of Work Blockchains

Under a proof of work model, a blockchain should switch the hashing algorithm after every block and the algorithms selected must be resistant to creation of mining pools. This is made possible by requiring a private key in control of more funds than the block reward to be used as part of the proof of work. Any mining pool would have to distribute their private key to all the members of the pool, any of which could walk off with the funds. The end result is that there would be no mining pools.

## Conclusion

It is my hope that this post will spark some much needed discussion on objective means of increasing decentralization and breaking through economies of scale and the Pareto distribution of power and influence it creates.

<sub>The original post and discussion can be found on [[my medium blog::https://medium.com/@bytemaster/decentralizing-in-spite-of-pareto-principle-eda86bb8228b]]. </sub>
