---
layout: post
title: Solution of the puzzle Mars Landers Ep1
---

This puzzle is really easy. We will see how to display a different response based on a condition.

### Description

The goal of this puzzle is to make land a spacecraft securely on a platform. It is an introduction of the puzzle "Mars Landers episode 2" which is more complex. You have different inputs like the horizontal speed, the vertical speed, the x and y coordinates, ... But in our case, we just need to take care of the vertical speed and the fuel.

To make it land securely, the vertical speed when landing should be equal or less than 40m/s. At the same time, we have a limited amount of fuel so we don't want to burn fuel when it is not necessary.

So let's create a function that does this. This function will take a number as an input (the vertical speed) and return a string that will display later. Note also that we need Ord to be able to compare the vertical speed with our limit (here 40 m/s). We can use the guards instead of a condition if else it's more elegant to write this way.

First condition, vspeed is less than 40 m/s, we do nothing, we let the spacecraft fall. Otherwise, we use full power to lower the vertical speed.


{% gist 13d1d46b2e435b4b9ab1d6d05785ef06 %}

Last thing, we call this function in the main function and give the absolute vertical speed as argument.

You can see the complete solution [here](https://github.com/siminio/Codingame/blob/master/easy/marsLandersEp1.hs)