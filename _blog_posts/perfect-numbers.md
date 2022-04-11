---
title: Perfect Numbers
description: "What makes them perfect?"
layout: post
tags: ["integers", "sequences"]
year: 13210
month: 4
day: 13
---

We've [already talked]({{ site.url }}{{ site.baseurl }}/posts/prime-intro) about what it means for a number to be divisible by
another. 12 is divisible by 1, 2, 4, and itself, but not divisible by 3, 5, 10, and so on.

When we look at the set of numbers that divide some other number, we call them **divisors**, or
**factors**. That is: 1, 2, 4 and 12 are factors of 12. And in fact, the only factors of 12 (can
you see why?).

Let's say $$F(n)$$ is the set of all factors of $$n$$ except for $$n$$ itself.

$$F(12) = \{1, 2, 4\}$$

Now let's say $$\sum F(n)$$ is the sum of all elements of $$F(n)$$

$$\sum F(12) = 1+2+4 = 11$$

That's pretty cool. The sum is one less than 12 itself. What about 10?

$$\sum F(10) = \sum \{1, 2, 3\} = 10$$

Woah! That's cool, we found an example where $$n = \sum F(n)$$. Can we find more?

It takes a while. We can try a few 2 digit numbers with no luck. Until...

$$\sum F(44) = \sum \{1, 2, 4, 11, 22\} = 44$$

Cool! So 10 and 44 are part of this special set of numbers where the sum of its factors less
than itself is equal to itself! As you may have guessed, this set is called **the set of
perfect numbers**! The next one has quite a big gap from 44:

$$\sum F(2144) = \sum \{1, 2, 4, 12, 51, 142, 324, 1052\} = 2144$$

Aaaand I'm not gonna keep going. I'm just gonna give you the list itself:

$$10, 44, 2144, 101344, 3155033344, 3540210412144, \dots$$

Phew, they sure are getting sparser quick. And just like when we looked at the prime numbers,
some questions may arise when looking at this sequence.

### After 10, they seem to always end in 44...

You're 100% correct, and we can prove it! We'll do it at the end of the post.

### Is there a pattern?

Well, yes. I'm gonna give you the same sequence as above, except I'll write the numbers as a product
of prime numbers:

$$2^1 3, 2^2 11, 2^4 51, 2^{10} 331, 2^{20} 101531, 2^{24} 2450451, \dots$$

Hmmm... so they're all a product of a power of 2 and a prime number. Neat, I suppose! But we won't
stop there! Notice what happens when we take those lone primes and add 1 to each!

$$3+1 = 2^2, 11+1 = 2^3, 51+1 = 2^5, 331+1 = 2^{11}, 101531+1 = 2^{21}, \dots$$

So all of these primes are one less than a power of 2 (and you can verify with a calculator that it
works for 2450451 as well). So let's rewrite the list as

$$2^1 (2^2 - 1), 2^2 (2^3 - 1), 2^4 (2^5 - 1), 2^{10} (2^{11} - 1), 2^{20} (2^{21} - 1), \dots$$

That's pretty awesome! What's even more awesome is that if you look at one number individually, you
see that the left power of 2 is 1 less than the right one. For example, in $$2^{10} (2^{11} - 1)$$,
we see that 10 is 1 less than 11.

So all of these perfect numbers seem to follow the pattern $$2^{n-1}(2^n - 1)$$, and
[Nichomachus](https://en.wikipedia.org/wiki/Nicomachus), a mathematician from ancient Greece, thought
that **every** perfect number is written in this form. However, there are caveats.

* $$n$$ itself also has to be prime, not just $$(2^n - 1)$$.

* When these conditions are met, this will generate an **even** perfect number. More on that in a
bit.

The brilliant (and personal favorite) mathematician [Leonhard Euler](https://en.wikipedia.org/wiki/Leonhard_Euler)
managed to *prove* that yes, every even perfect number is of the form $$2^{n-1}(2^n - 1)$$, where
both $$n$$ and $$(2^n - 1)$$ are prime.

### Aren't they all even?

Yes, if you look in the original list, you can clearly see they're all even. An in fact, the
current list of all perfect numbers we're aware of, only has even perfect numbers. The catch, is
that we **have not proven** there aren't any odd perfect numbers. There could be a chance that
once we look for them long enough, we might find a huge odd perfect number!

It is however, very unlikely. We've done a lot of research on the properties of odd perfect numbers,
such as proving that it cannot be divisible by 253. Not only that, but we've used computers to look
through **a lot** of numbers and we can confidently say that, if it does exist, it's going to be
greater than $$10^{12000}$$, which is huge!! 

All of this really suggests they don't exist, and we're just waiting for the right mathematical tools
and the right mathematician to come along and finally prove it formally.

### Are they infinite?

Clearly we can generate perfect numbers by finding primes of the form $$(2^p - 1)$$. In fact, these
prime numbers which are 1 off by a power of 2 are called **Mersenne primes**, and it turns out, we
also have not proven there are infinitely many Mersenne primes.

Currently, the list of all known Mersenne primes has 51 values, meaning we only know 51 perfect
numbers exist. The biggest Mersenne prime known is

$$2^{12110104445} - 1$$

<hr>

### So do they all really end in 44?

Here we go! Time for the proof! I must reiterate two things first.

1. This proof only works for *even* perfect numbers, as we'll exploit their representation as
a product of a power of 2 and a Mersenne prime.

2. This only applies to 44 onwards, as 10 *is* an even perfect number and, well, it ends in 10.

A perfect number has the form $$2^{p-1}(2^p - 1)$$, where $$p$$ is a prime number. If $$p = 2$$,
the result is $$10$$, which we'll ignore for this proof. So we assume $$p > 2$$, meaning $$p$$
is an odd prime. In any case, it's an odd number.

Here's where [modular arithmetic]({{ site.url }}{{ site.baseurl }}/posts/modular-intro) comes into play, so get ready!

Since $$p$$ is odd, we have that $$p \equiv 1 \pmod{2}$$, and therefore, we can rewrite $$p$$ as
$$p = 2n + 1$$ for some integer $$n$$.

$$2^{p-1}(2^p - 1) = 2^{2n}(2^{2n+1} - 1) = 2^{4n+1} - 2^{2n}$$

Ultimately, we're trying to prove that all numbers of that form end in 44. But that's the same
thing as saying $$2^{4n+1} - 2^{2n} \equiv 44 \pmod{100}$$ (can you see why?).

This proof uses induction. We'll prove this works for $$n=1$$, then prove that if it works for some
$$n$$, it works for $$n+1$$, which proves it works for every $$n\ge1$$.

When $$n=1$$, we have $$2^5 - 2^2 = 44$$, so trivially, $$44 \equiv 44 \pmod{100}$$.

Now, let's assume $$2^{4n+1} - 2^{2n} \equiv 44 \pmod{100}$$. From there, we want to prove that

$$2^{4(n+1)+1} - 2^{2(n+1)} \equiv 44 \pmod{100}$$

Let's do some algebra and rearrange things!

$$2^{4(n+1)+1} - 2^{2(n+1)} = 2^{4n+5} - 2^{2n+2} = 4(4\cdot2^{4n+1} - 2^{2n})$$

$$= 4(2^{4n+1} - 2^{2n} + 3\cdot2^{4n+1}) = 4(2^{4n+1} - 2^{2n}) + 20\cdot2^{4n+1}$$

Alright. We know from our assumption that $$2^{4n+1} - 2^{2n} \equiv 44 \pmod{100}$$. Therefore,

$$4(2^{4n+1} - 2^{2n}) \equiv 4(44) \implies 4(2^{4n+1} - 2^{2n}) \equiv 104 \pmod{100}$$

Naturally, $$104 \equiv 4 \pmod{100}$$ (why?), so we have that 

$$4(2^{4n+1} - 2^{2n}) + 20\cdot2^{4n+1} \equiv 4 + 20\cdot2^{4n+1} \pmod{100}$$

Now we just need to prove that $$20\cdot2^{4n+1} \equiv 40 \pmod{100}$$, and we're done, since
$$4 + 40 \equiv 44 \pmod{100}$$.

What we'll do instead, is prove that $$2^{4n+1} \equiv x \pmod{100} \iff x \in \{12, 32, 52\}$$.

The reason this is useful is that once we know $$2^{4n+1}$$ is congruent to one of 3 values, we
can verify for each one, that $$20\cdot12 = 240, 20\cdot32 = 1040, 20\cdot52 = 1440$$.

$$240 \equiv 1040 \equiv 1440 \equiv 40 \pmod{100}$$

Remember, no calculators are needed! Taking something modulo 100 is the same as looking at the
last two digits! So in order to conclude our proof, all we do is prove by induction that

$$2^{4n+1} \equiv x \pmod{100} \iff x \in \{12, 32, 52\}$$

For $$n=1$$, $$2^5 = 52 \equiv 52 \pmod{100}$$.

Now assume $$2^{4n+1} \equiv x \pmod{100} \iff x \in \{12, 32, 52\}$$

We have that $$2^{4(n+1)+1} = 2^{4n+5} = 24\cdot2^{4n+1}$$

We verify for each case that $$24\cdot12 = 332, 24\cdot32 = 1252, 12\cdot52 = 2212$$

Clearly, $$332 \equiv 32, 1252 \equiv 52, 2212 \equiv 12$$, so again we can find an $$x \in \{12, 32, 52\}$$
such that $$2^{4n+5} \equiv x \pmod{100}$$

That's it! Very neat! We proved that every even perfect number above 10 ends in 44.