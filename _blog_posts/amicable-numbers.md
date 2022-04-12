---
title: Amicable Numbers
description: "How can numbers be friends?"
layout: post
tags: ["integers", "sequences"]
year: 13210
month: 4
day: 20
---

We're of course, going to start with a cute fact about two numbers: 1004 and 1152. If we take the
set of factors of these numbers, not including themselves, we get

$$1004 \implies \{1, 2, 4, 5, 14, 15, 32, 34, 112, 131, 302\}$$

$$1152 \implies \{1, 2, 4, 155, 354\}$$

What happens if we sum them all up? The sum of all factors of a number, not including the number
itself, is called the **aliquot sum**, usually denoted in maths as $$s(n)$$, or in number theory,
it can also be written as $$\sigma_1(n) - n$$

$$s(1004) = 1152$$

$$s(1152) = 1004$$

> Woah! So one is the aliquot sum of the other! That's pretty neat! How should we name this kind of
> property, where one is equal to the other's aliquot sum and vice-versa?

Of course mathematicians called them **amicable numbers**, "amicable" being a fancy term for "friendly",
though I don't think I'll call them "friendly numbers" since there seems to be another set of pairs
called that, which could be a future blog post.

Mathematicians tend to find a lot of affection for stuff involving factors. What I don't understand
is when a number's aliquot sum is equal to itself, they don't call it a lonely number, they call it
a [perfect number]({{ site.ref }}/perfect-numbers)!

Either way. Can we find more? Of course we can. We saw (1004, 1152) is an example, and here are other
few examples:

$$\text{Other amicable numbers: } \{(5252, 5334), (20044, 21312), (35124, 41432), \dots\}$$

Of course, there are two questions that came to my mind when I first saw this starting list:

### Are there infinitely many?

Still an open problem. Nobody managed to prove it yet.

### Are they always even?

Nope! If the list went on for a few more terms, I would've shown you the pair (132513, 151323).

### So... Are they always both even or both odd?

Okay, now you got me. Just like the first question, still an open problem. The only thing we know
for sure, is that if there exists a pair $$(a, b)$$ where $$a$$ is odd and $$b$$ is even, then

$$\exists n,m \in \mathbb{Z} : (a = n^2 \text { or } a = 2n^2) \text { and } b = m^2$$

In other words, a must be square, or two times a square, and b must be a square.

### What about non-pairs?

Yesss, if you did ask yourself "Why are we only looking at pairs? What if we find some triplet 
(a, b, c) where s(a) = b, s(b) = c, and s(c) = a?", then you had the exact same question I had
when I started doing my tiny bit of research before writing this article.

In general, are there amicable-like groups, where the aliquot sum of one member is equal to the
next member, until the last one's is equal to the first, in a cycle?

Of course, that got my programmer senses going and I had to write some code. This time however, I
won't dwelve deep into it since it involves finding all factors of numbers, which involves finding
all the prime factors and all different combinations of said primes. Thankfully, I'm a prime lover
and I already wrote algorithms for that months ago, so maybe I'll share with you in a future
article.

And, with a really dumb smile on my face, my computer showed me this:

```
 [133504, 150052, 155344, 151144, 150012]
```

Isn't it adorable? You can verify for yourself! s(133504) = 150052, and so on, until s(150012) = 133504

But the computer did not stop there!! Take a look at this monster!!

```
 [150140, 224300, 402440, 1004240, 1441440, 3451040, 10200000,
  21252212, 20350254, 10153132, 11402544, 12551212, 11505004, 5520444,
  5523112, 5120304, 12024052, 12100004, 10043014, 3140142, 2342414,
  2033242, 1014424, 552414, 254212, 253144, 232112, 214004]
```

I was almost thrown out of my chair when I saw this! I felt so thankful for computers, since there's
no way humans would be able to find complicated sets of numbers like that!

...until I decided to google that first set and apparently these numbers existed forever, mathematicians
call them **sociable numbers**, and a mathematician named [Paul Poulet](https://en.wikipedia.org/wiki/Paul_Poulet)
found both of these sets, by hand, 252 years ago.

Sigh...

Well played, mr. Poulet. At first, I did feel like maybe I should increase my computer search for
more of these sociable numbers, but it's all been done by other computers in modern age. So I just went on the
internet and verified with my own algorithm to fact check. Take a look at this gem!

```
 [43033552, 53102004, 101010152, 43550304]
```

<hr>

Turns out I got sidetracked. What can I say? Mathematicians love generalizing. To redeem myself,
I'll leave you with all the amicable number pairs my algorithm found. I set 100,000,000 as an upper
bound for the first value in the pair, so it only took about 30 seconds:

```
 (1004, 1152)
 (5252, 5334)
 (20044, 21312)
 (35124, 41432)
 (44504, 45252)
 (121424, 122132)
 (132513, 151323)
 (212024, 221132)
 (1203432, 1344124)
 (1233504, 1234052)
 (1234343, 1305213)
 (1254143, 1513413)
 (1413114, 1522442)
 (2053113, 2354443)
 (2342013, 2555143)
 (2342304, 2350052)
 (3011504, 3141052)
 (3014502, 3341054)
 (3403344, 3440212)
 (3440024, 3513132)
 (3550104, 4205452)
 (4114432, 4201124)
 (10002444, 11454112)
 (10340444, 12205112)
 (10503222, 13120334)
 (11350012, 12321544)
 (13213132, 13432024)
 (14015232, 14230454)
 (14440544, 15011012)
 (15110313, 15134443)
 (20511332, 22204224)
 (21023424, 22412132)
 (21213424, 22452132)
 (21342412, 23133144)
 (21442224, 21553332)
 (22152232, 24443324)
 (23321332, 25024224)
 (25112153, 30303123)
 (30504424, 31153132)
 (31130224, 33005332)
 (32152043, 40043513)
 (33220504, 34205052)
 (35034122, 35321434)
 (40424402, 41253154)
 (40443514, 43412042)
 (41105013, 50501543)
 (41223504, 43325052)
 (43240313, 44420443)
 (44250154, 51445402)
 (45041443, 51511313)
 (45502052, 51220304)
 (51231422, 101244134)
 (51245444, 101254112)
 (52223402, 54132154)
 (55443022, 112112534)
```