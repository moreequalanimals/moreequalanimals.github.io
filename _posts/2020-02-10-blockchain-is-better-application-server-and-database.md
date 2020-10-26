---
title: Blockchain is a Better Application Server and Database
image: /assets/img/appserver.png
desc: By the time you do everything necessary to secure a traditional web application and database you will have implimented a blockchain.
tags: eos blockchain database 
---

Traditional web application infrastructure was designed with security as an afterthought and for over 25 years companies have been attempting to patch a fundamentally insecure architecture. This architecture was designed with the assumption that a server could be trusted and secured,  but years of experience has taught us that no server is safe from external attacks, let alone internal compromises. Stated another way, a server is fundamentally centralized.

We used to think that the “problem” was the connection between the user and the server and so we introduced SSL and HTTPS. But then we discovered that hackers would compromise the database and steal passwords. So we set about storing hashes of passwords, but then we discovered hackers would brute force the password after stealing the hashes. Then we introduced password rotation so that the password would be changed by the time it was brute forced, and on and on.

Businesses are spending billions of dollars attempting to protect their servers and databases and despite all of this effort there is still no easy way to audit systems and ensure businesses operate as they are intended.

Block.one is building blockchain software to keep databases and user accounts secure against unauthorized access and unaccounted for modifications.  With blockchain users adopt highly secure private keys which are stored in secure hardware and used to sign every user interaction rather than simply authenticate a connection to a server.  The blockchain creates an immutable log establishing an absolute and deterministic order in which user inputs were received and smart contracts provide deterministic business logic which ensures consistency across all systems.

The future Block.one is creating eliminates passwords and expensive auditing saving companies billions of dollars, preventing identity theft, and offering increased reliability and audit-ability for all.

I have maintained for years that every multi-user website can benefit from the adoption of a blockchain backend.  Contrary to popular opinion, blockchains don’t have to be slow, inefficient, databases nor do they have to operate on a censorship resistant, open access basis. A blockchain can provide a company huge improvements in security, audit-ability, transparency, and overall integrity of the business process even if the blockchain is entirely operated by the company itself and none of the contents of the blockchain are made public.  This article aims to shine a light on the true value of blockchain in corporate environments and show the way forward for the blockchain industry.

# Common Misconceptions

Within the blockchain industry many people are of the opinion that blockchains only provide benefit when they connect many parties who don’t trust each other. They have the opinion that traditional database technologies can already do everything required to ensure business  integrity. Stated another way, they view traditional database replication and “data integrity” guarantees as sufficient.  In the process they either ignore or are ignorant of the fundamentally different security and integrity guarantees that blockchains offer:

1.  Commitment to Global Sequence of Events
2.  Deterministic Execution of Business Logic
3.  Tight Coupling of Business Logic & Data  Integrity
4.  Elimination of Passwords

In traditional business application architectures the business logic is separated from the database.  There is usually an application server, such as Node.js or J2EE, which is provided a password to modify the database. It is the role of the Node.js server to authenticate the user via a password or multi-factor authentication scheme.  Once the application server authenticates the user it issues a session token which is used to authenticate future user interactions until it times out or some element of the session (such as IP) changes.

It should be obvious that this traditional design performs all database operations via a single login/password managed by the application server.The application server is responsible for implementing its own authentication scheme with the ultimate end use. It should also be obvious that there are usually multiple parties who could gain access to the username and password. The database admin can assign and revoke credentials to many different application servers and/or individuals.

Advanced systems ensure that in a horizontally scaled system each application server has its own username/password and in some cases it could even use a Public Key Infrastructure and Hardware Security Modules (HSMs). However, even here  the database only authenticates the connection to the application server. In order  to provide an audit log, it would have to record the entire datastream of the secure connection. However, even  this log only records the “reads and writes” requested by the application server which has already lost all information about the original users intent as expressed to the application server.

An auditor reviewing such a system would have no way of knowing whether the application server (e.g. Node.js) was following the proper business logic and properly authenticated the ultimate end user. The Node.js process could “log” user actions into the database so that an auditor could attempt to reproduce the same calculations, but such a log is not tamper-resistant  on its own and carries with it no independently verifiable authentication that the end user in question actually authorized the actions it logs.

An attempt could be made to log every user connection, but since the user often transmits their password over the connection, these logs would end up creating a honeypot for leaking user credentials. More sophisticated systems could encrypt these logs so that only the auditor can read them.

Assuming the audit log was not tampered with, the auditor would have to run the same action sequence through the application logic to verify that the resulting database state matched. This implies that the application server would have to be implemented in a deterministic manner.

# Deterministic Computation is Hard

While it may appear to be “simple” to write deterministic code, in practice all common computer languages are non-deterministic because they allow the developer to access data outside what is stored in the database. This could be something as simple as a timestamp, memory address, environment variable, IP address, or something far more subtle such as the behavior of floating point on the hardware or the order of insertion to a hashtable. In many cases simply accessing in-memory variables of a long-running application server is sufficient to introduce non-determinism. The very act of starting/stopping the application server must be logged and reproduced or every local memory access is potentially non-deterministic during replay.

The truth of the matter is that writing deterministic code is challenging for the best developers trained in the common pitfalls and actively looking for nondeterminism. The typical business application developer would find it difficult or impractical to write in a deterministic manner.

If we go further and assume the application code was deterministic, that the application faithfully recorded user events, we are still left with the challenge of tracking the version of the code deployed at any given time.  Applications are dynamic and frequently updated, therefore the application code itself must also be part of the database state and its updates managed and logged with the same degree of security and audit-ability as user actions. An auditor would then need to have a copy of all versions of the application server code and replay the user inputs through each version upgrading as necessary (and restarting the code whenever it was restarted in the past)

Even if a single application server was able to operate in a deterministic manner both in terms of its implementation and deployment, it would still suffer from a major scalability concern. Only one instance of the application server could ever operate on the database.  Parallel access could be implemented via complex locks, but even the race conditions on the locks would have to be logged and reproduced or two instances of the application logic with different local variables could produce non-deterministic output.

At this point one might be tempted to discard determinism altogether, but absent determinism a single bit of difference could compound over time into massive differences in the final data set. Auditors would be forced to use fuzzy logic and approximate matches and everyone would have to trust that the “fuzzy logic” was good enough.

Of course the only thing it takes to negate all of the effort put into writing and deploying deterministic code is for the database administrator to modify the database directly and without a trace. In some cases a careful updating of the user input log and state can create two different database states that each pass the deterministic test but nevertheless have different and irreconcilable outputs. For example, suppose a professor submits a students grade to the system as an F, and then the student hacks/bribes his way onto the database to change both his grade and the log as submitted by the professor.

# Replacing Passwords

The ultimate goal of any multiuser system that cares about integrity is ensuring that user inputs cannot be forged. The use of username/password or even other subjective multi-factor authentication (such as SMS or Google Authenticator) relies upon the server to conclude that the password matches or that the proper SMS code / email link / authenticator code was entered. It should be obvious that this is a huge problem for the integrity of the system, but just in case I will provide a real world example of just how bad these systems can be.

In 2016 I had an account on a cryptocurrency exchange which was hacked and allowed the hacker to steal tens of thousands of dollars worth of Bitcoin. The hack as observed from my perspective showed up as a “password reset” email being sent to my email, followed by another email that indicated my password had been successfully reset. Then I received an email asking for confirmation of the withdrawal of my bitcoin (with a code/link). Then I received a notice that my withdrawal had been processed.

At first glance it would appear that my email account had been hacked, but that shouldn’t have been possible given my use of multi-factor login on my email. A quick visit to my email security page showed that there was no unauthorized access to my email. I could tell because Google logs and displays all IPs/devices that access my email.

What had happened is that  the attacker intercepted the email as the exchange was sending it before it got to my email account. The application server had no way of knowing that the email was intercepted and therefore authorized the password reset and withdraw based only on the attacker having the one time code generated by the application server.

This same exploit could be used against SMS or any other technique that relies upon something other than a private key controlled by the user. At the end of the day,  the only way to really secure a user’s account is for all users to adopt hardware based private keys as their login credentials combined with a robust and time consuming process to facilitate a secure reset in the event the hardware keys are lost.

At this point a multi-user business application could now sign every user request with the user’s private key, log this signed request in the database, and process it with deterministic code. Even this does not provide the integrity one expects because the entire user request could still be deleted along with any side effects. Imagine hacking the police database and removing the signed request by a police officer when he submitted your ticket followed by all state derived from that request?

At this point an astute engineer would claim that every single problem I raise can be solved by changing the application logic. He would be right, a sophisticated application developer could use a “traditional database”, “traditional application server”, and “common cryptographic primitives” and construct a system that is relatively secure and audit-able. By this same logic an astute engineer could claim that a database is entirely unnecessary and instead everything should be built directly on the file system. Another engineer would point out that performance could be enhanced by coding everything from scratch instead of relying upon application server frameworks like Node.js and J2EE. It is almost as if everything is built out of lower level tech and we might as well design in transistors for maximum performance.

I point to this extreme because it highlights the true utility of higher-level frameworks in accelerating and securing the development of new applications. Few people write their own cryptography libraries or algorithms and those who do are either experts or serve as a cautionary tail when their system is hacked. The cost of developing/redeveloping everything from the ground up can make every application more expensive than building on top of proven frameworks.

# The Benefit of Blockchain Application/Database Servers

The reason blockchains and development frameworks like EOSIO exist is to free the application developers from having to reinvent the “database” in order to build secure applications. Security and determinism is hard, which is why technology is built in layers that abstract the details. EOSIO combines a deterministic execution environment (WebAssembly) with a fast database in the same process. All user actions are signed by their own private keys and logged in a replicated and distributed database with the ability to make public commitments to the block headers.

It is only a matter of time before frameworks like EOSIO are just as powerful and easy to develop for as traditional insecure systems. In many ways,  the architecture of EOSIO is already higher performance than traditional systems by the simple virtue of putting the application logic (Web Assembly) in the same process space as the in-memory database. This creates deterministic stored procedures on steroids.

In the years ahead, Block.one aims to add the tools and interfaces to make deploying your business applications on top of blockchain as easy (or easier) than deploying those same applications on top of traditional business application architectures.

It is clear that adoption of blockchain technology should become a priority for government agencies, public companies, and businesses that have a duty to prevent fraud and/or do financial reporting.  Not adopting blockchain tech in the years ahead will be like a bank not adopting SSL and once the technology is widely available not using blockchain technology could, in my view, be considered negligence.

Today is the time to act. Your businesses and users are not secure and will not be secure without a fundamental change in the way our applications are built. Every day you delay is another day your business is at risk of fraud or hacking.

<sub>Original post and discussion can be found on [[my medium blog::https://medium.com/@bytemaster/why-a-blockchain-is-a-better-application-server-database-architecture-9d7b78730fbb]]</sub>.

