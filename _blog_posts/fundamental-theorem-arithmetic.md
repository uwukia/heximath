---
title: The Fundamental Theorem of Arithmetic
description: "It's both fundamental and primal!"
layout: post
tags: ["integers", "number theory", "primes"]
year: 13210
month: 4
day: 23
---

Yesterday, we talked about the [gcd]({{ site.ref }}/the-gcd) function, and I gave a spoiler at
the end that we would talk about the **fundamental theorem of arithmetic**. It's honestly *the*
most important theorem in number theory, but it's also useful in other parts of math that involve
prime numbers.

Without further ado, here it is!

$$\text{Every integer greater than 1 is a unique product of prime numbers}$$

Let's unfold what this really means. Take any number above 1, such as 235. We can write

$$230 = 30 \times 5 = 10 \times 3 \times 5 = 2 \times 3 \times 3 \times 5$$

Notice that there are plenty of ways of writing 230 as a product of numbers (quick reminder that
product and multiplication is the same), but the last one is the only one that has **only** prime
numbers. That's what the theorem states, that one is the only possible way of writing 230 as
a product of primes.

By "unique" and "only possible way", we're of course, ignoring order. $$10 = 2 \times 3 = 3 \times 2$$,
so we can clearly rearrange the order of the primes. What we mean, is that if we have some collection
of prime numbers, their product will uniquely define a number above 1, and every number above 1 has a
unique collection of primes!

We're also hiding the fact that "no product" is also valid. Naturally, a prime number is a prime
number by itself, so it wouldn't be a product (again, it's by itself). If we wanted to be more precise,
but less concise, we could say "every integer above 1 is either prime or can be written as a product
of only prime numbers".

Every proof about "there is a unique" or "every something has a unique" is stating two things:

1. something exists

2. the something is unique

So we prove the first, then the second. If you're unfamiliar with mathematical proofs, you might
like reading [this intro guide]({{ site.ref }}/math-proofs). The first part also requires knowledge
of gcd and the Bézout Identity, which can be found [here]({{ site.ref }}/the-gcd). Of course,
since we're also talking about prime numbers, you can also check my [post]({{ site.ref }}/prime-intro)
on them.

<hr>

### Every integer above 1 *can* be written as a product of primes

This proof requires a tool called **strong induction**. Induction only requires that a certain
property is true for some n for us to prove the n+1 case. With *strong* induction, we assume it's
true for **every** value less than or equal to n, so we can prove the n+1 case.

The base case is $$n=2$$ (the smallest integer above 1), and naturally, $$2=2$$, which is a
prime by itself.

Now, let's assume it's true for every number from 2 to $$n$$. We want to show that $$n+1$$ can
also be written as a product of primes.

If $$n+1$$ is prime itself, we're done, trivially. If it's not prime, by the definition of
prime numbers, there's some number above 1 and below $$n+1$$ that divides it. In other words,
we can write $$n+1 = xy$$ for some value x and some value y.

But $$x$$ and $$y$$ must be smaller than $$n+1$$, so we know, from the inductive step, that
they're a product of primes. So substituting them for their product of primes, $$xy$$ will be
a product of only primes. So $$n+1$$ can be written as a product of primes!

<hr>

Before proving uniqueness, we'll prove an important lemma that is required for the proof.
It states that if a prime divides a product of two numbers, it must divide at least one
of the two numbers. In mathematical notation:

$$p \text{ is prime} \land p \mid ab \implies p \mid a \lor p \mid b$$

As a quick reminder, $$x \mid y$$ means "x divides y", $$\land$$ means "and", and $$\lor$$ means "or".
So out loud, it reads "if p is prime and p divides a times b, then p divides a or p divides b.

Note that in mathematics, "or" is inclusive. Meaning, when we say "P or Q", both P and Q can be
true. It's different than an *exclusive*-or, which is when only one of the two things said is
true at a time. When we say "I wanna go to Japan or Finland", we're not saying we *strictly* want
to go to only one of them, we're saying we want to go to at least one, that's *inclusive*.

**Proof.** We'll do a proof by cases that will make our life simpler:

If p divides a, we're done. If p doesn't divide a, we then prove p **must** divide b.

This means, we can rewrite the maths notation above to this:

$$p \text{ is prime} \land p \mid ab \implies (p \nmid a \implies p \mid b)$$

The negation of $$\mid$$ is $$\nmid$$, meaning "doesn't divide".

So, let's assume $$p$$ is prime, $$p \mid ab$$, but $$p \nmid a$$

Since $$p$$ doesn't divide $$a$$, it means their only common divisor is 1:

$$\gcd(p, a) = 1$$

Using Bézout's Identity, we can find some $$x$$ and $$y$$ such that

$$px + ay = 1$$

Multiplying both sides by $$b$$, we have

$$(px + ay)b = pxb + aby = b$$

To make the last step clear, knowing $$p$$ divides $$ab$$ we have that $$ab = zp$$ for some integer
$$z$$. Therefore:

$$pxb + aby = pxb + (zp)y = p(xb + zy) = b$$

So we found an integer $$xb+zy$$ that when multiplied by $$p$$, gives $$b$$. That's the same as
saying that $$p$$ divides $$b$$.

Importantly, Euclid's Lemma works for any product size. If we had that $$p \mid abc$$, we could
consider $$x = bc$$, so $$p \mid ax$$ and we can argue it divides either a or bc. If it does
divide x, meaning it divides bc, we apply the lemma again to find if it divides b or c.

### For an integer above 1, its representation as a product of primes is **unique**!

If we assume, by contradiction, that the above is false, we're saying there is one (or more)
numbers above 1 that can be written as two (or more) distinct products of primes. So we can take
the set $$S$$ of all numbers above 1 that *can* be written as two or more distinct products of
primes.

Since the set $$S$$ contains only **positive integers**, and has at least one element (that's
what we're assuming), it must have a **minimum element**. Let's say the minimum element is
$$k$$, and there's two, distinct, prime products that are equal to $$k$$. Namely,

$$k = p_0p_1p_2 \dots p_{n-1}p_n = q_0q_1q_2 \dots q_{m-1}q_m$$

To clarify the notation, since $$230 = 2 \times 3 \times 3 \times 5$$, we could say $$p_0 = 2$$,
$$p_1 = 3$$, $$p_2 = 3$$ and $$p_3 = 5$$. But the order doesn't matter. By no means $$p_1$$ has
to be greater than $$p_0$$, and so on.

$$p_1$$ obviously divides $$n$$, which is equal to that whole product of q primes:

$$p_1 \mid q_0q_1q_2 \dots q_{m-1}q_m$$

By Euclid's Lemma, it must divide one of the primes in that product. Let's call it $$q_i$$.
We say that $$p_1 \mid q_i$$ for some $$0 \le i \le m$$

Let's rearrange the indexes of the products to make things simpler. Let's switch $$q_i$$ for
$$q_1$$, switching the original $$q_1$$ to $$q_2$$ swapping it for $$q_3$$, until we reach
$$q_{i-1}$$, which swaps for $$q_i$$

$$q_i \rightarrow q_1 \rightarrow q_2 \rightarrow q_3 \rightarrow \dots
\rightarrow q_{i-2} \rightarrow q_{i-1} \rightarrow q_i$$

The product is still equal to $$n$$, we just swapped the indexes in a way that now,
$$p_1 \mid q_1$$

The important part here, is that if $$p_1$$ and $$q_1$$ are both prime, and one divides the other,
the only possible conclusion is that $$p_1 = q_1$$ (otherwise, $$q_1$$ would have to be a composite
number)!

So we can divide the p product by $$p_1$$ and the q product by $$q_1$$:

$$\frac{p_1p_2 \dots p_n}{p_1} = p_2p_3 \dots p_n = q_2q_3 \dots q_m = \frac{q_1q_2 \dots q_m}{q_1}$$

But because p and q are *distinct* products of primes and $$p_1$$ is **different than** $$q_1$$,
removing $$p_1$$ and $$q_1$$ from them, respectively, will still make the new p and q product distinct
from each other.

But these two products are smaller than $$k$$, because they're equal to

$$= \frac{k}{p_1} = \frac{k}{q_1}$$

This new number, that's smaller than $$k$$, has two distinct products of primes. However, that means
this new number is in the set $$S$$ we defined in the beginning! But $$k$$ was supposed to be the
minimum element! Ding ding ding, we found the contradiction!

Therefore, there is **no** number above 1 that has two distinct products of primes (meaning the
set $$S$$ is empty), and every product of primes uniquely defines a number above 1.

<hr>

The fundamental theorem of arithmetic is awesome, and super useful for proving a lot of stuff from
now on. In my article about primes, I "proved" that there are infinitely many primes, and in my
proof, I said "N+1 isn't divisible by any primes [...] That means N+1 must be a prime number!",
without really *proving* that it's true (I just gave a wordy explanation of why it *makes sense*
that it's true). So let's actually rigorously prove it!

For context, we were assuming that there is a finite number of primes, and $$N$$ was the product of
all those primes. If $$N+1$$ isn't a prime number, that means it is a product of prime numbers. So
there is *some* prime $$p_k$$ that divides $$N+1$$. But $$p_k$$ also divides $$N$$, since $$N$$ is
a product of all primes.

So $$p_k$$ is a common divisor of both $$N$$ and $$N+1$$. In other words, $$N = xp_k$$ and
$$N+1 = yp_k$$. This means their difference is

$$(N+1) - N = 1 = yp_k - xp_k = (y-x)p_k$$

This means $$p_k$$ divides 1, which is impossible, since all primes are greater than 1. This is the
key step that proves $$N+1$$ is prime and that our initial set of "all" prime numbers was missing
a prime number. Breaking the original assumption that primes are finite.

Finally, as I wrap this blog post off for today, I realize we accidentally proved another interesting
property about the gcd. For every integer $$x$$,

$$\gcd(x, x+1) = 1$$