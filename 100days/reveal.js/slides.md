# Hi there
I'm [@craigsdennis](https://twitter.com/craigsdennis)

[Treehouse](https://teamtreehouse.com) / [That Maker Show](https://thatmakershow.com)




# Lifelong Learning
Don't stop believin'

Note:
You're here tonight! Keeps you healthy. Keeps your mind active and growing.  You kind of have to in this industry.




# I am a teacher
So I kind of cheat

Note:
I've learned so much through necessity. Not necessarily what I want to learn.




## I don't know about you
But I get stuck <!--.element: class="fragment" -->

Overwhelming amount of tech to learn <!--.element: class="fragment" -->

Where do you even start? <!--.element: class="fragment" -->

I'll do it later <!--.element: class="fragment" -->




# Twitter
The student union of online learning

Note:
Online teaching is weird. I stay connected via Twitter.  Follow trends



# #100DaysOfCode
Commit to code 1 hour a day for 100 days

Note:
I researched it and used the hashtag. Keep track via Twitter posts.



# First Idea
I'll make a course project to track #100DaysOfCode study log

Note:
Perfect, multi-dimensional array. It'll encourage students and spread the message. Cuz this is really inspiring people.



<!-- .slide: data-background-image="https://media.giphy.com/media/ifxLK48cnyDDi/giphy.gif" -->
# Next idea
What if I did it too?

Note:
What if I practiced what I preached.



# Duh moment(s)
Time commitment was exactly what I needed <!--.element: class="fragment" -->

An hour is enough time to explore a technology <!--.element: class="fragment" -->

Community is extraordinarily supportive <!--.element: class="fragment" -->

Habit forming <!--.element: class="fragment" -->

Note:
Went from when am I going to do that, to what am I going to do tonight.



# Suddenly...
I have so much time to learn


## Microcontrollers
Adafruit Circuit Playground Express with Microsoft MakeCode <!--.element: class="fragment" -->

* Lasertag <!--.element: class="fragment" -->
* Parent annoyance alarm <!--.element: class="fragment" -->
* Jumpin' Jackpot <!--.element: class="fragment" -->
* Tetherball <!--.element: class="fragment" -->


## TypeScript


## MicroPython
Over a year on my todo list...

* Simon <!--.element: class="fragment" -->
* WhooPy Cushion <!--.element: class="fragment" -->


## ANTLR
Universal Abstract Syntax Tree Parsing through CSS selectors


## Reveal.js
This presentation software



# Give it a shot
And keep me posted




<!-- .slide: data-background-image="http://www.parrygamepreserve.com/images/lazerTag/seriesGroup1_M.jpg" -->
## Let's play some Lazer Tag

Note:
In the 90's this was so amazing.




## Adafruit Circuit Playground Express

10 NeoPixels <!--.element: class="fragment" -->

Infrared Sensor <!--.element: class="fragment" -->

Speaker <!--.element: class="fragment" -->



# Pseudocode

* While playing <!--.element: class="fragment" -->
 * Display health <!--.element: class="fragment" -->
 * On hit, decrement health and make noise <!--.element: class="fragment" -->
* Game over scene <!--.element: class="fragment" -->



# Demo
Pew pew pew



# State

```javascript
const MAX_HEALTH = 10;
let health = MAX_HEALTH;
```

Note:
Health is our only state, and it's global. Sorry.



## Always design a reset

```javascript
function reset() {
    health = MAX_HEALTH;
    light.stopAllAnimations();
    displayHealth();
}
```

Note:
Call this in the very beginning.  Note the shape of the function.



## Debugging trick: bind your reset

```javascript
// NOPE: Technically correct, but note the shape
input.buttonB.onEvent(ButtonEvent.Click, () => reset());

// INSTEAD:  Simply pass the function...it's the same shape
input.buttonB.onEvent(ButtonEvent.Click, reset);
```



## Display the health

```javascript
function displayHealth() {
    light.setAll(Colors.Black);
    for (let i = 0; i < health; i++) {
        light.setPixelColor(i, Colors.Blue);
    }
}
```

Note:
This is your render method



## How to take a hit

```javascript
function takeHit() {
    if (health <= 0) {
        music.playSound(music.sounds(Sounds.Wawawawaa));
        light.showAnimation(light.rainbowAnimation, 4000);
    } else {
        // Quick red flash
        light.setAll(Colors.Red);
        health--;
        displayHealth();
        music.playSoundUntilDone(music.sounds(Sounds.MagicWand));
    }
}
```

Note:
There are great defaults!



## Also bind your takeHit for debugging purposes

```javascript
input.buttonA.onEvent(ButtonEvent.Click, takeHit);
```



## Big Hack Attack

```javascript
// Unfortunately all IR is throwing infrared errors...
network.onInfraredError(takeHit);
```

Note:
Code expects to communicate between devices



## Get it
Code is [available on GitHub](https://github.com/craigsdennis/adafruit-lasertag)
