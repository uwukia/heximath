---
title: The Greatest Common Divisor
description: "...or GCD, for short"
layout: post
tags: ["integers", "number theory"]
year: 13210
month: 4
day: 22
---

When I was a first year student of mathematics in university, I first heard the term "number theory",
which was an astounding and almost funny-sounding name for a serious mathematical field! I mean,
real numbers are numbers, even if their limits go to zero, so isn't calculus also a theory of numbers?
Isn't most of maths number theory?

I honestly couldn't find any well-sourced info on *why* do we really name it that, but if you want to
at least know what number theory is about, Wikipedia is good enough:

> Number theory is a branch of pure mathematics devoted primarily to the study
> of the integers and integer-valued functions.

I've done some articles on number theory. [Prime numbers]({{ site.ref }}/prime-intro),
[perfect numbers]({{ site.ref }}/perfect-numbers), and [modular arithmetic]({{ site.ref }}/modular-intro),
which is quite an important tool for number theory in general.

But today, we talk about the **greatest common divisor**, which is another important tool that is
involved in many mathematical proofs, so it's definitely a good idea to cover it in a blog post!

If we have the fraction $$6/14$$, we learn in school that we can *simplify* the fraction to something
"simpler" with smaller terms. Mainly, we can divide both 6 and 14 by 2 to get $$3/5$$, but we can't
simplify it further from there.

What we essentially just said, in mathematical terms, is that 

$$\gcd(6, 14) = 2$$

The greatest common divisor between two numbers, as the name suggests, is the biggest integer
that can divide both numbers. For example, 2 divides both 20 and 32, so it is a *common divisor*,
but it's not the *greatest* because both are also divisible by 4.

In the mathematical language, we can write a definition of the gcd below:

$$\gcd(a,b) = \max\{ n \in \mathbb{Z} : n \mid a \land n \mid b \}$$

First we take the set of all common divisors of $$a$$ and $$b$$, and the GCD will be the biggest
value in that set, that's what the $$\max$$ function is for. The "bar" in $$n \mid a$$ means "n is
divisible by a", and $$\land$$ is the logical symbol for "and". So that formula up there can be
read, out loud, as "the gcd of a and b is the maximum of the set of all integers n such that
n divides a and n divides b".

Let's exercise the gcd a little with some properties:

$$\gcd(a, b) = \gcd(b, a)$$

Swapping the order wouldn't change anything. A common divisor for a and b is also a common divisor
for b and a.

$$\gcd(x, x) = x$$

Keep in mind $$\gcd(0, 0)$$ is undefined because *every* integer divides 0, so there is no
maximum value. We assume $$x \ne 0$$. Of course, the biggest divisor of x is x itself!, in fact...

$$\gcd(x, nx) = x$$

because any multiple of x is divisible by x. The following theorem requires a bit more work:

$$\gcd(a + nb, b) = \gcd(a, b)$$

If $$d = \gcd(a+nb, b)$$, it follows that $$d \mid (a+nb)$$ and $$d \mid b$$, in other words,
$$a+nb = xd$$ and $$b = yd$$ for some x and some y. However, we can substitute $$yd$$ for
$$b$$ in the first equality:

$$a+n(yd) = xd \implies a = xd - nyd \implies a = (x - ny)d$$

So $$d$$ divides $$a$$, and therefore *is* a common divisor of $$a$$ and $$b$$! We just need
to prove it's the *greatest*.

Let's assume $$g$$ is a common divisor or $$a$$ and $$b$$. If it divides $$b$$, it must also
divide a multiple of $$b$$, namely, $$nb$$. Which ultimately means it also divides $$a+nb$$
(if it's unclear why, let $$a = xg$$ and $$b = yg$$ and do some algebra). So $$g$$ is a
common divisor of $$a+nb$$ and $$b$$, but that means $$g \le d$$, since $$d$$ is the greatest
common divisor of $$a+nb$$ and $$b$$.

We just proved that every common divisor of $$a$$ and $$b$$ is smaller than $$d$$, which
means $$d = \gcd(a, b)$$

<hr>

Now let's evaluate gcd(22, 23). You will see that they're not divisible by 2, or 3, or 5, and
so on. And in fact, the only common divisor they have is 1 (which is always a common divisor
between two integers). Since it's the only common divisor, it sure is the greatest!

$$\gcd(22, 23) = 1$$

When the gcd between two numbers is 1, we say the numbers are **coprime**. 22 is coprime with
23, just like 3 and 12 or 5 and 25. We call them *coprime* because they don't share a prime
factor. Naturally, if one is prime and the other is not divisible by that prime, they must be
coprime. All prime numbers are coprime between each other (except themselves).

So how can we compute the gcd of really big numbers? Do we just guess? Of course not! We got
plenty of methods for hand-computing it! Of course, not for the really *really* big numbers,
we can let the computers have those.

$$\gcd(1023, 3225) = \, ?$$

Let's try to divide the biggest by the smallest! 3225 divided by 1023 would give 3, with
remainder 112. That is, $$3225 = 3\times1023 + 112$$. But notice what happens when we
substitute it for the gcd! We can use that last property I mentioned above, where
gcd(a+nb, b) = gcd(a, b)

$$\gcd(1023, 112+3\times1023) = \gcd(1023, 112)$$

And now we do it again! Try to divide 1023 by 112, get 5 with remainder 15, so we have that

$$\gcd(1023, 112) = \gcd(15, 112)$$

Finally, doing the division again, we find out that 112 is a multiple of 15, specifically,
$$112 = 4\times15$$, and therefore, $$\gcd(15, 112) = 15$$

So there we have it! What we're doing here, taking the remainder when dividing a by b, is
often called $$(a \mod b)$$, so $$(3225 \mod 1023) = 112$$

There are other cool properties about the gcd, and it's especially fun to talk about how
we can program efficient algorithms for it, but that's gonna be said in a later article.
As always, stay tuned.

<hr>

For now, we'll prove a cool theorem called the **Bézout Identity**. It states that

Let $$a$$, $$b$$ be integers (where one at least one of them is not zero): There
exist integers $$x$$ and $$y$$ such that

$$ax + by = \gcd(a, b)$$

The proof is pretty neat, but it requires an important theorem involving integer sets:

> If $$S$$ is a non-empty set of **positive integers**, then it has a *minimum element*,
> that is, there is some element in $$S$$ that is the smallest value in the set.

Which makes sense! If we took the set {3, 10, 20}, 3 would be the minimum element. Even
if we took **all** positive integers {1, 2, 3, ...}, 1 would be the minimum element!

It's very important to restrict this to a set with **integers** and **positive** ones.
If we allow for negative integers, we could have the set {-1, -2, -3, ...}, which has
no minimum element, as it goes for negative infinity.

If we allowed for non-integers, such as rational numbers, we could take the set of all
positive rational numbers! By contradiction, let's say $$r$$ is the smallest positive
rational number, we know that $$r/2$$ is also a rational number, but it's smaller than
$$r$$, so by contradiction, it's impossible to have a smallest positive rational.

Of course, we also need to restrict it to non-empty sets, since empty sets have no
elements, so there's no smallest element.

<hr>

**Proof of Bézout's Identity**

We know $$\gcd(c, 0) = c$$ (can you see why?), so naturally,
$$cx + 0y = c$$ for x=1 and any y. Those cases are trivial, so we just have to prove
the identity for values of a and b that are **both** non-zero.

Let $$S = \{ ax+by : x,y \in \mathbb{Z} \land ax+by > 0 \}$$ be the set of all
combinations of ax+by that are positive (greater than zero). We know this set is
not empty, because for y=0, we have all possible values for ax, and we know a is
not zero, so either -a or +a is positive, and both are in the set for the values
x=-1 (multiplied by the negative one) and x=1 (multiplied by the positive one).

And this set only contains positive integers, because it only has combinations for
ax+by that are positive! So we conclude that it must have a minimum element! Let's
say $$d$$ is the minimum element of $$S$$.

Because $$d$$ is in the set, it means $$d = as + bt$$ for some value of s and t,
since all elements of the set are of the form ax+by for some element x and y.

If we try to divide $$a$$ by $$d$$, we get some value $$q$$, and a remainder $$r$$.
In other words, $$a = qd + r$$. In other words:

$$r = a - qd = a - q(as+bt) = a - qas - qbt = a(1 - qs) + (-qt)b$$. Since $$1-qs$$
is an integer, and $$-qt$$ (heh, out loud it sounds like "cutie") is also an
integer, we have something of the form ax+by if we substitute those for x and y
respectively. However, the remainder *could* be zero or positive. So it's either
zero, or in the set $$S$$. In other words, $$r \in S \cup \{0\}$$

The problem is, $$r$$ was the remainder of dividing $$a$$ by $$d$$, so it has to
be smaller than $$d$$, or it wouldn't be a remainder! So if it *is* part of the
set $$S$$, it would be an element smaller than the *smallest element*, which is
a contradiction! Therefore, $$r$$ is not part of the set, which ultimately means
$$r = 0$$.

There's nothing special about $$a$$ here. We could've done the same argument
above when dividing $$b$$ by $$d$$. We take the remainder, do some algebra to
find that the remainder is either zero or in the set, and conclude that cannot
be in the set, because again, it's smaller than $$d$$.

But if the remainder is zero for both $$a$$ and $$b$$, that means $$d$$ divides
both $$a$$ and $$b$$! This concludes that **d is a common divisor of a and b**.

Now, if we can prove that it's the *greatest* common divisor, we can conclude
that $$\gcd(a, b) = d$$, and since $$d = ax + by$$ for some values of x and y,
we have proved the Bézout Identity!

Let $$c$$ be a common divisor of a and b. That means $$a = cw$$ and $$b = cz$$
for some integer w and some integer z. Therefore, $$d = as+bt = (cw)s+(cz)t
= c(ws+zt)$$. This means c also divides d, and any divisor of d must be equal
to or smaller than d (this is true for every positive integer). So $$d$$ is
definitely the greatest common divisor, as any other common divisor is either
itself, or smaller.

Neat, huh? Bézout's Identity is a nice tool for proving a plethora of number
theory tools, including the **fundamental theory of arithmetic**, which I
am quite inspired to write about, and might be tomorrow's blog post.

