(sec-4-6)=
# 4.6 Proof of the continuous master theorem

Proving the master theorem (Theorem 4.1) in its full generality, especially dealing with the knotty technical issue of üoors and ceilings, is beyond the scope of this
book. This section, however, states and proves a variant of the master theorem,
called the continuous master theorem1 in which the master recurrence (4.17) is
deûned over sufûciently large positive real numbers. The proof of this version,
uncomplicated by üoors and ceilings, contains the main ideas needed to understand
how master recurrences behave. Section 4.7 discusses üoors and ceilings in divide-
and-conquer recurrences at greater length, presenting sufûcient conditions for them
not to affect the asymptotic solutions.
Of course, since you need not understand the proof of the master theorem in
order to apply the master method, you may choose to skip this section. But if you
wish to study more-advanced algorithms beyond the scope of this textbook, you
may appreciate a better understanding of the underlying mathematics, which the
proof of the continuous master theorem provides.
Although we usually assume that recurrences are algorithmic and don’t require
an explicit statement of a base case, we must be much more careful for proofs that
justify the practice. The lemmas and theorem in this section explicitly state the base
cases, because the inductive proofs require mathematical grounding. It is common
in the world of mathematics to be extraordinarily careful proving theorems that
justify acting more casually in practice.
The proof of the continuous master theorem involves two lemmas. Lemma 4.2
uses a slightly simpliûed master recurrence with a threshold constant of n0 D 1,
rather than the more general n0 > 0 threshold constant implied by the unstated base
case. The lemma employs a recursion tree to reduce the solution of the simpliûed
master recurrence to that of evaluating a summation. Lemma 4.3 then provides
asymptotic bounds for the summation, mirroring the three cases of the master the-
orem. Finally, the continuous master theorem itself (Theorem 4.4) gives asymp-
totic bounds for master recurrences, while generalizing to an arbitrary threshold
constant n0 > 0 as implied by the unstated base case.
