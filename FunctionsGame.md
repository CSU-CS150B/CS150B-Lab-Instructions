# Lab 8 - Functions Game

Welcome to Lab 8, today's lab will have you reconstructing a series of functions in order to get a game (that's already been made for you) properly running.
A couple notes for this lab:
1. You can move around lines of code freely using a keyboard short cut. Hold down one of these keys (depending on your system) and the arrow keys to move code.
     - On Mac: option key
     - On Windows and Linux: Alt key
2. Remember that the tab key is how you indent lines of code. 
3. You do NOT need to add or delete ANY lines of code for this lab. To get full points, all you need to do is move lines around. 


## Step 1: Fixing Helper Functions
The add and isEven functions are out of order. Put them back in order so that the logic functions correctly and returns the correct values.

## Step 2: Fix checkNums
The checkNums function is also out of order, but it's a little more complicated than the last two. For this one, make sure the string is being
assembled correctly, using the example below the function. Take note of the function calls to add and isEven; they have to be working before you can finish
this step. Also make sure that the indentation for the if statements are correct. Finally, make sure the return is in the right place.


## Step 3: Make the game run
For this final step, you have to reassemble request and startGame to make everything run smoothly. For startGame, make sure the variables are assigned first. Remember
that when you call a function, that function runs in its entirety before the code that called it continues. In this case, when you call game, the entire game will play
out before the last bit of runGame executes. 
Once you have the game running, try changing the values of health, attack, and defense to see how that effects the game. 

Take a look at the Game file to see all the different function calls and how they're used (even if you can't understand the entire program yet).
