---
title: An introduction to Mathematical Proofs
description: "The proof is left as an exercise for the reader."
layout: post
tags: ["logic"]
year: 13210
month: 4
day: 15
---

Today, we'll talk about mathematical proofs!

Most of the time, in school, we're taught things as is. 

> The angles in a triangle always sum up to $$\pi$$

> The quadratic equation will always give you the two solutions

> If ABC is a triangle where AB forms a right-angle, $$a^2 + b^2 = c^2$$

Most of the time, you're never taught *why* these things were true. And I'm not here to blame, I
know these proofs can get tricky, especially when taught to a class of students that already don't
have any interest in maths, unfortunately.

But every mathematical statement needs to be proved! And I'll be going through a lot of proofs
when writing blog posts, so it's important to go ahead and give a short explanation and motivations
(with examples) to the most common types of mathematical proofs!

## Direct Proof

This one is straightforward. No funny business, just straight up going from a hypothesis to a
conclusion. There aren't any fancy logical tools needed for it.

### Example: An even number plus an odd number is an odd number

Even numbers are of the form $$2k$$ for some integer $$k$$. For example, 30 is even because it
can be written in the form $$2 \times 13$$. Odd numbers are 1 more than an even number. So they
can be written as $$2k+1$$ for some $$k$$. 11 is odd because $$11 = 2 \times 3 + 1$$.

So let $$2m$$ be an even number and $$2n+1$$ be an odd number. We can evaluate their sum:

$$2m + (2n+1) = (2m + 2n) + 1 = 2(m+n) + 1$$

Since $$m+n$$ is just an integer, we managed to show that this sum is of the form $$2k+1$$, and
therefore it is odd.

## Proof by Contradiction

> If the earth is spherical, how does water not fall off?

> If the earth is flat, how did nobody reach the edge?

Regardless of what the earth really is. both of these individuals are using the same type of
proof for their argument. First, we assume something is true, then we realize that it
leads to an absurdity (again, we're not here to question the validity of the first one), also known
as a **contradiction**.

These types of proofs have all kinds of names: Indirect proof, "by way of contradiction",
reductio ad absurdum, etc. And they revolve around assuming a statement is true. Then we develop
our proof until we reach a point of contradiction. Our assumption led to a contradiction, which
is not allowed in maths. So our assumption must be false!

### Example: If $$n^2$$ is even, then $$n$$ is even

Let's assume, by contradiction, that we have some $$n$$ such that $$n^2$$ is even, but $$n$$ itself
is odd.

If $$n$$ is odd, then it can be written in the form $$2k+1$$ for some integer $$k$$. Therefore, the
square is

$$n^2 = (2k+1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1$$

Note that $$2k^2 + 2k$$ is just an integer, so we managed to write $$n^2$$ in the form $$2m+1$$ for
some integer $$m$$, meaning $$n^2$$ is an odd number. But that contradicts our original hypothesis
that it's even!

Therefore, our assumption is false, and we can't have $$n^2$$ even but $$n$$ odd. So if $$n^2$$ is
even, $$n$$ must also be even.

## Proof by Cases

> I really enjoy seeing my friend happy. So playing against them is great! If I win, I'm happy.
If they win, they'll be happy, so I'm happy! It's a win-win!

Sometimes, a proof requires us to break the problem down into various cases. Most commonly, 2 or
3 cases. One fun fact is that this type of proof is heavily dependent on the *law of excluded
middle*, which states "either something is, or isn't". But that could be a thing on its own
in a future blog post.

### Example: If $$n$$ is an integer, then $$n^2 + n$$ is even

Since $$n$$ is an integer, we know it has to be either even or odd. So it is either of the form
$$2k$$ or $$2k+1$$. Let's evaluate both cases for $$n^2 + n$$

$$n = 2k \implies n^2 + n = (2k)^2 + 2k = 4k^2 + 2k = 2(2k^2 + k)$$

$$n = 2k+1 \implies n^2 + n = (2k+1)^2 + 2k+1 = 4k^2 + 4k + 1 + 2k + 1 = 2(2k^2 + 3k + 1)$$

In both scenarios, we reached something which is a multiple of 2, and therefore both cases gave
us an even number for the result. So $$n^2 + n$$ is even.

## Proof by Induction

> Look at this huge line of dominos! Notice how each one is separated in such a way that one would
knock off the next one. So as soon as I knock the first one down, they're all going to fall off
eventually!

This one is special, and it's only really useful when we're talking about integers (and 99% of
the time, positive integers).

The idea behind induction is proving two things: We prove that a statement is true for some 
specific value, usually called the "base case". Then, we show that if our statement is true for
any value above our "base case", then it should also be true for the next value, usually called
the "induction step". Joining these two together will prove that the statement is true for
every value above the base case.

### Example: The sum of all integers from 1 to $$n$$ is equal to $$n(n+1)/2$$

We want to prove this is true for any $$n$$ above and including 1. So $$n=1$$ is our base case.

$$1 = 1 \times 2 / 2$$

Sometimes, the base case won't be very enlightening (like here), so it doesn't hurt to try this
for greater values (but only to visualize what's going on, the base case is proven, so all we
*really* need is the induction step).

$$1+2 = 3 = 2 \times 3 / 2$$

$$1+2+3 = 10 = 3 \times 4 / 2$$

$$1+2+3+4 = 14 = 4 \times 5 / 2$$

Seems to hold! Now, for the induction step, we'll assume our statement is true for some $$n$$,
then prove that it *will* be true for $$n+1$$.

Assume $$1+2+3+ \dots + n = n(n+1)/2$$

Then, $$1+2+3+ \dots + n + (n+1) = n(n+1)/2 + (n+1)$$. Let's do some algebra:

$$\frac{n(n+1)}{2} + (n+1) = \frac{n(n+1)}{2} + \frac{2(n+1)}{2} = \frac{n(n+1) + 2(n+1)}{2}$$

However, note that

$$\frac{(n+1)(n+2)}{2} = \frac{n(n+1) + 2(n+1)}{2}$$

So we managed to prove that $$1+2+3+ \dots + n + (n+1) = (n+1)(n+2)/2$$, which is exactly
what we wanted to prove!

Induction proofs are the tricky the first time you hear about them. But the more you read and
exercise them, the more comfortable your brain will be with them.

