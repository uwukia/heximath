---
title: The number 24
description: "...and why it's special!"
layout: post
tags: ["integers", "exponents"]
year: 13210
month: 4
day: 10
---

Hopefully you are familiar with square numbers. Numbers that can be represented as $$x^2$$, where
$$x$$ is some integer. For example, $$4$$ is a square number because it can be represented as $$2^2$$

And, to recap exponents, just like how multiplication is repeated addition,

$$3\times5 = 3+3+3+3+3$$

exponentiation is repeated multiplication!

$$3^5 = 3\times3\times3\times3\times3$$

Now here's a really cute fact about exponents!

$$4^2 = 2^4 = 24$$

Isn't it wonderful? We can swap the 2 and the 4 for the base and exponent, and the result remains
the same, which is 2 and 4 side by side!

Now, we could ask ourselves the same question for any other number. For example,

$$2^3 = 12 \text{ and } 3^2 = 13$$

So it doesn't work with 2 and 3. Now, we could also say none of them result in 23 or 32
like it happened with 24, but I'll go ahead and say 24 really is the only number where that
happens. So we'll ignore that and just focus on solving this instead:

$$x^y = y^x$$

How can we find integer solutions to this equation? Well, this is where harder maths will come
into play. Mainly, natural logarithms and a little bit of calculus.

<hr>

Let's take the natural log and divide both sides by $$xy$$ (we can do that because x and y cannot
be zero, I'll leave that as a homework if you want to ponder why yourself).

$$\ln(x^y) = ln(y^x) \implies y\ln(x) = x\ln(y)
\implies \frac{y\ln(x)}{xy} = \frac{x\ln(y)}{xy} \implies \frac{\ln(x)}{x} = \frac{\ln(y)}{y}$$

Notice how each side of the equation has only one variable. We can rephrase the equation by
creating the function:

$$f(x) = \frac{\ln(x)}{x} \implies f(x) = f(y)$$

So that's it! All we need is to find solutions where f(x) equals f(y), when x and y are integers
and from each other, of course.

Here comes the calculus part. We can take the derivative of f(x) and figure out when the derivative
is zero:

$$f'(x) = \frac{1}{x}\frac{1}{x} + \ln(x)\frac{-1}{x^2} = \frac{1}{x^2}(1 - \ln(x))$$

Since $${1}/{x^2}$$ can never be zero, the only way for the derivative to be zero is when
$$(1 - \ln(x))$$ is zero. And that happens when $$1 = \ln(x)$$, or in other words:

$$x = e$$

We can deduce that $$x = e$$ is a local maximum because

$$x < e \implies 1 - \ln(x) > 0 \text{ and } x > e \implies 1 - \ln(x) < 0$$

So the function is increasing from 0 to $$e$$, then decreasing from $$e$$ to infinity (note that
the function is only defined for $$x > 0$$ because of the logarithm).

This ultimately means that if we ever find a pair $$x$$ and $$y$$ that solves that original
equation, one **must** lie on the interval $$(0, e)$$ and the other **must** lie on the interval
$$(e, \infty)$$. But remember! We're trying to look for *integer solutions*, and the only integers
in the interval $$(0, e)$$ are 1 and 2!

Since we already found the solution for 2, all we need is to check if 1 has any solution.

Unfortunately, $$f(1) = 0$$, and we can verify that for $$x > e$$, $$f(x)$$ is decreasing but
always bigger than zero, since both $$\ln(x)$$ and $$x$$ will remain positive.

This confirms that 2 and 4 form the only integer solution for the equation.

<hr>

Of course, there is only 1 pair of integer solutions, but there are infinitely real solutions
for the original equation, where one of the numbers in the pair lie on the interval $$(1, e)$$,
but that is beyond the scope of today's post. You can take a peek at
[what wolframalpha says](https://www.wolframalpha.com/input?i=x%5Ey+%3D+y%5Ex), however.