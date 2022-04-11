---
title: An introduction to Prime Numbers
description: "My favorite infinite set of positive integers!"
layout: post
tags: ["integers", "primes", "sequences"]
year: 13210
month: 4
day: 11
---

When we say a number is **divisible** by another number, we mean that we can evenly divide it
into an integer result. If we have 10 apples to divide among 3 people, we can do it perfectly
by giving each person 2 apples. That is, 10 is divisible by 3.

5 however, is not divisible by 3. The best you can do is give each person 1 apple and be left
with 2 apples to spare.

Hmmm, if you think about it. 5 is also not divisible by 2 or 4 either. Tho obviously, it's
divisible by 1 (which essentially means not dividing at all), and also divisible by 5 (you can
give 1 apple to each person).

So 5 is divisible by 1 and itself, but not divisible by any number in between.

11 works the same way. Divisible by 1 and itself, but not by any number between 1 and 11.
13 does break the "odd pattern". You can divide 13 apples among 3 people (each will have 3 apples).

What we're describing here is precisely what defines **prime numbers**. 5 and 11 are prime numbers,
while 13 and 10 aren't. For a more precise mathematical definition...

> A prime number is an integer greater than 1 that is only divisible by 1 and itself

Before we analyze the definition above, let's take a step back and remind ourselves of a few things:

1. All integers are divisible by 1. $$x / 1 = x$$

2. All integers are divisible by themselves. $$x / x = 1$$

3. An integer will never be divisible by a bigger integer. Naturally, if you have 4 apples and 10
people, you really can't give them any apples without at least one person being left out.

That third statement is important because if we ever want to check which numbers divide another
number, we never have to look for numbers above itself. For example, if we want to know which
numbers divide 14, we don't have to go above 14, they won't be able to divide 14.

Now, based on the definition we gave above, 1 is not a prime number. As it stated, it must be
"greater than 1".

2 however, is a prime number! It's only divisible by 1 and itself! Same goes for 3. 4 is not a prime
number because it's divisible by 2, but 5 is! If we decide to list out all the prime numbers, the
list would start more or less like this:

$$2, 3, 5, 11, 15, 21, 25, 31, 35, 45, ...$$

After seeing this small sample of primes, some questions may start to arise!

### Everyone seems to be odd... except 2!

Indeed! 2 is the first and last even prime number. That's because the definition of being even is
being divisible by 2. So 4, 10, and so on cannot be prime (but 2 can since it is 2 itself).

### After 3, their last digit seems to be either 1 or 5...

If you noticed that, very good catch! We can prove that easily as well. 

Everytime we try to divide something by 10, we might be able to divide it evenly (that would mean
it's divisible by 10) or there will be a leftover amount. This leftover amount has to be 1, 2, 3,
4, or 5. Mathematically speaking, we're saying that every integer can be written as the form

$$10k + n \text{, where } n \in \{ 0, 1, 2, 3, 4, 5 \} \text{ and }k\text{ is some other integer}$$

Now, if n is 0, 2, or 4, our original number has to be even. $$10k = 2(3k)$$, $$10k+2 = 2(3k+1)$$,
and $$10k+4 = 2(3k+2)$$. If n is 3, our original number is divisible by 3, since $$10k+3 = 3(2k+1)$$

So the only way for a number to be a prime above 3, is to be of the form $$10k+1$$ or $$10k+5$$,
which ultimately means the last digit will be 1 or 5.

### Are there infinitely many primes?

A very good question, there's a very simple and elegant proof for this! It uses a very important
logical tool in math which I might write a blog post about it in the future. Essentially, we'll
assume primes aren't infinite, and that will result in a contradiction. Because we don't allow for
contradictions in math, we'll then conclude that they must be infinite.

<hr>

Assume there are finitely many primes. Only a finite set of them exists, and it's the set below:

$$\{2, 3, 5, 11, \dots, p_{n-1}, p_n\}$$

This set has size $$n$$, meaning there is a total of $$n$$ primes. What we do then, is multiply them
all into a huge number:

$$N = 2\times 3\times 5\times\dots\times p_{n-1} \times p_n$$

Of course, $$N$$ is divisible by 2. It's also divisible by 3, and 5. It's divisible by every prime!
But what about $$N+1$$?

Well, $$N+1$$ isn't divisible by any primes... But that means it's not divisible by any composite
number either! If it's not divisible by 2, it won't be divisible by 4, or 10, or 124. Likewise, it
can't be divisible by 13 or 100 because it's not divisible by 3. Therefore, there are no divisors
of $$N+1$$ other than 1 or itself... That means $$N+1$$ is a prime number!

Here comes the contradiction: There is no way $$N+1$$ was part of our original list. If we assume
$$p_n$$ was the biggest prime in our list (but it works for any prime in the list), because all
primes are positive, clearly multiplying them all up will yield something much much greater.

To recap, we assumed the primes were finite. If they are, we can create a finite set with **every**
single prime that exists. That list, by definition, includes every prime. Except it turns out, it
suddenly doesn't, since $$N+1$$ is missing!

So the list has all prime numbers, but not all prime numbers! It's the Schrödinger's prime list!
No, not really. It's purely a contradiction. That's not allowed. Therefore, our assumption that the
primes were finite was incorrect, and therefore, **there are infinitely many prime numbers**!

<hr>

There are loads of interesting things we can do with prime numbers, which will possibly render a
lot of blog posts on them. So stay tuned for that!