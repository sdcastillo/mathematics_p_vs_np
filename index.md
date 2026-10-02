---
layout: default
title: P versus NP
description: Painfully challenging notes on verification, search, and NP-completeness.
samwiki: true
---

The P versus NP problem asks whether every decision problem that has a short, efficiently checkable proof also has a polynomial-time decision algorithm. This page records the definitions, the completeness notion, and the barriers a proof still has to clear. On the SamWiki ladder the subject is painfully challenging, for a reader who wants the complexity-theory statement.

A language L ⊆ Σ\* belongs to **P** when a deterministic Turing machine decides membership in time O(n^k) for some constant k, with n the input length. The same language belongs to **NP** when yes-instances carry a short witness: there is a polynomial p and a deterministic verifier V, running in time polynomial in n, such that x ∈ L exactly when some string y with |y| ≤ p(|x|) satisfies V(x, y) = 1. That verifier definition is equivalent to the existence of a nondeterministic Turing machine that decides L in polynomial time. **P** is contained in **NP**, because a deterministic decider is a verifier that ignores any witness.

The open question is whether the inclusion is an equality. Equality would give every language in **NP** a polynomial-time algorithm, including every NP-complete language. A language is NP-complete when it lies in **NP** and every language in **NP** maps to it by a deterministic polynomial-time many-one reduction. The Cook–Levin theorem places Boolean satisfiability in that class. Subset Sum is NP-complete as well. Its standard dynamic program is pseudo-polynomial in the magnitude of the integers, hence exponential in their bit length, so the algorithm does not place Subset Sum in **P**. The decision version of the traveling salesman problem, which asks whether some tour has total cost at most K, is NP-complete. The optimization version, which asks for a shortest tour, is NP-hard and is not a decision language in **NP**.

**P** is the usual mathematical model of tractability. Exponential time is a different regime, and the gap is visible in a concrete time-to-solve budget. A machine that performs 10^9 basic operations each second finishes an O(n) or O(n^2) pass over an input of length 100 in well under a millisecond. The same machine finishes a loop of 2^n operations in about 10^−6 seconds at n = 10, about one second at n = 30, about 13 days at n = 50, about 3.7×10^4 years at n = 70, and about 4×10^13 years at n = 100. A faster processor changes the leading constant. The bound 2^n stays outside every polynomial.

A proof has to survive three barriers that already rule out large families of arguments. Baker, Gill, and Solovay constructed oracles A and B with P^A = NP^A and P^B ≠ NP^B, so a relativizing argument cannot settle the question. Razborov and Rudich showed that natural proofs cannot establish the superpolynomial circuit lower bounds that would separate **NP** from **P**/poly, if suitable cryptographic pseudorandom generators exist. Aaronson and Wigderson extended the obstruction to algebrizing techniques. Integer factoring and the discrete logarithm lie in **NP** and are hard in deployed cryptography, and neither is known to be NP-complete: a polynomial-time factoring algorithm would leave satisfiability unresolved. The Beamer source in this repository, `p_vs_np_beamer_styled.tex`, uses these definitions and treats an AI co-pilot as a way to organize reductions and instances. The conjecture still requires a mathematical argument.

- **P** is deterministic polynomial-time decision. **NP** is polynomial-time verification of a polynomially long witness. The classes are equal only if every such verifier can be replaced by a decider.
- SAT, by Cook–Levin, together with Subset Sum and the decision traveling salesman problem, are NP-complete. One polynomial-time algorithm for any of them decides every language in **NP**.
- Generalized Sudoku is NP-complete. Checking a completed grid is a deterministic polynomial-time predicate. Filling the grid is the search problem.
- Factoring, discrete logarithms, and collision resistance of a hash function are cryptographic hardness assumptions. They sit beside P versus NP and do not decide it.
- Relativization, natural proofs, and algebrization are the three obstructions a separation argument has to escape.
- Time-to-solve is the resource reading of the same gap: time, memory, and energy as n grows, set against the question of whether any polynomial bound exists.
