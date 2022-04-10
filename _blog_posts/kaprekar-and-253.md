---
title: Kaprekar's Routine and 253
description: "Buckle up, it's time to cycle!"
layout: post
tags: ["integers", "programming"]
year: 13210
month: 4
day: 14
---

How about a little magic trick involving 253? Let's choose at random, a 3 digit number.

$$151$$

Let's write down two numbers based on 151. One with the digits in descending order, the other one with
the digits in ascending order.

$$511, 115$$

Now subtract the latter to the former. We have $$511 - 115 = 352$$, right? Now let's do the same process
again for 352, and...

$$532 - 235 = 253$$

Brilliant! We reached 253! Maybe you think to yourself, "there's no way this will always happen!", so you
think for a bit and choose 344.

$$344 \implies 443 - 344 = 55$$

Okay, since we're supposed to stay in the 3 digit realm, we need to "append" a zero to the left of 55.

$$055 \implies 550 - 055 = 451 \implies 541 - 145 = 352 \implies 532 - 235 = 253$$

It took a few more steps, but we got it!

### Hold on, but both of them reached 352 first. Isn't 352 more special?

Yes, technically it is special. And notice how the order of digits of a number don't matter. If instead
of 344, we started with 434 or 443, the process would've been the same, as we reorder the digits after
anyway. So 352 and 253 are equivalent in that regard. The reason we chose 253 is that it iterates into
itself.

$$253 \implies 532 - 235 = 253$$

And some numbers reach 253 directly, without going through 352.

$$314 \implies 431 - 134 = 253$$

### Wait... What about 111?

Brilliant catch. If you gave it a go in trying to break this algorithm, there's a chance you tried
with a number where all the digits are the same, like 111 or 444. Those are the only ones that do
break the algorithm, since rearranging their digits does nothing, and subtracting it to itself will
give you zero.

So an important restriction is that we need *at least* two digits to be different from each other.

### How can we prove it'll always work?

Well, since there are only 500 3-digit numbers, we might as well go through them all using
computers! In fact, that's what I used to fact-check and write some of the examples above. So I
figured I might as well show you what I wrote and how it works.

My programming language of choice is [Rust](https://www.rust-lang.org/). It's absolutely beautiful,
memory-safe, super fast, does what I need, and there's a fantastic community behind it.

It's okay if you're not familiar with programming, because just by reading this blog post, I'm sure
you will be able to at least get a hinch of how things kind of work.

<hr>

For starters, we need to separate the digits from a given number. We want to create a list (or in
Rust's vocabulary, a *vector*) of digits of a given number.

```rs
fn to_le_digits(mut num: u144) -> Vec<u12> {
    let mut vec = Vec::new(); // Step 1

    loop {
        vec.push((num % 10) as u12); // Step 2
        num /= 10; // Step 3

        if num == 0 { // Step 4
            break vec
        }
    }
}
```

Let's break these bit by bit. I created a function called `to_le_digits`, which will convert a
number such as 153 into [3, 5, 1]. You may find it strange that the list looks "backwards", but
it's just easier to do it this way. And if we really needed the list to have the digits in the
same order as the number, we can just call the `reverse()` function.

`mut num: u144` means "this function will receive a 144-bit number, and it will change throughout
the algorithm". `-> Vec<u12>` means "this function returns a vector (or a list) of 12-bit numbers".
Those 12-bit numbers represent each digit.

Now for each step inside the function. We'll use 153 as an example.

**1\.** For step 1, all we do is create an empty list (the `mut` stands for "mutable" and is what
indicates to the computer that this list will change over time).

**2\.** In step 2, we take the current number (153) and retrieve the last digit (which is 3). `%` is
an operator that divides the left number by the right number, and returns the remainder. If
you read my blog post about [modular arithmetic]({{ site.url }}{{ site.baseurl }}/posts/modular-intro),
this should hit close to home.

`a % b = c` $$\iff a \equiv c \pmod{b}$$

When we try to divide 153 by 10, we end up with 15 and remainder 3, right? Therefore, `153 % 10`
is equal to 3. In modular arithmetic, we say $$153 \equiv 3 \pmod{10}$$

Then, we add the 3 to the empty list with the `push` function. So the list goes from [] to [3].

**3\.** In the third step, we remove what's left from the division. Reiterating, 153 divided by 3
gives us 15 with remainder 3. So when Rust divides the two integers, it will result in 15.

The `/=` operator basically takes the number on the left, divides it by the number on the right,
then "substitutes" its value by the result.

So remember, `num` was originally 153, and now we divided it by 10 and replaces its value with
the result. Now, `num` equals 15.

**4\.** In this step, we check if `num` is zero. It's 15, so it does not pass the check. Therefore,
nothing happens.

Because we are in a loop, we will loop back to step 2, now with a different value for `num`.

In step 2, we have 15, so we'll push 5 into the vector, so instead of [3], it is now [3, 5].
In step 3, we divide the number by 10 again, and ignore the remainder. So `num` becomes simply 1.
As it is still not equal to zero, we ignore step 4.

We loop back to step 2, and push 1 into the vector, so it is [3, 5, 1]. In step 3, notice how we
can't divide 1 by 10 (the only way to divide 1 apple among 10 people is to just not give anyone
any apples), so the result is zero and `num` is now zero.

But now, it passes the check in step 4, as it's now zero! Because of that, we'll execute the code
inside that block of code. Which says `break vec`. This means "please stop the loop and return
the value of `vec`!". So the function will stop running through the loop, and return [3, 5, 1].

That's it! We extracted the digits of a number.

We'll also need to create a function that will take a list such as [3, 5, 1] and return 153.
But it's a bit unintuitive for non-rust programmers, especially for non-programmers in general!
But if you're curious, here's how it looks:

```rs
fn from_le_digits(digits: &[u12]) -> u144 {
    let mut result: u144 = 0;
    for &digit in digits.iter().rev() {
        result *= 10;
        result += digit as u144;
    }

    result
}
```

This will take a list such as [3, 5, 1], reverse it into [1, 5, 3], then retrieve each digit one
by one. For each digit, it'll multiply the result by 10, then add the digit. So the result will,
for each iteration, change in the following way:

$$0 \implies 10\times0+1 = 1 \implies 10\times1+5=15 \implies 10\times15+3=153$$

```rs
fn kaprekar_iteration(x: u144, digit_count: usize) -> u144 {
    let mut digits = crate::to_le_digits(x); // Step 1
    while digits.len() < digit_count { digits.push(0) } // Step 2

    let mut descending_digits = digits;
    descending_digits.sort(); // Step 3

    let mut ascending_digits = descending_digits.clone();
    ascending_digits.reverse(); // Step 4

    // Step 5
    let descending_number = crate::from_le_digits(&descending_digits);
    let ascending_number  = crate::from_le_digits(&ascending_digits);

    descending_number - ascending_number
}

```

Finally, this is the algorithm that performs the iteration itself! Here's a brief explanation
of each step:

1. Convert a number such as 153 into [3, 5, 1].

2. If the list has less items than the expected number of digits, add zeros to the end. This
step is important, as if you remember in the beginning of the article, 344 yielded 55, which is
not a 3 digit number. So if we have a list like [5, 5], we need to add a zero so it becomes
[5, 5, 0].

3. We take the resulting digits and sort them. Rust by default sorts them in ascending order, but
remember the list is written backwards. So [3, 5, 1], when sorted, becomes [1, 3, 5]. But remember,
that list represents the number 531, which is sorted in descending order.

4. Now we want the same number, but with the digits in ascending order. That's easy if we just clone
the list into another location and reverse that other list. So first, we clone the list,
then reverse it! So that clone goes from [1, 3, 5] into [5, 3, 1].

5. The list [1, 3, 5] becomes the number 531, and the list [5, 3, 1] becomes the number 135.

The last line of the function performs 531 - 135, which is equal to 352.

And thus, we can run the following algorithm to verify every 3 digit number and see which numbers
iterate to themselves:

```rs
for x in 100..1000 {
    if x == kaprekar_iteration(x, 3) {
        println!("{} iterates to itself!", x);
    }
}
```

This piece of code will go through every x between 100 and 1000 (not including 1000) and verifies
if the Kaprekar iteration is equal to itself. When running this code, my terminal looked like this:

```
253 iterates to itself!
```

That is, out of every 3 digit number, only 253 mapped to itself.

There's a lot more that can be done with this algorithm. We can verify for 4 digit numbers and beyond,
but if you want a spoiler alert, 41532 is the magical number for 5 digit numbers. 4 digit numbers
don't have a neat number that iterates to itself, but does have the following loop:

$$1554 \implies 4042 \implies 4132 \implies 3043 \implies 3552 \implies 3133 \implies 1554$$