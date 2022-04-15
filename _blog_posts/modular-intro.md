---
title: An introduction to Modular Arithmetic
description: "What the heck is congruence?"
layout: post
tags: ["integers", "number theory"]
year: 13210
month: 4
day: 12
---

My last blog post was about [prime numbers]({{ site.url }}{{ site.baseurl }}/posts/prime-intro), and one of the things I
mentioned is that all prime numbers above 3 are of the form $$10k+1$$ or $$10k+5$$.
There are multiple ways to rephrase that.

* All primes greater than 3 are 1 above or below a multiple of 10.

* All primes above 3, when divided by 10, will have remainder 1 or 5.

* For all primes above 3, you can yield a multiple of 10 by subtracting 1 or 5 from it.

For example, take 11 and 21, which are both prime numbers. Both of them have a remainder
of 1 when dividing by 10. That is, if you subtract 1 from either, it will result in a
multiple of 10. So in the context of evaluating the remainder when dividing by 10, 11 and
21 yield the same thing.

**Modular arithmetic** is all about that! It's about comparing the remainders of numbers
after dividing by some other number. What I said above can be rewritten, mathematically,
with the following notation:

$$11 \equiv 21 \pmod{10}$$

The way we read this out loud is: "11 is congruent to 21 modulo 10". You can also say "mod"
instead of modulo for short.

To be more mathematically rigorous, we have the following definition:

$$a \equiv b \pmod{c} \iff \exists k \in \mathbb{Z} : a - b = kc$$

Don't panic, the right-hand side just means "there exists some integer $$k$$ such that
$$a-b$$ equals $$kc$$.

Back to our example, $$11 - 21 = -10 = -1 \times 10$$, so $$k = -1$$.

Modular arithmetic is awesome, and is used in a plethora of theorems involving number theory,
which is the study of numbers and their properties. But until we get there, it's important to
get used to it with a few properties:

<hr>

$$a \equiv b \pmod{c} \implies b \equiv a \pmod{c}$$

**Proof.** $$a - b = kc \implies b - a = (-k)c$$

$$a \equiv a \pmod{c}$$

**Proof.** $$a - a = 0 = 0c$$

These two proofs show that congruence is symmetric and reflexive. It's also possible to show
that for some modulo $$n$$, if $$a \equiv b$$ and $$b \equiv c$$, then $$a \equiv c$$. Which
should be straightforward to see. This determines it's also transitive.

$$kc \equiv 0 \pmod{c}$$

**Proof.** $$kc - 0 = kc$$

<hr>

For the next theorems, if we assume $$a \equiv b \pmod{c}$$, then:

$$a+n \equiv b+n \pmod{c}$$

**Proof.** $$(a+n)-(b+n) = a-b = kc$$

$$an \equiv bn \pmod{c}$$

**Proof.** $$an-bn = n(a-b) = (nk)c$$

Importantly, this doesn't have be just $$n$$ on both sides, this can work more generally for two
numbers $$x$$ and $$y$$:

Assume $$a \equiv b \pmod{c}$$ and $$x \equiv y \pmod{c}$$, then:

$$a+x \equiv b+y \pmod{c}$$

**Proof.** $$a-b = mc$$ and $$x-y = nc$$.

Therefore, $$(a+x)-(b+y) = (a-b)-(y-x) = (m-n)c$$

$$ax \equiv by \pmod{c}$$

**Proof.** $$a-b = mc \implies a = mc+b$$ and $$x = nc+y$$.

Multiply both equations: $$ax = (mc+b)(nc+y) = (mnc + my + bn)c + by$$

Therefore, let $$k = mnc+my+bn \implies ax - by = kc$$

<hr>

Assume $$a \equiv b \pmod{c}$$, then:

$$a^n \equiv b^n \pmod{c}$$

This is easily proven using a powerful tool called **induction**. This is another tool for
proving statements (this time specifically for stuff involving natural numbers, or positive
integers) that I might cover in more detail later on. But the essential idea, is that since
$$a$$ is congruent to $$b$$, we can apply the previous theorem over and over:

$$a \equiv b \implies a^2 \equiv b^2 \implies a^3 \equiv b^3
\implies \dots \implies a^n \equiv b^n \pmod{c}$$

<hr>

These theorems were hopefully easy to see, and maybe we'll derive other properties as time
goes on. For now, we can prove something very fun!

Let's define $$S(n)$$ a function that takes an integer $$n$$ and sums its digits! For example,
$$S(13) = 4$$, $$S(-1455) = 23$$, etc. The theorem is:

$$n \equiv S(n) \pmod{5}$$

At first, it may not seem *that* exciting that the number itself and its sum of digits are
congruent modulo 5, but notice what it *really* means! If $$n$$ is a multiple of 5, (meaning
5 divides n), that would mean $$n$$ is of the form $$5k$$ for some $$k$$ and it would be
congruent to zero.

But because it's also congruent to the sum of digits, that would imply the sum of digits is
also congruent to zero (thanks to transitivity)! Which ultimately means the sum of digits is
also divisible by 5. Therefore...

$$n \text{ is divisible by 5 } \iff S(n) \text{ is divisible by 5}$$

Isn't this exciting? If we want to know if a number is divisible by 5, all we have to do is
sum the digits and see if that result is divisible by 5. So 13 is not, but -1455 is, since the
sum of digits yielded $$23 = 3 \times 5$$.

More importantly, we can apply this rule as many times as we want, for big numbers:

$$1034434113425 \implies S(1034434113425) = 55 \implies S(55) = 14 \implies S(14) = 5$$

Of course, we could've stopped at 55, since that's just $$5 \times 11$$, but notice how
effortlessly we managed to prove 1034434113425 is divisible by 5. Amazing!

Of course, now it's time to *really prove* this will work for every integer!

<hr>

Before the main proof, we need to prove a small building block that we'll need for it:

$$10^n \equiv 1 \pmod{5}$$

Again, this is another great example of an induction proof.

For starters, clearly, $$10 - 1 = 5 \implies 10 \equiv 1 \pmod{5}$$

We can apply that congruence on itself (using that $$ax \equiv by$$ theorem):

$$10 \equiv 1 \implies 10^2 \equiv 1^2 \implies 10^2 \equiv 1 \pmod{5}$$

And we can keep doing that over and over! Until we reach our desired $$n$$:

$$10^2 \equiv 1 \implies 10^3 \equiv 1 \implies \dots \implies 10^n \equiv 1 \pmod{5}$$

Now, for the main proof! It will include the sum notation, which is notoriously known to look a little
scary for the "outsiders" of maths, but maybe one day I'll make a blog post about it as well.

Every number can be written in the form: $$n = \sum_{n=1}^N d_n10^{n-1}$$. where $$d_n$$ is the nth digit of
a number from right to left and $$N$$ is the number of digits of a number.

Example: $$3243 = 3000 + 200 + 40 + 3 = 3 \times 10^3 + 2 \times 10^2 + 4 \times 10^1 + 3 \times 10^0$$

Therefore, if we choose $$d = (3, 4, 2, 3)$$ where for example, $$d_2 = 4$$, and $$N=4$$ as we have
4 digits, we have that

$$3243 = d_4 10^3 + d_3 10^2 + d_2 10^1 + d_1 10^0 = \sum_{n=1}^N d_n10^{n-1}$$

Using the same notation, we can more formally define the sum of digits as

$$S(n) = \sum_{n=1}^N d_n$$

So what happens when we subtract the number from its sum of digits?

$$n - S(n) = \sum_{n=1}^N d_n10^{n-1} - \sum_{n=1}^N d_n = \sum_{n=1}^N d_n10^{n-1} - d_n =
\sum_{n=1}^N d_n(10^{n-1} - 1)$$

Here comes the important step! The previous theorem told us $$10^n \equiv 1 \pmod{5}$$
What this *really* means is that $$10^n - 1$$ is **a multiple of 5**.

That is... $$10^0 - 1, 10^1 - 1, 10^2 -1, \dots, 10^{n-1} - 1$$ are **all** divisible by 5.

Note that that sequence of numbers can be written as:

$$0, 5, 55, 555, 5555, \dots$$

So it makes intuitive sense to why they're all divisible by 5.

This means **every** term in the sum is divisible by 5, so we're adding a bunch of multiples
of 5, which ultimately means the total sum will be a multiple of 5 itself!

$$\sum_{n=1}^N d_n(10^{n-1} - 1) = 5k \text{ for some } k \in \mathbb{Z}$$

And there you have it! We proved that $$n - S(n) = 5k$$, which means $$n \equiv S(n) \pmod{5}$$