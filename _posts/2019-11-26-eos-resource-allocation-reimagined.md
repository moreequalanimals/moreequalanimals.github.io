---
title: EOS Resource Allocation Reimagined
desc: A better approach to allocating CPU and NET resources that makes resources more affordable and easier to understand for developers and users.
image: /assets/img/eos-resource-reimagined.jpg
tags: eos blockchain defi crypto

---

The EOS public network, the first implementation of EOSIO, is the most used public blockchain by a wide margin and has recently been processing a sustained 800 transfers per second utilizing a fraction of its technical capacity. The demand for transfers has been so high that the resource exchange, REX, has run out of EOS tokens to lease. This post explores the reasons why REX ran out of EOS to lend and proposes a solution that ensures that CPU resources are always available at a reasonable market price.

The EOS resource model was derived from my earlier work on Steem and "[[How to build a Decentralized Application without Fees]]". 

EOS tokens provide the utility of CPU bandwidth when they are staked. The capital cost of CPU utility has been priced highly by the market, which means that most people need to rent EOS to get the CPU they need at an affordable price with minimal exposure to capital loss as a result of the volatility in the price of EOS.

The REX (Resource Exchange) is designed to automate a market between those who own the EOS CPU utility and those who wish to use the CPU time without owning EOS. The challenge has become  establishing a price for renting EOS, while maintaining the value of utility for EOS owners: if priced too high, then no one will be willing to rent and the network will therefore be under-utilized, and if priced too low, then the available supply of EOS will be over extended, leaving no CPU available at any price.

We designed the REX to use an algorithm that raises the price toward infinity as the remaining supply of EOS available to rent approaches zero.Recently the REX got into a situation where there was no EOS available to rent at any price, because it is possible for those providing EOS for others to rent to recall them at will. We did not anticipate that such a large amount of EOS would be withdrawn from the REX given the expected demand to earn.

The good news is that REX is working as designed and that it will deliver on the promises the code made to allow EOS put into REX to be returned to the lender within 30 days. The pricing algorithm response to a sudden withdraw request of more EOS than there was to lend out was to push the price to infinity.

This happened because of initial assumptions made during the design of REX:

1.  There would be a normal distribution of rental demand across a large number of accounts
2.  There would be a normal distribution of lending demand to the REX
3.  Rising rental rates would drive new demand to supply REX with additional EOS to rent
4.  Withdraws from REX would be offset by deposits with the total rental supply being relatively stable

Reality:

1.  Deposits into REX are governed by Pareto distribution
2.  Withdraws from REX are distributed on Pareto
3.  Demand for borrowing from REX is governed by Pareto distribution
4.  Rental income that is earned up front can be claimed by withdrawing before the 30 day rental period has expired

The result of the mismatch between initial assumptions and the reality of REX usage has been a volatile price for renting resources and the unavailability of EOS for rent.

# Clean Slate Design for CPU Allocation

The current state of the REX is the result of a gradual evolution in resource allocation strategies for public EOSIO networks. In order to maximize our flexibility in imagining solutions, we like to consider what could be done differently if we had no restrictions from past designs. If a better ideal solution can be conceived, then we can work backwards to a design that can be evolved from the current state of the EOS network and its REX.

The single biggest complaint is that  “CPU” is too expensive, followed closely by the complaint that it is  too unpredictable  in terms of  how much CPU bandwidth you get at any given time. The source of these complaints can be tied to prior attempts at making CPU cheaper given the high capital cost and the low utilization. EOSIO was conceived to use a token to represent an ownership model where 1% of the EOS allowed you to consume 1% of the CPU, forever, free of charge. This resource model is similar to buying a house in which you can live forever.

The CPU ownership model gave EOS great utility, but also resulted in users having to own a large amount of EOS in order to use the network. Because the market has imbued all transferable crypto assets with speculative value beyond the intended utility value, the capital required to gain the utility of the EOS CPU time is more than most users can commit. Furthermore, the risk associated with volatility means that the true cost of CPU is unpredictably tied to capital gains or losses in an extremely volatile market.

To reduce the cost of CPU, EOSIO introduced “fractional reserve CPU”, which allocated unused CPU cycles to active users. This lowered the perceived cost of CPU by up to 1000x when the network was under utilized; however, it simultaneously gave unpredictable results when usage surged and people were locked out of their accounts because they had already consumed more than their minimum guaranteed CPU.

Last month we introduced the option to greylist all accounts and remove the 1000x boost in free CPU  and subsequently encouraging people to use the REX; where they could rent EOS at a much lower risk and cost than buying EOS to stake themselves. At the same time some EOS users leased most of the EOS from the REX and started utilizing their rightful CPU budget. Even with the elimination of the 1000x free CPU bonus, the predictability of CPU time per EOS was dependent upon the percentage of total EOS staked to CPU.

Imagine that you are the only user staking EOS to CPU, you would be allocated 100% of the CPU. Now imagine that another user stakes 100x the amount of EOS you staked to the CPU, bringing your CPU budget down to 1% of what it was originally. This is what happens when someone rents a large quantity of EOS from the REX and stakes it for CPU.

Bottom line: in addition to the 1000x bonus, there was an additional 3–5x bonus based upon unstaked EOS that could be staked  at any time. These factors have made CPU allocation unpredictable for people who have staked EOS, whether they rented it or owned it.

# The Ideal Algorithm

In the ideal algorithm, CPU would have no speculative value and the amount of CPU time you had reserved would be fixed and predictable.Furthermore, you could use CPU without tying up large amounts of capital (in the form of EOS tokens) and exposing it to capital gains or losses. Finally, there would always be CPU available at some price and therefore,  the price of CPU would be relatively stable across time.

To achieve this 100% of all CPU time should be leased from the system contract at an EOS price that grows exponentially as the percentage of CPU leased increases.  The EOS paid to lease the CPU time would be distributed to staked EOS tokens (e.g. the REX pool). This model preserves the allocation of CPU to staked EOS holders via offsetting income from staking and expenses from leasing CPU. Assume your staked EOS generates 1 EOS per month in growth, you could spend that 1 EOS in the rental markets and get some amount of CPU. The amount of CPU will be dynamic based upon the current prices. Obviously, some of the CPU rental costs would be directed back to you based upon your percentage of staked tokens.

By having 100% of all CPU allocated by leasing, there is no longer a _dynamic_ supply of tokens staked to CPU, nor is there any need to worry about people withdrawing EOS from REX causing shocks to the CPU rental market and its pricing algorithm.

Furthermore,  CPU time becomes non-transferrable  because all CPU time is allocated via  leasing from the system contract rather than by staking EOS. This eliminates the speculative component to CPU pricing and ensures everyone is  operating under the same resource model.

A simple equation could be used to determine the amount paid to lease a fixed percentage of the total CPU time for 30 days.

The chart below shows charging 100M EOS * PercentUsage2 for the rent. With this equation, the rental income would exceed EOS inflation once the network leased about 10% capacity. It is possible that future versions of EOSIO governance may choose to pay block producers a percentage of the rental income, which would align their interests in maximizing the utility value of the network. In principle, the community could use any constant exponent to determine the price curve. Higher exponents will allow a larger percentage of the network to be utilized cheaply, but will increase prices faster as utilization approaches 100%. The ideal exponent would balance supply and demand to maximize the difference between total rental income minus blockchain operating costs.

![cpu price vs usage graph](/assets/img/eos-resource-reimagined-graph.png)

Because those who would rent CPU are distributed in a Pareto distribution, we would expect there to be a number of large renters who rent and/or renew at the same time. This could result in sudden drops in rental rates followed by increases. Absent an “order book” to catch falling rental rates it could create an undesirable pricing advantage to larger renters.  Therefore, we propose that rental prices fall slower than they rise. Given a pricing function, P(TotalUsage), the price that a new CPU rental would be issued at would be MAX( P(CurrentUsage), P(DailyAvgTotalUsage) ). If prices get too high, then the CurrentTotalUsage will drop and over time so will DailyAvgTotalUsage. If there is a sudden  increase in CurrentTotalUsage then prices will climb rapidly to prevent supply of CPU from being consumed.

We could consider variations on this algorithm, such as resetting DailyAvgTotalUsage to CurrentTotalUsage anytime CurrentTotalUsage is greater than DailyAvgTotalUsage. This would cause the averaging algorithm to respond quickly to increases in demand while still gradually lowering the price over 24 hours if there is no new demand.

A user looking to acquire 1% of the CPU supply for 30 days would pay a price equal to: MAX(P(CurrentTotalUsage+1%),P(DailyAvgTotalUsage+1%))) — MAX(P(CurrentTotalUsage),P(DailyAvgTotalUsage)))or more simply put, they would need to pay the delta between the total amount of rental revenue collected at the current utilization and the total amount of rental revenue expected to be collected at the new utilization level.

# Migrating from REX

The new design is made possible because, unlike in REX, it isn’t possible for the “CPU” to be withdrawn from the rental market. The REX algorithm must balance the needs of both borrowers and lenders. In the process lenders end up waiting 30 days for leases to expire or potential renters end up without any EOS for rent because lenders have asked for their EOS back. There is no simple solution that creates ideal simplicity for both renters and lenders under the current REX model.

The most direct way to resolve this is to gradually shift the percentage of CPU allocated under the current model to the new model via “inflating the CPU supply” over time. This can be achieved by implementing a new action in the system contract that allows CPU allocation to be rented and then allocates  “virtual cpu-stake”  which dilutes the total CPU staked (whether owned or rented) to existing CPU. This does not increase the EOS supply, instead it merely adjusts the parameters that determine the ratio of CPU allocated to each account. Currently, the system contract connects this 1:1 to EOS staked to CPU, but the underlying EOSIO protocol only knows about relative CPU weight (the weight assigned to your account divided by the sum of all weights assigned to all accounts).

If the supply of “CPU” created by the new resource market gradually grows to 100x the supply of EOS staked to CPU, then the new rental market would effectively control 99% of EOS CPU time. Eventually staking EOS to CPU and NET could be deprecated and removed as everyone moves to the CPU/NET rental markets.

The proceeds from the new CPU rental market could then be directed to people staked in REX just like name auctions and RAM market fees. This solution could make CPU available immediately and at reasonable prices. Over time utilization of the REX market will decrease and the new CPU market will take over.

If adopted by the community, those who own EOS  and stake for themselves would have to shift to renting CPU from the new market as their existing staked  EOS would have a decreasing share of the total CPU market.  I would propose the CPU be phased into the new market over a one year time periodto give people a chance to migrate their CPU resource strategy.

Ultimately, the ability to stake EOS for CPU and rent EOS from REX could be deprecated in favor of the new proposed CPU market.

Everything that applies to CPU can also apply to the NET market which has the same dynamics as the CPU market.

# Usability for End Users

Many applications and wallets have already  adopted the first-authorizer-pays model for CPU, eliminating the headache for the end user having to consider renting or staking for CPU bandwidth. This new proposal would mirror similar platforms where the application providers, that are renting services from cloud providers, cover their costs via a number of monetization strategies such as subscriptions, advertising, or product sales.

# Conclusion

The proposed CPU rental market will  stabilize CPU prices, reduce rental CPU costs, and increase predictability of CPU access. The proceeds from CPU and NET rentals can still be distributed to those staked in REX. However, the biggest change would be the gradual loss of the ability “own CPU” forever via staking EOS for a share of CPU. Combined with the ability of service providers to cover CPU costs on a per-transaction basis for their users, this will make EOSIO based networks the easiest to use and most cost effective solution on the market.

