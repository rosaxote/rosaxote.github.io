---
layout: post
title: Time is a Corkscrew on the Complex Plane
published: true
category: main
---

{{ page.title }}
================

<p class="meta">3.26.26 - Miami/Orlando</p>

Look at your desk. How is it held together? Likely, if it is not injection molded furniture, by screws. Screws are one of the strongest forms to hold things together -- from the walls of your home to the hinges on a rocketship.

In this post, I want to explore how time is like a corkscrew holding the universe together, and the implications.

### First, a few concepts

First, I must introduce a few concepts (I will write as if the reader has little background in math/physics, to start from the ground up). 


##### Euler's constant *e*

One of them is the incredible number *e*, Euler's constant. This number had oft been bandied around in my undergraduate chemistry, biology, and math courses, but as a teenager I had zero appreciation for it (if my professors had emphasized its importance, I must've snoozed right through). Only much later, after I had started a company, taught a business course, and seriously confronted the idea of "growth" did I realize its significance. 

*E*, first discovered by Swiss mathematician Jacob Bernoulli in the late 1600s, is integral to the idea of growth. Bernoulli discovered that when you compound a value at a certain interest with increasing frequency, the final value does not go infinitely up -- it approaches a limit. This limit, across all values, is a function of the approximate number ~2.718.  

$$(1+r/n)^n \to \approx 2.718^r \text{ as } n \to \infty$$

Where $$n$$ is the frequency of compounding and $$r$$ is your interest rate.

As the simplest example, if you invested $1 at 100% interest per year, after one year you will have $2. If you increase the number of times you compound during the year, that final number will go up. However, it will not grow linearly. As you compound two, ten, a hundred times, the final value will approach ~$2.718(...).

$$
\begin{aligned}
&\text{Compounded once a year: } \$1.00 \times (1 + 1)^1 = \$2.00 \\
&\text{Compounded twice a year: } \$1.00 \times (1 + 1/2)^2 = \$2.25 \\
&\text{Compounded 12 times a year: } \$1.00 \times (1 + 1/12)^{12} \approx \$2.613
\end{aligned}
$$


This number, ~2.718, turns out to be a constant in compound interest calculations. No matter what numbers you plug in, the end result will be a function of this constant. The full compounding equation is: 

$$P \left(1 + \frac{r}{n}\right)^{nt} = A$$

(where the initial principal = $$P$$, annual interest rate (decimal) = $$r$$, time (years) = $$t$$, compounding periods per year = $$n$$, and the final amount = $$A$$)

Which, as n approaches infinity (aka continuous compounding), simplifies to:

$$P(2.718...)^{rt} = A$$

Decades later, Bernoulli's compatriot Leonhard Euler expanded on the applications for this constant, showing that it crops up wherever there is continuous compounding. **Where there is continuous compounding, something is either growing or decaying.** 

Euler assigned this constant the letter *e*, and it became known as Euler's constant. *E* is fundamental to our later understanding of such disparate fields as population growth, radioactive decay, statistical normal distribution (and yes, [the Secretary problem](https://rosaxote.github.io/main/2026/02/27/optimal-stopping.html)).

So let's keep this number in mind.

##### The complex plane

The second concept I want to introduce are imaginary numbers and the complex plane. 

Most numbers we encounter are real - we can perform calculations with them and get concrete solutions, whether the number is negative, positive, or irrational (cannot be expressed as a simple fraction, such as &pi; or *e*). 

However, there is a class of numbers where there is no "real" solution, such as the square root of -1 (multiplying two negative numbers gives you a positive number, which is why finding the square root of -1 seems like a misnomer). We will use $$\sqrt{-1}$$ as a building block, and call it $$i$$. Any multiple of $$i$$ is called an "imaginary" number.

This belies the fact that imaginary numbers are very real and essential in quantum mechanics, signal processing/telecommunications, electromagnetic fields, and much more.

When you combine a real number and an imaginary number, like so: 

$$a + bi$$

(where $$a$$ is the real number and $$b$$ is some multiplier of $$i$$), you get a "complex" number.

The reason I'm providing this background is to explain the complex plane. When you try to graph complex numbers, you can't just map it on a line like a normal number; you must have two axes: one for the real part and one for the imaginary part. By convention, the horizontal (x) axis represents the real part and the vertical (y) axis represents the imaginary part. 

You'll see that mapping $$i$$ maps rotation.

Each multiple of $$i$$ corresponds to a 90 degree rotation on the complex plane, because $$i$$ is $$i = \sqrt{-1}$$. That means if you start at 1, your only trajectory is:<br>

$$i$$ or (1 x $$i$$) → a 90 degree turn<br>
-1 or ($$i^2$$) → a 180deg turn<br>
$$i$$ or (-1 x $$i$$) → a 270deg turn, and<br>
1 or (-1 x -1) → a full 360deg turn.<br>


### NATURAL GROWTH IS ROTATION ON THE COMPLEX PLANE

So what does any of this matter? 

Euler found an interesting relationship between *e* and $$i$$. He found that complex numbers following the formula $$\cos(x) + i\sin(x)$$ are equal to: 

$$e^{ix}$$

where $$x$$ is the angle in radians.

The most famous extrapolation from this is Euler's Identity, where if you set $$x$$ to equal &pi;, the formula boils down to:

$$e^{i\pi} + 1 = 0$$

also called "the most beautiful theorem in mathematics."<sup>1</sup>

We will not dive deep into that in this post, except to observe that there is a very strong relationship between $$e$$ and $$i$$, and thus natural growth can be mapped as rotation on the complex plane.

In other words, natural growth, under constraints, turns into rotation.

### TIME ALSO GROWS

We tend to think of time as independent and linear, but we know from Einstein's equations that space and time are linked. While the universe is unimaginably large relative to us, and time flows (relatively) smoothly within this space, the universe has ultimately (likely) spatial limits too. That means, under those spatial limits, the growth of time must be constrained.

Thus, under spatial limits, the growth of time must turn into rotation.

**Time must cycle.**

### IMPLICATIONS FOR THE NATURE OF THE UNIVERSE

I think there is a reason in various world religions there is a concept of rebirth and cycles of time. 

If time (and space) rotates, it is like a corkscrew holding things in our universe and beyond together. Without the rotation, everything in the universe would fall apart.

*What happens if there are no spatial limits?*

*What happens if one escaped these cycles (as described in some Eastern religions)?*

*What is the nature of these rotations?*

There are many questions and things to ponder, to savor for another day.


<hr>

<sup>1</sup><small>When $$x$$ equals &pi;, because $$\cos(\pi) = -1$$ and $$\sin(\pi) = 0$$, the formula boils down to: $$e^{i\pi} = -1$$. Or put another way, $$e^{i\pi} + 1 = 0$$. </small>
