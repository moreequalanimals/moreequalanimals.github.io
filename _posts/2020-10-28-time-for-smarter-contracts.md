---
title: It’s Time for Smarter Contracts
tags: blockchain government eos economics
desc: Traditional contracts are fraught with problems, it is time to rethink the structure and enforcability of all contracts whether or not we encode them in software as smart contracts.
image: /assets/img/digital-handshake.jpg

---

Blockchains create entirely new possibilities for managing property rights. Property rights are key to a peaceful society because they define who owns (controls) what. At the end of the day the outcome of all contracts is a transfer of property from one person to another. This is true even in the event of a default because a judge will assign damages which result in the transfer of property.

Rothbard introduced the title transfer theory of contract. Under his theory promises to do things are not enforceable except by reputational damage. His reasoning is that a promise is not a transfer of property and that your will is inalienable. There is a monumental difference between the following two contracts:



1.  I promise to transfer 100 bitcoin to you next Wednesday.

2.  I hereby transfer title to you of 100 bitcoin effective next Wednesday.


To the untrained eye these two statements look similar and appear to be nothing more than semantics; however, one of these contacts can be encoded and enforced by software and the other cannot. Let’s explore the difference.

Under the first case, an individual makes a promise to sign a transaction. This may or may not happen. If it doesn’t happen then no title transfer occurs. The promise can be made without ownership of any bitcoin. Without having a present title to 100 bitcoin, how can one enter a contract regarding that property?

Under the second case, an individual has a present title to 100 bitcoin and places a lien on that title which is lifted next Wednesday. This could easily be implemented as a smart contract which holds 100 bitcoin until the specified time.

If we assume that the only enforceable contracts are those which could be represented on a blockchain that tracks a mapping between real things and their owner then it would fundamentally change how society operates. For starters, fractional (aka fictional) reserve banking systems could not be built! Banking collapses would not be possible.

We are so used to viewing contracts as promises that it isn’t always intuitive to limit contracts to conditional title transfers. If you are not careful it is incredibly easy to fall back into a promise theory of contracts. Even Rothbard fell into this trap in a chapter titled, “Property Rights and the Theory of Contracts”, of his book [[“The Ethics of Liberty”::https://mises.org/library/ethics-liberty]].

Fortunately, there is a framework that ensures that it is impossible to construct an invalid contract, smart contracts. Anything that can be represented as a smart contract is compatible with the title transfer theory of contracts (TTToC). The only thing the courts need to enforce is that the physical property referenced by the smart contract is in control by the owner specified by the smart contract.

Rothbard’s mistake was in his example of a loan for $1000 with a promise to repay $1100 in a year. Let's look at an excerpt:


> Suppose that Smith and Jones make a contract, Smith giving $1000 to Jones at the present moment, in exchange for an IOU of Jones, agreeing to pay Smith $1100 one year from now. This is a typical debt contract. What has happened is that Smith has transferred his title to ownership of $1000 at present in exchange for Jones agreeing now to transfer title to Smith of $1100 one year from now. Suppose that, when the appointed date arrives one year later, Jones refuses to pay. Why should this payment now be enforceable at libertarian law? Existing law largely contends that Jones must pay $1100 because he has “promised” to pay, and that this promise set up in Smith’s mind the “expectation” that he would receive the money.
>
> Our contention here is that mere promises are not a transfer of property title; that while it may well be the moral thing to keep one’s promises, that is not and cannot be the function of law (i.e., legal violence) in a libertarian system to enforce morality. Our contention here is that Jones must pay Smith $1100 because he had already agreed to transfer title, and that the nonpayment means that Jones is a thief, that he has stolen the property of Smith. In short, Smith’s original transfer of the $1000 was not absolute, but conditional, conditional on jones paying the $1100 in a year, and that, therefore, the failure to pay is an implicit theft of Smith’s rightful property.
> 
> - Rothbard



The mistake made by Rothbard is that the title cannot be transferred until the conditions are met, furthermore, Jones cannot agree to transfer the title to $1100 he doesn’t have. If Jones wanted to spend the $1000 he conditionally received from Smith, then the condition would be a lien that followed the $1000. If Jones used the $1000 to buy a laptop from Alice he would have to disclose that he doesn’t have a clean title to the $1000 because he has not yet paid $1100 to Smith. Alice would have to accept the credit risk of Jones not paying Smith and would therefore make the transfer of title to the laptop contingent upon getting the lien on the money lifted. If Jones failed to pay $1100 to Smith in one year, then Smith retains title to $1000 and Alice retains title to the laptop. If Jones keeps the laptop he is a thief. If Alice keeps the $1000 she is a thief. The $100 of interest is an unenforceable promise that only exists as the condition upon which transfer of title to $1000 may be affected. Titles held to money conditioned by different promises are not fungible. This means that there is no efficient way to use encumbered assets as money.

So how would lending work under a consistent view TTToC? Your contract with the bank will be something like: if required monthly payments are not made then title to the house is transferred to the bank. No promises are made, just predefined conditional transfers of assets to which the parties have clean title. Normally, “recourse” bank loans also hold you liable for the difference between what the bank can sell the house for and your loan balance. This arrangement would be invalid because all assets subject to the contract would have to be owned at the time the contract was entered in order to agree to transfer title to those assets. Since the borrower doesn’t have the money to pay cash for the house, she cannot sign a contract that transfers title to the cash. Any promise to pay cash would be unenforceable under TTToC. This means that only non-recourse collateralized loans are enforceable under TTToC.



You don’t have to implement a full up smart contract in order to achieve the benefits of smarter contracts. For example, when you pay cash for a coffee, there are two title transfers. The first contract is when you transfer title to cash, contingent upon a transfer of coffee within a certain period of time. The second transfer is an instantaneous, contingency free, transfer of coffee. There is no need for a contingency on the transfer of coffee because by virtue of the transfer the lien on the cash is lifted.



Promises can be enforced with the conditional transfer of title. For example, I would have no recourse if you promised to sing at my wedding and then failed to show up. The promise is not enforceable because it didn’t involve the transfer of title to property you own. If I wanted to make an enforceable contract, then I would require you to sign a contract that transfers title to 1 bitcoin if you fail to sing. You would likely want me to sign a contract that transfers title to you of 1 bitcoin if you do sing. The act of singing or not singing will determine whether the lien on the bitcoin is lifted or title is transferred.



There is never any risk of non-payment or uncollectable damages for “failure to perform”. Everyone knows in advance what assets are involved in the contract and under what conditions title to those assets are transferred.


Lawyers everywhere could easily start writing contracts that are compatible with TTToC. These would be smarter contracts than we have today and wouldn’t require programmers or complex technology to implement. According to Rothbard, this structure of contract was widely used in the past until governments started interfering with the enforcement. Fortunately smart contract platforms such as [[EOS::https://eos.io]] offer us an alternative means of enforcing these smarter contracts without relying upon governments. What we need is a standardized set of primitives for defining titles, owners, liens, and oracles to report on whether the subjective promises were kept. Combine this with a simple interface for combining these primitives and we could get rid of dumb contracts for ever. Elimination of dumb contracts will vastly reduce the opportunity for disputes and greatly enhance peace, prosperity, and freedom.

I cover this subject in more detail in my up coming book, so please [[subscribe::/posts/why-subscribe]] to be notified when my book becomes available!
