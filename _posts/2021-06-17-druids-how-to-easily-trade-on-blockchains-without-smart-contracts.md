---
layout: post
title:  "DRUIDs: How to Easily Trade on Blockchains without Smart Contracts"
date:   2021-06-17 16:03:36 +0200
categories: blockchain
---

_This article is also available on the Zenotta Tech Blog, and can be found [here](https://medium.com/the-zendesk/druids-how-to-easily-trade-on-blockchains-without-smart-contracts-ac1af79a34df)._

--

Your phone’s lock screen tells you it’s just about to hit 1am, and you know somewhere in the neglected backroom of your tired brain that you need to shuffle to bed if you’re going to get all 7 hours of sleep. That Solidity contract is so close to done, though, and a last cup of coffee is probably all you need to get it over the line. So you pour, you sit, you sip and you code.

..

The phone has changed to 1:34, but it doesn’t matter because the contract is done. I mean, you should probably check it on the test net, but it’s such a small change and the siren call of your bed sheets has only gotten louder since you found the bottom of your coffee mug again. It’s fine, deploy it.

..

You close your editor and are about to do the same to the lid of your laptop when it suddenly catches your eye. Line 632. Oh God. Is that a bug in the code, a weakness in the logic? But if it’s on line 632 that means it’s in the major pay-out function. And that means it’ll affect all the funds for a contract.

The contract that’s worth more than your annual salary.

![Steve Harvey - Oh Snap](/assets/images/harvey-oh-snap.gif)

The desire for sleep drains from your body. It’s quickly replaced by an adrenaline that will only be used when you prowl the job boards for your saviour from all this madness. Crypto is for the birds. The phone will have to berate you a few hours more.

## Error 404: Justice not Found!

When Ethereum burst onto the crypto scene it made the promise of Turing complete contracts, where you could write anything you could dream up. This was incredible for flexibility but, as any engineer or lawyer could tell you, with flexibility comes complexity. Smart contracts are often riddled with bugs, just like any other programming system, but unlike other programming systems these problems are immutable and affect people’s bank balances. And people get mad when your smart contract bugs affect their bank balance in the wrong direction, which has happened a [number](https://www.coindesk.com/ethereum-learn-dao-attack) of [times](https://hackernoon.com/how-the-170-million-ethereum-bug-could-have-been-prevented-819053c3b2cb) in Ethereum’s history.

It’s one of the reasons smart contracts have yet to see wider adoption in mainstream use cases like company share agreements or simple escrows. Even the stuff that only smart contracts can supposedly do, like [fractionalising the ownership of a property](https://www.youtube.com/watch?v=Z-CZLuLPZwI), haven’t made much of a dent in the mainstream economy.

<quote>If code is law, then bugs are the new miscarriages of justice</quote>

But there is another way, one which allows you to make simple, atomic trades of any kind without the need for bug-riddled smart contracts.

## Why We Can’t Already Have Nice Things

Traditional UTXO model blockchains are super simple. Here’s a picture of Alice paying Bob some good ol’ fashioned Bitcoin, as seen by the Bitcoin UTXO:

![Alice to Bob Token Transfer](/assets/images/alice-to-bob.jpeg)

There are no pesky, buggy smart contracts to worry about here because this transaction is atomic, which means it’s executed on the blockchain in a single step. Boom. Done.

The problem with this picture is that it looks like Alice is just incredibly kind, and gave Bob the Bitcoin out of charity. Nothing in the Bitcoin ledger tells us that Bob got the Bitcoin because he delivered the most expensive pizza ever made, and that’s because Bitcoin doesn’t have the ability to encode this information in its transaction structure<sup>1</sup>. It’s just not possible in traditional UTXO blockchains.

Ideally, what we really want is something like this:

![Alice to Bob Token Transfer, Bob to Alice Asset Transfer](/assets/images/alice-to-bob-to-alice.jpeg)

In this picture we can see that Alice traded with Bob for an asset (which could be a different token type, a data asset or a digital representation of her pizza order) as one step, and that the transaction happened atomically. By keeping the trade asset generic we also ensure that there’s no need for a smart contract; anything can be traded for Alice’s tokens.

Unfortunately, as lovely as this scenario would be, we have a few problems:

- if anything can be traded for Alice’s tokens, how do we make sure that her specific 5 tokens are traded for Bob’s specific asset in such a way that both parties are happy with what they’re receiving?
- how do we make sure that neither can get duped?
- how do we make sure that no one can claim they didn’t receive their goods after the transaction is complete?

The solution, of course, is the mighty DRUID.

## Enter the DRUID

In a UTXO blockchain model, Alice’s 5 BTC existed long before her transaction with Bob. In fact, her 5 BTC have gone from transaction to transaction and every Proof-of-Work-secured step has been recorded since the genesis block.

If Bob’s asset could be recorded on the blockchain too, it would also have existed long before his transaction with Alice. So what we actually have is 2 distinct paths for 2 distinct asset types, which just happen to meet at this 1 point in time that Alice and Bob want to be trading buddies.

In order to solve all our problems around the trade, all we need to do is make sure that Alice and Bob tell some third party (let’s call him Charlie) that they agreed to this trade at this point in time. Let’s call that their **declaration** to Charlie.

In fact, their declaration doesn’t even have to be all that fancy. It just has to be a value that Alice and Bob both agree on (say, a concatenation of hashes from each participant in the trade) and that can be attached to each of their transactions. If Charlies thinks this declaration is on the up-and-up (and no one is in fact bankrupt) then the trade can proceed with Charlie as the transaction’s notary. This declaration is our _Double Resolution Unique ID_ (DRUID).

<quote>Alice and Bob’s agreed upon declaration for accepting a trade is a Double Resolution Unique ID (DRUID)</quote>

With the DRUID attached to their transactions and attested to by Charlie, no one can come back at a later date and say they didn’t get their fair share because it’s the DRUID they originally agreed to and signed into said transaction.

The process for an atomic trade therefore looks like this:

![DRUID Charlie](/assets/images/druid-charlie.png)

No more complicated smart contracts, no more bugs, no more problems. Just a simple, atomic trade at the cost of a single hash.

## Wait, Where Did Bob’s Asset Come From?

Bob’s asset is virtually anything that can be recorded on a blockchain and put into a transaction. This could be a hash value representing something important, a public key for authentication, or a data asset. It could even be a token-for-token trade, although in most current blockchains the structure only supports a single token and so it makes little sense for there to be such a trade.

At Zenotta, where we’re focused on bringing a true data economy to the blockchain space, DRUIDs make sense when trading a token for a data asset. What’s important to note though is that a DRUID can be implemented in a simple manner regardless of the blockchain, so long as the transactional system is capable of holding the DRUID value as a field. You could even implement DRUIDs into a smart contract’s logic, if that’s your jam.

If DRUIDs can be implemented into a blockchain’s structure at a transaction level and can facilitate atomic trades, then maybe your days of fearing transactional bugs will finally be over. Maybe you won’t need to fear that deploy button anymore. Maybe, just maybe, you’ll get all 7 hours and the job boards can linger in loneliness a little while longer. Maybe then this crypto stuff won’t be so bad.

--

**1**: _Sure, it’s possible to include extra info in transaction metadata. But how can a third party trust that the extra info is in fact true, and that Alice didn’t actually receive a pound of cocaine instead of the described pizza?_
