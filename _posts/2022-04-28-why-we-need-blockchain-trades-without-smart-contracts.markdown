---
layout: post
title:  "Why we need Blockhain Trades without Smart Contracts"
date:   2022-04-28 20:12:56 +0200
categories: blockchain
---

Last year June I wrote an article on [how you could trade on blockchains without Smart Contracts][druid-article]. The idea was that if Alice and Bob wanted to perform a trade using the blockchain, they could do it as long as they had an agreed upon unique value (which I call the DRUID, or Double Resolution Unique ID).

In order to facilitate the trade, they'd also need some kind of server to hold this data while they both confirmed they were getting what they each wanted. They need somewhere to check each other's expectations for the trade, in other words. I called this server Charlie, and it's a name that has stuck in our implementation at Zenotta ever since. 

![DRUID Charlie](/assets/images/druid-charlie.png)

This process meant that Alice and Bob could perform a Lightning Network-like trade on an almost purely P2P basis and without needing any Smart Contracts. The problem with this is I never actually explained _why_ you would want this in the first place.

So let's fix that.

--

## Smart Contracts Are Buggy AF

A large promise from cryptocurrencies like BitCoin and Ethereum was that they would disintermediate. They would remove the need for bankers, lawyers, insurance and possibly even governments, because it was _you_ who could do all the things these middlemen were gatekeeping yourself. You were now the one in control. I think this is a great vision, one I agree with and am invested in seeing more of.

While I think BitCoin largely delivered on this promise within the world of banking, I'm not sure the same can be said of Ethereum and the world of law. To be fair, law is far more complex than moving currency from one place to another, but Ethereum's answer in Smart Contracts leaves a lot to be desired for Joe Average.

In the wild, the Turing complete logic of Solidity has led to a number of incredibly expensive bugs and exploits. You can read about the [$31 million bug here][ars-technica], [the DeFi bug worth $162 million here][cnbc], and [a complete bug breakdown here][breakdown]. These are just the top results I found in a quick Google search and I'm sure there are many more in the wild that don't make it to the front page of CNBC's business section.

In short, do you really want to trust your financial and legal infrastructure to a language that can be [destroyed by a junior developer on his first big contract?](parity-fund-freeze-junior)

![oh snap junior](/assets/images/oh-snap-jim.gif)

--

## Smart Contracts Still Need Middlemen

All this, just for Alice and Bob to record a trade of tokens for assets...

"Fine", I hear the naysayer cry, "but what if I already have a rockstar Smart Contract developer? The guy's never made a mistake in our trade contracts in the 5 years I've known him."

"It sounds like you put a lot of trust in him", I reply.

"Of course!"

"But I thought the point of crypto, the big dream, was that you didn't need to trust anyone but yourself..."

In a blind and rabid effort to disintermediate the lawyer, the immature but very powerful capabilties of Smart Contracts have forced us to replace one middleman with another: the Smart Contract developer. The problem is that, unlike the legal profession which vets its members and disbars those who break the rules, software developers are known to "move fast and break things". This is a good trait in a startup looking to grow quickly, but it's not a good approach when you're developing on a data structure with immutability as one of its biggest features.

--

## I Don't Want to Learn yet another Programming Language

And neither do the vast majority of developers out there. Numbers of developers in any given programming language are difficult to pin down accurately, but the average was [18,000 active Solidity devs at the end-of-2021 crypto peak](number-solidity-devs). For reference, this is in an ocean of roughly 27 million developers globally ([or 0.07% of total](market-cap-per-engineer)), so there isn't a vast influx of developers into Solidity. In fact there has actually never been, if we compare the numbers to the more popular languages such as Rust in recent years.

Why is that, given that there's so much money lying around in crypto? 

This is speculation on my part, but I just don't really want to learn yet another programming language (as well as its VM and associated development environment) for simple integration with blockchain functionality. I may be in the minority, but I suspect that many "regular" developers feel the same way, despite the golden allure of the crypto space.

**To be clear, I think complex contract structures will always require dedicated languages (DSLs)**. I just don't think I should need a DSL if all I want to do is send you tokens for some digital asset.

--

## Alice and Bob Deserve Better

If Alice and Bob need to use the blockchain to record the trade of an asset for some tokens, they shouldn't need to retain the services of an expensive Smart Contract developer to do it. They should be able to effect such a trade relatively simply and atomically. They should be able to do it themselves, to live the dream that BitCoin and Satoshi created so long ago.

DRUIDs fulfill the requirements of such a trade, and leave Alice and Bob with much heavier pockets than they'd have if they had tried to facilitate it on Ethereum and Solidity. It's time to drop Smart Contracts for simple trades and start adopting more user-friendly blockchain practices.

![Raining Money](/assets/images/raining-money.gif)


[market-cap-per-engineer]: https://tomtunguz.com/programming-languages-web3/

[number-solidity-devs]: https://medium.com/electric-capital/electric-capital-developer-report-2021-f37874efea6d

[breakdown]: https://medium.com/solidified/most-common-smart-contract-bugs-of-2020-c1edfe9340ac

[cnbc]: https://www.cnbc.com/2021/10/03/162-million-up-for-grabs-after-bug-in-defi-protocol-compound-.html

[ars-technica]: https://arstechnica.com/information-technology/2021/12/hackers-drain-31-million-from-cryptocurrency-service-monox-finance/

[druid-article]: /blockchain/2021/06/17/druids-how-to-easily-trade-on-blockchains-without-smart-contracts.html

[parity-fund-freeze-junior]: https://www.crowdfundinsider.com/2018/04/132537-ethereum-votes-no-to-rectifying-junior-developer-error-that-froze-360-million-in-parity-client-wallets/
