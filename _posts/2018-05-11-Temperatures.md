---
layout: post
title: Solution of the puzzle Temperatures
---

In this puzzle, I will show you how to do compare values in an array in Haskell.

### Description

In this puzzle, you are given an array of temperatures. The goal is to find the nearest temperature from zero.

### Solution

We read the input line and we split it in array with the function `words`. Now we have an array of strings which represent the temperatures. In order to convert a string into an int, we use the `read` function which as it says reads a string and tries to convert it into the asked datatype. We use map to apply this function to all our values of our array.

Here is the code

{% gist e4acd5da7a6ef4cb3941a43834155032 %}

The first thing to do is to write the edges cases. As it is said, if we have no values at all, we must output "0".

If the list of temperatures is not empty then it is asked to return the closest temperature from zero so the temperature which absolute value is the minimum. Another condition is that if two numbers are equally close to zero, positive integer has to be considered closest to zero. In order to find the minimum that respects these two conditions. I created a custom compare function that returns `x^2 - x`. Why `-x`. Let's say that we have 5 and -5 then 5 will be the smaller because `5*5-5 < 5*5-(-5)`. I import comparing from `Data.ord` in order to tranform my function `compare ::Int -> Int` into a function `Int -> Int -> Ordering`.