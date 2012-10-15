---
layout: post
title: AKS Primality Algorithm in Perl
status: unpublished
---

# {{ page.title }}

The first implementaiton of the
[AKS](https://en.wikipedia.org/wiki/AKS_primality_test) (Agrawal–Kayal–Saxena)
primality algorithm in pure Perl!

[Math::Primality::AKS](https://metacpan.org/module/Math::Primality::AKS)

The majority of the work was done by my previous GSoC student, [Bob Kuo](https://twitter.com/bubaflub). I
merely helped get the [fix_aks branch merged](https://github.com/leto/math--primality/commit/1c6545f8f7a464bf5a5066cc4ef0d06532631588), helped add some tests and pushed
the distribution to CPAN.

Optimized algorithm by Lenstra + Pomerance: http://www.math.dartmouth.edu/~carlp/PDF/complexity12.pdf

