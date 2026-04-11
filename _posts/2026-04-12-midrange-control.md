---
layout: single
title: Optimal midrange and control manacurves
date: 2026-04-12
author: esteve
tags: [magic]
---

Following the [post](https://tarragoesteve.github.io/redlua/2026/03/28/aggro-manacurve.html) about the aggro manacurve, I wanted to investigate further and propose an optimal manacurve for midrange and control decks.
We are using the same [script](https://github.com/tarragoesteve/manacurve) with the same hypothesis as we did. In the original post, I defined aggro in limited formats as a deck that wants to win by turn 5.

For the current post, we will define midrange as a deck that is able to compete with aggro in the early turns and is optimizing for turn 6.
In other words, it will try to get over the aggro deck, but would be smashed in the late game by a control deck.

Our control deck will be optimizing for turn 7, winning the late game and being able to go stop midrange but most likely losing agains aggro strategies.

This are the resulting deck compositions:

| Deck     | Lands | 1-drops | 2-drops | 3-drops | 4-drops | 5-drops | 6-drops |
|----------|-------|---------|---------|---------|---------|---------|---------|
| Aggro    |   17  |    5    |    9    |    6    |    3    |    0    |    0    |
| Midrange |   18  |    0    |    9    |    6    |    5    |    2    |    0    |
| Control  |   18  |    0    |    6    |    6    |    5    |    4    |    1    |


After having the decks configurations, I wanted to evaluate their performance along the first turns of the game.
It was no surprise to me that the aggro deck is the one having more impact on the first 5 turns, midrange in the 6th and control in the late game.

![]({{site.baseurl}}/assets/images/posts/2026-04-12 midrange-control/optimal from turn_3_ to_7.png)

We are doing a lot of hypothesis to get to this numbers, as all the cards of the same mana value have the same impact or not considering card draw.
When drafting and building your deck, you should use this as a guideline, not a hard rule.


Bonus fact, for very fast draft formats, as vintage cube, it might be helpful to have the optimal 4 turn deck configuration, an  hyperaggro configuration:

| Deck       | Lands | 1-drops | 2-drops | 3-drops |
|------------|-------|---------|---------|---------|
| Hyperaggro |   16  |    11   |    8    |    5    |
