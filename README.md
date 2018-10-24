# Arkanoid JavaScript

Project developed in 24 hours.


## Objective of the project

The main objective of the project was working with the JS canvas and try to develop every aspect of the game from scrap, even the "physics".

![](/images/screenshot1.png)

## Challenges

The main challenge of the game was to implement the robound physics of the ball with the non-staatic objects. In this particular case the collision with the player bar.

After a ton of failed implementations and with some paper sketches, I realized a quite interesting solution.

### The solution

To simplify the problem the collision box of every object in game is a rectangle, in particular the rectangle (or square) of the sprite. So, the collision to solve was between to rectangles.

The basics of this collisions where simple. If the rectangle bounds of the ball are at the height and between the vertical bounds of the bar, invert the y component of the velocity of the ball.

But, what happens when the ball collides with the side of the bar? I needed some way to detect if the ball was colliding with the side or with the top.

After a million failed "solutions", I made this sketch:



In this sketch I realized that when the ball's box entered the bar's box another reactangle was created between them. This rectangle was the key!

- If the rectangle formed has the width bigger than the height, side collision

- If the rectangle formed has the height bigger than the width, side collision

With that simple idea the collisions were solved. It is still bugged but it works nicely.

## The rules

This Arkanoid is no diferent from others. 

The objective is simple, break all the bricks to get to the next level without losing all the lifes. If the ball touches the ground the player lose a life.

Some bricks will drop power-ups. This power-ups modify some mechanics when they are taken:

- ![](/resources/power1.png)    : The bar gets longer
- ![](/resources/power2.png)    : The bar gets shorter
- ![](/resources/power3.png)    : The ball moves faster
- ![](/resources/power4.png)    : The ball moves slower

## Additional features

The levels off the game are designed with a 2D array, so any level can be created by creating new arrays.


```
//0 --> No brick.
//1 --> Random brick.

level2[0] = [1,1,1,1,1,1,1,1];
level2[1] = [1,1,1,1,1,1,0,0];
level2[2] = [1,1,1,1,0,0,0,0];
level2[3] = [1,1,0,0,0,0,0,0];
level2[4] = [0,0,0,0,0,0,0,0];
level2[5] = [0,0,0,0,0,0,0,0];
```
The code over references the next level:

![](/images/screenshot2.png) 


