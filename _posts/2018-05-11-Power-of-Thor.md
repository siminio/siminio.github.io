---
layout: post
title: Solution of the puzzle Power of Thor
---
This puzzle is similar to Power of Thor but this time you have multiple conditions instead of only one condition


### Description


In this puzzle, you have a person and you must make him move to the thunderbolt.  The map is 40 squares wide and the height 18 squares.

The inputs are the initial position of Thor and the position of the light.

At the end of each turn, you must display the direction that Thor has to take :

- "N": North
- "S": South
- "E": East
- "W": West
- "NE": North East
- "NW": North West
- "SE": South East
- "SW": South West


First things we can say is that in order to know the direction we need to compute the delta x and the delta y. Another thing is that we need to update the position of Thor at each turn.

In order to do this, we read the inputs in the main section and create a loop function that will update our position and output the direction.

This function will take the position of the light (lx ly) and the current position of Thor (tx ty). Thanks to this information, we get the direction then with this direction we update the position and eventually we display this direction before calling recursively the loop function (it will stop when Thor reaches the light).


{% gist 417a53544ec79fdb58d850af17a4855f %}

So now let's see how to create the giveDirection function. The direction is the sum of the direction along the vertical axis (north or south) and the direction along the horizontal axis.

{% gist ca0f0cc23611a0b9d711b533749babee %}

To finish, we need to update the position of Thor. In order to do this, let's create a function move. It takes as inputs the position, the delta x and the delta y. Thor can only move one case per turn. This is why I use the function signum which returns -1 if the delta is negative, 0 if the delta is equal to 0 and +1 if the delta is positive.

{% gist f3c822a14b478b6b2a1bf4556e468654 %}

You can see the complete solution [here](https://github.com/siminio/Codingame/blob/master/easy/powerOfThor.hs)