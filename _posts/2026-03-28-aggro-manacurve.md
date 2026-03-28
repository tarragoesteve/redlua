---
layout: single
title: Manacurve for an aggro deck
date: 2026-03-28
author: esteve
tags: [magic]
---

After Turin 2026 LTQ, I've been wondering what's the optimal manacurve for an aggro deck. I played an aggro archetype (Merfolk) without enough 2-drops. After doing some research, I couldn't find a clear answer so I had to solve it myself.

First of all format speed. After searching on 17lands.com, I could find the distribution of games that ended in a turn for the format I was playing (ECL).

![]({{site.baseurl}}/assets/images/posts/2026-03-29-aggro-manacurve/ECL_speed.png)

I already had a [script](https://github.com/tarragoesteve/manacurve) that given an input of desired sequences, output the optimal deck composition. It required a final turn to do the optimization, so I set it to 5 after reviewing the format speed data.

To do the optimization, we first need an heuristic on how impactful a given card is. I ended up using the following formula.

```
    Impact(Mana Value) = 1 + Mana Value + (1 - probability of casting card of Mana Value on curve)
```    

The first term was trying to account for the card, the second for the mana and the third for the risk of not being able to cast that card on curve.

After computing all possible [sequences](https://raw.githubusercontent.com/tarragoesteve/manacurve/refs/heads/main/sequences/sequences_turn_5.csv) (7172), this where the top ones:
```
    22.8;[0, 1];[0, 1, 1];[0, 3];[0, 4];[0, 5]
    22.76;[0, 1];[0, 2];[0, 3];[0, 4];[0, 1, 4]
    22.75;[0, 1];[0, 2];[0, 1, 2];[0, 4];[0, 5]
    22.73;[0, 1];[0, 2];[0, 3];[0, 1, 3];[0, 5]
    22.69;[0, 1];[0, 2];[0, 3];[0, 4];[0, 2, 3]
    22.68;[0, 1];[0, 2];[0, 3];[0, 2, 2];[0, 5]
    22.5;[0, 1];[0, 1, 1];[0, 1, 2];[0, 4];[4]
    22.5;[0, 1];[0, 2];[0, 1, 1, 1];[0, 4];[4]
    22.48;[0, 1];[0, 1, 1];[0, 3];[0, 1, 3];[4]
    22.48;[0, 1];[0, 1, 1];[0, 3];[0, 4];[1, 3]
```

It made sense to me as a magic player, so I proceed with the optimization. This were the results I obtained:

| Mana Value | Quantity |
|:----------:|:--------:|
|    Lands   |    17    |
|      1     |     5    |
|      2     |     9    |
|      3     |     6    |
|      4     |     3    |

I was very satisfied to get 17 lands. Once I tested with a larger final turn, the number of lands started to increase. I think I will have to weight different turns to get the numbers for mid-range and control decks. I will come back when I have them :)
