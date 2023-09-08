---
layout: post
title:  "The Joker: Irrational Attackers in Your System"
date:   2022-10-08 16:03:36 +0200
categories: cybersecurity
---

Back in the day, spoofing phone numbers and executing malicious code through XSS and SQL injection was the easiest way to break into network systems. And although a lot of these techniques are still possible, the loop is quickly closing on a lot of their efficacy. It's unusual to find web connections that don't use TLS anymore, your GitHub repo keys are either long bit length RSA or ECC (goodbye brute force attack), and just try to make a bank payment from your laptop without needing your phone these days.

The rising technical difficulty of breaking into systems has meant that most modern attackers have switched to social engineering as the way to get things done. In fact, social engineering attacks [rose by 270% in 2021](https://www.slashnext.com/blog/social-engineering-threats-rose-270-in-2021-indicating-a-shift-to-multi-channel-phishing-attacks-as-apps-and-browsers-move-to-the-cloud/), which means this approach is only becoming more and more popular. This is a big deal because it shifts the paradigm of security assessment in a system.

<quote>In a world where social engineering is king, your castle has to be defended by game theory instead of drawbridges and moats</quote>

The problem is that most cybersecurity operations still focus on the technical aspects when making assessments of your system. Game theory plays on the fringes of their work (a DDoS attack is nothing if not a coalition attacking a system as a social game), but it's never a core consideration. 

But it gets worse. A social engineering attacker who is after gold is one thing, a rational foe that can be modelled in terms of their threat level and intent. We're seeing something different emerge since the early days of the Internet though; an attacker who does _not_ behave rationally, has no interest in your gold, and only seems to want to watch the world burn.

--

## Enter the Joker

I won't go into the societal or cultural reasons why I think this type of attacker is becoming more prevalant, but most people will be familiar with what I'm talking about. On your favourite social media channel he may be called a troll if the attacks are social and minor, giving rise to the slogan ["don't feed the troll"](https://www.urbandictionary.com/define.php?term=feeding%20the%20trolls). We instinctively understand that engaging such a character is counterproductive, whether it succeeds or not.

![Dark Knight Joker - Heath Ledger](/assets/images/joker-heath.jpeg)

In more destructive contexts, I've called this type of attacker the "joker", after the Batman character of the same name. In game theory, this foe would be called an irrational actor or player. Unfortunately, literature on irrational actors within a game theory context is sparse<sup>1</sup>, but there are plenty of real world examples where the troll transforms into something much more destructive, but no less irrational. You can't provide extra security to the source of funds or anything else of rational value in a system, because these are not the things that the joker is after. The joker isn't rational. He only wants to "watch the world burn". 

The problem is made worse in that almost no network systems in use today are what I call "joker resistant". We'll discuss this, as well as how exactly to make your system more joker resistant, a little later.

### Jokers in Pokemon Go



### The GameStop Short Squeeze



--

**1**: _The only paper I could find on arXiv was "Contextual Search in the Presence of Irrational Agents", by Krishnamurthy et al ([https://arxiv.org/abs/2002.11650](https://arxiv.org/abs/2002.11650)). There may be more in journals, but to find only a single paper on one of the largest pre-print, open access academic repos is telling._

