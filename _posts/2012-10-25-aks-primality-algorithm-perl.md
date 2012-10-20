---
layout: post
title: AKS Primality Algorithm in Perl
status: unpublished
---

# {{ page.title }}

The first implementaiton of the
[AKS](https://en.wikipedia.org/wiki/AKS_primality_test) (Agrawal–Kayal–Saxena)
primality algorithm in pure Perl!

The AKS algorithm was an extremely important advance in the field of prime numbers,
because it proved that checking if a number is prime is in the class of the polynomial
run-time algorithms (P), instead of those that are not solvable in polynomial time (NP).
In practical terms, this means that there are efficient, deterministic algorithms that
can tell if a number is prime.

This is the "naive" implementation, which is O(log(n)^12). There is an
[improved algorithm by Lenstra +
Pomerance](http://www.math.dartmouth.edu/~carlp/PDF/complexity12.pdf) that is
O(log(n)^6) and we would love patches that implement it :)

[Math::Primality::AKS](https://metacpan.org/module/Math::Primality::AKS)

The majority of the work was done by my previous GSoC student, [Bob Kuo](https://twitter.com/bubaflub). I
merely helped get the [fix_aks branch merged](https://github.com/leto/math--primality/commit/1c6545f8f7a464bf5a5066cc4ef0d06532631588), helped add some tests and pushed
the distribution to [CPAN](http://cpan.org).
