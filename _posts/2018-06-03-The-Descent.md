---
layout: post
title: Solution of the puzzle the Descent
---

In this puzzle, I will show you how to use a recursive function to simulate a loop.

### Description
In this puzzle, you have a starship and must destroy the highest mountain each turn in order not to crash.

### Solution
First, I created a list mountains that contains the heights of the mountains. After I find the index of the heighest mountain and then I print it.


## Creation of the list mountains
To create the list mountains, I used the `replicateM` function which has the signature `replicateM :: Monad m => Int -> m a -> m [a]`. It means that it performs n actions and gathers the results in a list. In my case, there are 8 mountains so I do `replicateM 8 $ do`. In the do block, I use getLine to get the input then I convert it into an `Int` with the read function.
The read function takes a string as input and you must specify in what you want to convert it for example for an Int it will be `let mountainh = read input_line :: Int`.
Note that instead of doing `let mountains = replicateM...`, I did `mountains <- replicateM...`it is necessary in order to have a list of type `[Int]` and not a list of type [Int IO].

## Finding the index of the highest mountain
When the list of heights of mountains is created, I used the maximum function to find the heighest mountain. After, I used the elemIndex to know the index of this mountain. Note that elemIndex returning type is `Maybe Int`. The Maybe type constructor is like a box that can have either Nothing if it has no value or the value itself it it is provided. In our case we know that this value exists so we just need to extract it with the function `fromJust`.
