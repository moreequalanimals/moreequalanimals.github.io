---
title: Infinitely Scalable and Private Digital Cash
desc: How to securely send cryptocurrencies without an internet connection and no fees.
image: /assets/img/bitcoin-disolve.jpg
tags: blockchain bitcoin government economics
---

Blockchain technology has enabled a host of digital currencies and smart contract platforms with the promise of bringing free market solutions to government interference in the most critical components of a stable society: its money and contracts. The challenge of the past decade has been to understand the uses and limitations of the technology that Satoshi introduced. In my previous article on [[The Ideal Cryptocurrency]] I documented my belief that Bitcoin and other blockchain technologies are unable to solve the problem of free market money at scale and set a new standard for an idealized cryptocurrency. The inability to scale without centralization means currencies like Bitcoin will suffer the same fate as gold and silver coins.



An ideal cryptocurrency should act like copper coins that you can transmit instantly anywhere in the world without a fee. I use copper in the analogy because gold and silver are not sufficiently divisible without adoption of financial intermediaries, aka banks. Unless Bitcoin transaction fees fall substantially then Bitcoin is far less divisible than gold, silver, and copper.



I have been investigating solutions to this problem and believe we are on the cusp of a technological solution. Imagine for a moment that instead of using your private key to sign a transaction to transfer your Bitcoin you could just give someone your private key and know, with a very high degree of certainty, that the other party does not retain a copy of it. With software tools that enable this kind of interaction millions of transactions per second could occur in complete privacy with a potentially lower risk of counterfeit than the paper money we have used for centuries!



Now imagine that if at any time you have any doubts as to your sole possession of the private key you could pay a fee to transfer the token to a new key you do trust. It would be like taking a suspect bill to a bank and paying a fee to mint a fresh bill.



Modern cell phones and M1 Macs contain secure enclaves with key attestation. This allows third parties to validate that a particular key is managed by the secure enclave, and critically, to know how many times it has been used to sign something. This is a powerful primitive and this article will demonstrate how that primitive can be used for cryptocurrencies. With a few additional hardware primitives we could eventually create even more powerful and secure solutions.



**Digital Cash**

A signed application running on a secure operating system can generate and encrypt a private key using an attested hardware key. Using Apple’s attestation features other applications can receive a copy of the private key and know (with high confidence) the sender has deleted the key. How does this work? The sender’s device requests a public key from the receiver device that is attested to belong to a particular application.  The sender then re-encrypts the private key to the receivers public key and then deletes the senders private key and the hardware keys. The receiver gets the key and optionally verifies that the coins exist on a public blockchain.



The application would enforce that a private key could not be sent on to any other user once it had been revealed.



This system is clearly not perfect. A sufficiently advanced attacker would be able to extract the private key from their local device without the application knowing it had been read. Then they could use this to attempt a double spend attack by sending the private key to multiple parties and then use the private key to move tokens on a blockchain before the receivers notice.



With the right firmware on a Yubikey like device such attacks could be limited to state actors and would be incredibly expensive. Each private key would be like a serial number on fixed denomination paper bills. Given the cost of the attack is much greater than the value of an individual private key there is no economic incentive to even attempt it.



Fortunately, 99.99% of people are not sufficiently advanced attackers. This means that receiving a private key controlling some blockchain based tokens could be safer than receiving a paper bank note. It means that transaction finality can be at the speed of light instead of waiting for a block confirmation. It means transfers can occur without the internet and with complete privacy. It means no transaction fees.



A final layer of security is to integrate a decentralized web of trust and every private key would retain a history of “owners”, known only to the application and not to the user. This history could be used to create an automatic risk score. As long as the key is only being transferred among people in your local trust network then the risk of an attack can be quite low even without any hardware based security.



Inside block.one there is an Innovation Lab where we play with ideas like this. We built an application we call [Mojey](https://github.com/eosio/mojey) which allows you to transfer digital tokens via bluetooth and Messages. No internet connection is required. The application is secured using Whitebox crypto, Apple’s key attestation, and various code scrambling techniques and jail break detection algorithms. For various reasons block.one will never publish this application to the app store, so it was released as open source software. I would like to thank Todd and Thomas for their effort in building this prototype. 

**Limitations**

Despite the many great things about digital cash, it does lack one property that many people rely upon: the ability to backup your tokens. Because the software enforces that your private key exists in only one place at a time you run the risk of losing your device. In this situation it really is like cash and coins. 

Until the M1 Macs were released this entire system depended upon the good graces of Apple allowing such an application in their store. With the M1 Macs we now have a (relatively) open platform, but that relative openness compared to iOS also reduces some of the protections provided by iOS as well as the conveniences of a mobile device. 

Clearly digital cash implemented in this manner is not as secure as a confirmed Bitcoin transaction, but it just might be more secure than an unconfirmed transaction. It may even be more secure than dealing with paper money. If you are doing business with known parties and they pass you a "counterfeit key" then you can simply contact them and ask them to make good on their payment. This leaves the only risk to using digital cash to those accepting payment from anonymous sources.

I believe that it is worth exploring less than "perfect" security solutions if they enable powerful new use cases with acceptable levels of risk / reward. We have thrived for thousands of years with less than perfect security on our money, why should we ignore the potential practical trade offs made possible by slightly less than perfect security? After all, many people leave their doors unlocked or secured by a half inch of pine that is trivially kicked in. Lets not let perfect be the enemy of good enough.
