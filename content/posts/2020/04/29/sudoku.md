---
title: "sudoku"
date: 2020-04-29T20:10:18-05:00
draft: false
author: "jks"
authorlink: "mailto:john@scholvin.com"
tags: [ "programming" ]
---

{{< figure src="/2020/img/sudoku.png" >}}

The other day I did a curbside pickup of some lab glassware---as one does during pandemics---and the guy threw a Sudoku
book in the box. He probably thought he was being nice, or maybe he just had a lot of stock and wanted to get
it off his shelves.

Either way, he couldn't possibly know that I hate Sudoku.

All due respect to the people who love it, really, but to me it's pure drudgery. There's no creativity or
reasoning to speak of, just brute force algorithms and/or dumb luck. It offends me that it usually shows
up in periodicals near the crossword puzzle. That's like sitting down at a high-stakes poker table and the dealer offers
to just cut the deck for the pot instead. Or showing up to a chess tournament and they're playing tic-tac-toe.

[So last night I rage-coded a backtracking algorithm to solve them.](https://github.com/scholvin/sudoku) It took about four hours, the majority of which was
spent on the I/O and the validation function. It takes under 250ms to solve any puzzle I tried, meaning
the time it takes to type the puzzle in dwarfs the solution time by 2-3 orders of magnitude, which feels about
right. AlphaGo or Deep Blue, this ain't.

Really, there was no point to doing this at all, just like there's no point in doing Sudoku.

