---
layout: post
title: Solution of the puzzle Horse Racing Duals
---

In this puzzle, I will show you how to do operations on arrays in Haskell.

### Description

You have a racetrack and you organize a race with two horses. In order to have an interesting race you must select the two horses that have the lowest difference of powers.

### Solution

The first thing to do is get the inputs. The first line is easy it is an int that represents the number of horses. It's trickier to get the horses array. In order to do that, we use the function `replicateM` which performs n times an action and gathers the n results in an array.
Once we have this array we need to use the arrow going left to convert it from `[IntIO]` to `[Int]`.

{% gist af121493203b15ffaa320dabf3c9a452 %}

Now that we have our inputs, we can tackle the problem. Let's say for example that we have  `[5, 3, 8, 9]` as the list of horse powers. The list of all spreads of powers would be `[5-3, 8-3, 9-3, 8-5, 9-5, 9-8]`. The problem is that it will take O(n²) to compute this list.

Let's say that we have a sorted list `[h1, ..., hn-1, hn, hn+1, ...]`, let's take hn, the two horses that are the most similar in terms of power are hn-1 and hn+1. So our list above could be rewritten `[5-3, 8-5, 9-8]` which can be computed in O(n) time.

So we sort the list of horsepowers. We create the list of spreads to do this we use `zipWith`, we take as inputs `tail hpSorted` and `hpSorted`. If we take the data of our previous example, it will do `zipWith (-) [5, 8, 9] [3, 5, 8, 9]` which is equivalent to `[5-3, 8-5, 9-8]`, we take the minimum of this list and we display it.

{% gist 569dfc0a2159f73c8f39f9cc19e298bb %}

You can see the complete solution [here](https://github.com/siminio/Codingame/blob/master/easy/horseRacing.hs)
