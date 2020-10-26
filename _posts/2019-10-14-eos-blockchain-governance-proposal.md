---
title: EOS Blockchain Governance Proposal
desc: A proposal to utilize multiple staking pools of different lengths to allocate power and align economic incentives
tags: eos government blockchain defi crypto
image: /assets/img/treasury-yield-curve.png
---

The purpose of blockchain governance is to make decisions in the best interest of as many people as possible while minimizing the opportunity for a small group of people to act in ways that benefit themselves at the expense of the community. The key is to align interests and select the parties with the most to lose if the network fails to operate to its potential. True proof of stake aligns long term interests and puts control in the hands of those with a long term commitment.

From the perspective of what can be proven objectively, we can conservatively assume all accounts which vote for a producer are owned by the producer. We can also view votes and “vote buying” as nothing short of “renting stake” for the purpose of qualifying for the top N. Since there is little difference between renting and selling with a trustless repurchase agreement, there is nothing immoral with this activity and attempts to prevent it are in fact a potential violation of ownership rights.

To ensure a long-term outlook and “skin in the game”, only tokens locked in a long-term staking contract qualify for voting.  The yield someone earns for staking compensates them for the loss of liquidity and should be proportional to the length of time the tokens are locked up. It is best for the network for tokens to be locked as long as possible based upon **_market determined rates of interest_**.

Therefore, I propose the creation of 6 staking pools: 3 month, 6 month, 12 month, 2 year, 5 year, and 10 year. In a network with a token supply of 1B, each pool will receive 5M tokens per year on a minute by minute basis (assuming network is operating at 100% reliability). Users can buy into the pool to receive their pro-rata share of that pools income. A user’s vote-weight is based upon the sum of their percentage ownership of each pool. This represents a 3% annual inflation paid to the different staking pools.

Funds can be withdrawn from the pool at most one a week. Stake in a 3 month pool could be withdrawn at about 7% per week. Stake in a 10 year pool could be withdrawn at 0.2% per week.

Tokens in a stake pool are taken out of the “resource” pool so cannot be lent to the REX, this increases the bandwidth per token for all tokens in the REX.The staking pools can be viewed as a bond where the tokens are taken out of circulation now and returned to circulation with added interest from inflation at some point in the future.

So long as your tokens remain in a staking pool they will have their interest compound at a rate proportional to the total amount of stake in each pool.

Tokens can move from a shorter term to a longer term without any delay. So you can move 100% of your 3 month stake to a 10 year stake at any time; however, you cannot move from a 10 year to a shorter term except at the rate of 0.2% per week.

The outcome of this staking system is that market forces will set the yield curve based upon balancing the desire for power and liquidity. Few people will want to give up liquidity for 10 years so they will earn a higher relative yield and more power over the network. More people will be willing to give up liquidity for 3 months, so they will get a lower yield and less power.

Once everyone has staked and voted, 21 block producers will be selected on a “one token one vote” basis  (weighted by percent of pool tokens are staked in).  These producers will be paid proportionally to the votes they receive instead of on a per-block basis.  Paying block producers anything other than a linear relationship to their votes will incentives a sybil attack and result in increased centralization of power instead of 21 distinct parties, there may only be 20 or less with one person attempting to control two or more slots.

Producer rewards should be minimized to just 0.5% of token supply per year (discounted by global reliability). Ultimately, the largest stakeholders will likely control who the producers are; therefore, the yield paid to the staking pools is likely flowing to most of the same people who are running the producers.

All the decentralization in the world helps no one if the network cannot ensure that blocks are produced reliably; therefore, all inflation is scaled by the 7 day average availability raised to the 10th power. At 99% reliability the total inflation will be 90% of the max inflation of 3.5%. If a producer starts missing blocks and reliability falls to 97% then everyone’s yield falls to 73% of maximum yield. This means that voters (stakers) are punished if they don’t vote for reliable producers.

# Expected Outcome

Exchanges would be unable to vote with user tokens because most of the control is tied up in long-term staking contracts.  With one token one vote model and pay proportional to votes it would end the situation of two producers are operated by one individual. With only staked tokens voting we assure that everyone seeking to be a producer has skin in the game and that even the lowest producer slot is likely to be reliable. Perhaps one of the more fascinating outcomes is the discovery of a true market-based interest rate and yield curve. Smaller stakeholders can gain extra influence and higher yields by participating in the long-term staking pools.

The REX will define the yield on the shortest term (3-day) staking pool and tokens in the REX would no longer having voting rights. Those seeking yield should move to the staking pools instead.

Everything in this proposal is for community consideration and may be one of many viable solutions.

_Disclaimer: Everything in this post is my opinion and not that of my employer. Do not assume anything in this post will be implemented or adopted by any blockchain. I have not considered any legal or tax consequences of the proposed design, so please consult relevant advisors before moving forward._
