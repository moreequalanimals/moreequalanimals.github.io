---
title: Trustless Contracts overcome Artificial Restrictions
desc: Anyone designing smart contracts that attempt to rely upon artificial limits, such as fees or time locks, to enforce a certain game theory outcome should read this article first.
image: /assets/img/contract-lock.jpg
tags: eos blockchain economics crypto
---

Smart contracts make the economy more efficient by making it easy to bundle and forward rights and obligations in a trustless manner. This has profound implications for those who attempt to build limitations on transferability of rights into contracts whether in the form of fees, time locks, vote buying, indivisibility, or some other restriction. Anyone designing smart contracts that attempt to rely upon artificial limits to  enforce a certain game theory outcome should read this article first.

Imagine for a moment that you wish to create a token smart contract that charges everyone 2% any time they transfer the token. This is a practically unenforceable restriction. Anyone can create a new contract that accepts deposits of your token (paying a 2% fee) and then reissuing a new transferable token that charges a lower fee or no fee at all. Others can then withdraw tokens from this new contract after performing an unlimited number of transfers and paying a final 2% fee. Most people will accept and trade the feeless token because the contract can be made immutable and there is no trust involved. This is one example of how smart contracts make markets more efficient and bypass artificial restrictions like high fees.

Now suppose you wanted to create a  new token that attempts to lock value in a long-term contract, where your tokens are now staked at different locked-in time periods. It is simple enough to implement the  timelock  just like it is simple enough to charge a 2% fee on transfers; however, it can be just as simple to bypass by use of other smart contracts.

In the time-lock case a new account can be created which locks tokens into the staking contract and then distributes a new tradable token. The tradable token would be valued like a  zero risk bond payable at a future date. Assuming the underlying asset was valuable and there was a demand to trade zero risk bonds, there would be no way to prevent the underlying value of the bond from being sold and/or placed into another smart contract. This is particularlly relevant to my post on [[EOS Blockchain Governance Proposal]].

The EOS RAM market is another example of an asset with an  _artificial_restriction, allowing users to only buy and sell RAM with a fee. RAM can be effectively transferred by simultaneously buying or selling in a single transaction, incurring an effective 1% transfer fee. If someone simply wanted to trade in the  economic value of RAM rather than the utility of RAM, then a trivial contract could be constructed which would issue  RAM-backed tokens that can be transferred without fees. This even creates the potential for a secondary RAM market without trading fees.

The one thing that is not easily bypassed is the utility of the underlying asset. Token-RAM is not the same thing as actual RAM because you cannot actually use Token-RAM to store anything without first convert it to actual RAM and paying the 1% transfer fee (via simultaneous buy/sell). A similar thing could be said for staked tokens, you might be able to trade the economic value of the staked tokens but you would not be able to easily  mirror any extra utility, such as voting rights or CPU time, of the staked token (depending upon the design of such utility).

For example, assume staked tokens provide the utility of voting. A contract that stakes on behalf of a group, and then reissued tokens, would have to “vote as a group”. Assuming each staked balance could only vote for one person, then the entire group would need to organize a meta-vote to determine which way the group would vote. This would provide less utility to minority members of the group because they would be forced to have their stake vote with the majority.

If the stake token system allowed each staked position to divide its vote among many options, then a  liquid-stake token could mirror the meta-vote trivially, and the vast majority of the utility from the underlying staked tokens would be passed on to the liquid-stake tokens.

Even limiting voting to  one vote per staked position  isn’t a true limit. It is trivial for the liquid stake token contract to manage any number of staked positions and cast different votes for each staked position based upon the meta-vote of the liquid token holders.

It should go without saying, but I’ll say it anyway.  These types of solutions should also be carefully considered from legal, regulatory and tax perspectives before being implemented.

# Preventing Management by Smart Contract

One way to frustrate attempts to bypass intended restrictions is to prevent an account from being managed by a smart contract. This can be achieved by requiring all interactions with the restricted contract to be signed by an  actual private key and requiring  only one action per transaction. What this does is reintroduce an element of “trust” by requiring someone to hold and use a private key.

Assume for a moment that our token with a 2% transfer fee blocked all actions originating from other smart contracts. The trust model changes to one of a centralized exchange that reissues a tether-like instrument. This has the potential to fundamentally change the legal nature of the arrangement and discourage work-arounds.

While this approach would likely discourage attempts to work around the limits, the use of secure multi-party computation, hardware security devices, or the utilization of a minimal level of trust is sufficient to achieve the goal of bypassing artificial restrictions. This would also reduce the security and overall flexibility of your contract within the broader smart contract platform.

# Embracing Freedom to Contract

An alternative to fighting market demand for financial freedom is to embrace it in the first place. Instead of attempting to charge a 2% fee, cut the competition off by using a 0% fee.  Rather than trying to prevent RAM transfers, make it transferable. Instead of trying to force one person to hold their stake, make staked positions fungible and tradable.  Fees are only viable to the extent that the friction from workarounds is greater than the cost of the fee or there is some utility (such as market liquidity) which is not easy or possible to reproduce.

On many public blockchains based on EOSIO, the  system token is designed to provide the utility representing a  pro-rata share of the available CPUtime. This underlying utility cannot be provided by a CPU-backed token any more than RAM can be utilized by the holder of a RAM-backed token without first redeeming the token for the underlying CPU or RAM resource.

Imagine there was a market that wanted to lock people into a long-term interest in the value of CPU. It would allow people to stake their CPU today in exchange for more CPU time in the future. In effect, you lend your CPU for a long-term contract and receive interest in the form of CPU time.

Now let’s assume someone had a large sum of money  locked in a one year CPU staking contract  and they had a  liquidity crunch and  needed cash today. In theory they should be able to sell their CPU staking position to others. The value they would receive on the sale would be the  net present value of CPU  delivered in one years time given the projected interest rates. Changes in the long-term value and/or interest rate paid on one year CPU staking would move the value of long-term CPU to a much greater extent than present CPU.

Making  staked positions liquid  doesn’t undermine the  value of aligning voting incentives. If voters holding long-term staking positions act in ways today that impact the expected value of future CPU negatively then everyone holding one year stake will  realize an immediate and painful loss of capital  due to market reaction. On the other hand if their voting decisions today raise future expectations of CPU demand (aka adoption) then they might be able to realize an immediate profit.

Instead of having to wait a year to  _realize_  the profit or loss,  holders in staked positions  realize the predicted long-term consequences  of their present actions immediately. The liquidity of the staked positions in turn makes more people willing to stake by reducing the average yield paid on staking and, at the same time, increasing the cost of attacking a voting system based on long-term staking.

A voting system that requires tokens to be staked for 10 years, with no trustless liquidity options, would have low participation rates, making it cheaper for someone to buy a small amount of sacrificial tokens, stake them for 10 years, and then attack the network. The same attack on a liquid staking solution would be much more expensive.  Once again, the legal, regulatory and tax issues may affect how such a solution can be implemented in practice.

# Conclusion

Smart contracts should embrace freedom and  avoid adding artificial limits, which can be trivially bypassed. It is possible to charge some fees, but only to the extent that the fee is more convenient than the workaround.  Making staked positions liquid retains the incentive for long-term thinking of voters while increasing voter participation.  Real-time market feedback on the long-term consequences of present day governance decisions is likely more powerful than making voters  wait until the future arrives to realize their gains or losses.  This leverages the wisdom of the crowds  in punishing voters who mistakenly believe their actions will improve long term value by causing losses today rather than in the future after it is too late to correct.

_Disclaimer: Everything in this post is my opinion and not that of my employer or anyone affiliated with it. Do not assume anything in this post will be implemented or adopted by any blockchain. Anyone considering implementing the proposed solutions should consult relevant advisors to address any legal, regulatory or tax consequences._

<sub> Original post and discussion can be found on [[my medium blog::https://medium.com/@bytemaster/how-trustless-contracts-overcome-artificial-restrictions-f8cc939faeb6]]</sub>
