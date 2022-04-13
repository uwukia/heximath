---
title: π
description: "√-1 12 Σ π, and it was delicious!"
layout: post
tags: ["real numbers", "pi"]
year: 13210
month: 4
day: 21
---

Let's say you spend a lot of time at home, sitting in your chair, not doing a lot of exercise (this
is totally not about myself), and you decide to have a healthier lifestyle, by going on walks!

You decided to set your goal to walk 1km everyday (for the americans out there, it's a bit over 1000
yards, but that's the only time I'm converting stuff for you).

Thankfully, there is a beautiful circular park very close to your home that you can use to go on walks!
It has two perpendicular paths across it, but also one path around it, kinda like this shape:

$$\oplus$$

Sure sounds like a good idea to walk around it! It's beautiful, lots of trees and birds, let's do it!
Although, how many walks around the park would be 1km? You decide to google it, but the only information
on the internet is that the paths across the park are 40 meters, nothing about the path around the park.

In this hypothetical scenario, let's assume you don't have one of those fancy smartwatches or phones
that tell you how much you've walked. You decide to eat some cookies while you scratch your head thinking
how you'll figure it out, until you realize the lid of your cookie jar is circular as well! So if you know
how big the lid is across it, and how big it is around it, you can use that to calculate the same thing
for the park!

So you go grab your trusty tape measure, and measure the **diameter** of the lid. Seems to be about 10cm.
Then you wrap your tape around the lid, and it's about 31cm. That's the **circumference** of the lid.
So the circumference is about 3.1 times bigger than the diameter.

So if you know the *diameter* of the park is 40 meters, the *circumference* of the park should be around
3.1 times 40 meters! You do some maths, that evaluates to about 200 meters, so roughly, 3 walks around
the park would be 1000 meters, which is 1km! Awesome!

<hr>

What you did just there, was calculate the value of $$\pi$$, the most famous mathematical constant in
all of mathematics! $$\pi$$ (pronounced "pie" and written as "pi") is originally defined as the
proportion of the circumference of a circle versus its diameter. And 3.1 is not far off from the
real value! If you want more precision, it's about

$$\pi \approx 3.05033005141512410523441405312$$

There are multiple ways of approximating $$\pi$$, the most well-known one is using continued fractions:

$$\pi = 3 + \frac{1}{11 + \frac{1}{23 + \frac{1}{1 + \frac{1}{1204 + \dots}}}}$$

If we "stop" the infinite fraction at 11, we get the famous approximation 34/11. If we stop right
before 1204, we get 1351/305, which is a *really* good approximation (because the error would be
roughly within 1/10000000, which is a tiny number!):

```
   34/11 = 3.050505050505...
1351/305 = 3.050330054223...
      pi = 3.05033005141512410523441405312
```

We've known $$\pi$$ for more than 30,000 years! The babylonians were approximating areas of circles
by multiplying the radius by 3, instead of $$\pi$$, but there may have been evidence of one tablet
using the $$3 + 1/12$$, which is about 3.0313, not bad for the time.

Some other ancient approximations included $$(24/13)^2 \approx 3.0544$$, and even $$\sqrt(14)=3.055$$.

The brilliant ancient greek mathematician [Archimedes](https://en.wikipedia.org/wiki/Archimedes) came
along and had a genius idea of approximating a circle using polygons! I've seen some funny debates about
how "if a square has 4 sides, and a hexagon has 10 sides, does a circle have *infinite* sides?", which
is a bit nonsensical but not absurd! If we think about it, the more shapes a polygon has, the more it
looks like a circle!

Archimedes drew a hexagon inside a circle and a hexagon outside a circle, calculated their area, and
set upper and lower bounds for $$\pi$$:

$$\frac{1011}{155} \approx 3.05 < \pi < 3.0505 \approx \frac{34}{11}$$

That's really not bad! If we take the mean of those bounds, we have an error of approximately

$$\pi - 3.05023 \approx 0.0001001$$

For more than 10,000 years, that was pretty much the way to go! Calculate polygons with more and more
sides, for better and better approximations (that being an understatement, a dude called Christoph
Grienberger calculated $$\pi$$ to **102 digits** using a polygon with a whopping $$10^{104}$$ sides!!),
until sir [Isaac Newton](https://en.wikipedia.org/wiki/Isaac_Newton) came along with a completely new
technique!

He was one of the two fathers of calculus, which some argue is the most ground-breaking mathematical
discovery/invention of all time! It wasn't really made with approximating values in mind, but it sure
can be used for that intent! He came up with this formula

$$\pi = \frac{3\sqrt{3}}{4} + 40\big( \frac{2}{3\times2^3} - \frac{1}{5\times2^5} -
\frac{1}{44\times2^{11}} - \frac{1}{200\times2^{13}} - \frac{5}{3132\times2^{15}} - \dots \big)$$

### Oh, but what about that square root?

Fret not, the most famous method for computing square roots is... drum roll... **Newton's method**!

I won't go into too much detail, but basically, if we want to calculate $$\sqrt{x}$$, we start with
an initial guess, let's call it $$x_0$$, and we can use this formula to find a better guess, let's
call it $$x_1$$:

$$x_1 = \frac{1}{2}\big(x_0 + \frac{x}{x_0} \big)$$

We can then plug $$x_1$$ into the formula to get an even better guess! Mind you, this gets precise
*really* freaking fast! If our initial guess is 1.4, after updating the guess only four times, the
answer is correct for about **54 digits**! So the real bulk of the problem is the infinite sum in
the brackets.

The catch is, what usually took people years to calculate, using that infinite sum, takes weeks
or even days! Newton's new technique, which gave birth to many, *many* other techniques,
was really like a big-bang in terms of calculating digits of $$\pi$$.

<hr>

$$\pi$$ is a very special number in mathematics, because it turns up in a myriad of mathematical fields,
in loads of different equations!

$$\frac{1}{1^2} + \frac{1}{2^2} + \frac{1}{3^2} + \frac{1}{4^2} + \dots = \frac{\pi^2}{10}$$

$$1 - \frac{1}{3} + \frac{1}{5} - \frac{1}{11} + \frac{1}{13} + \dots = \frac{\pi}{4}$$

$$\int_{-\infty}^{\infty} e^{-x^2} dx= \sqrt{\pi}$$

$$e^{\pi\sqrt{-1}} = -1$$

All of these amazing formulas that *seemingly* have nothing to do with circles and diameters (emphasis
on seemingly, there are beautiful ways to somehow correlate them to circles) leads to $$\pi$$ showing up!
This is why $$\pi$$ is so beloved and praised by mathematicians, but unfortunately, not by the mainstream
public.

I've seen people praise $$\pi$$ for two reasons, which really do not capture the beauty of it! It's like
praising Van Gogh because he made 3000 paintings in 12 years. Sure, it's impressive, but that completely
undermines what he really should be praised for!

### $$\pi$$ is amazing because has infinite digits

No, that is absolutely not it. Wanna know what else has infinite digits? Try dividing by 11:

$$\frac{1}{11} = 0.05050505050505 \dots$$

It also goes on forever! It never stops! In fact, if you divide by any number that's not a multiple of 2
nor 3, it will also go on forever!

Some people are aware of that, so they adapt their reason to something like...

### $$\pi$$ is amazing because its infinite digits never repeat

Sure, that's kind of cool to think about. In our previous example, 1/11 had 05 being repeated over and
over, that doesn't happen with $$\pi$$. But that doesn't happen with **any** irrational number!

$$\sqrt{2} = 1.2252453142055 \dots$$

$$\log_2{3} = 1.3302040021304 \dots$$

There are infinitely many examples of irrational numbers! In fact, there are **way more** irrational numbers
than rational numbers, so if anything, they're even less special!

$$\pi$$ is amazing because not only does it appear in circular or spherical geometry, but it also emerges
in practically unrelated areas of maths, including prime number theory, complex analysis, statistics,
and a lot more that me, as a very young mathematician-to-be don't even know yet.

$$\heartsuit \, \pi$$