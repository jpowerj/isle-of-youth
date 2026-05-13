(sec-4-7)=
# 4.7 Akra-Bazzi recurrences

This section provides an overview of two advanced topics related to divide-and-
conquer recurrences. The ûrst deals with technicalities arising from the use of
üoors and ceilings, and the second discusses the Akra-Bazzi method, which in-
volves a little calculus, for solving complicated divide-and-conquer recurrences.
In particular, we’ll look at the class of algorithmic divide-and-conquer recur-
rences originally studied by M. Akra and L. Bazzi [13]. These Akra-Bazzi recurrences take the form

T .n/ D f .n/ C
kX
i D1
ai T .n=bi / ; (4.22)
where k is a positive integer; all the constants a1 ; a2 ; : : : ; ak 2 R are strictly posi-
tive; all the constants b1 ; b2 ; : : : ; bk 2 R are strictly greater than 1; and the driving
function f .n/ is deûned on sufûciently large nonnegative reals and is itself non-
negative.
Akra-Bazzi recurrences generalize the class of recurrences addressed by the
master theorem. Whereas master recurrences characterize the running times of
divide-and-conquer algorithms that break a problem into equal-sized subproblems
(modulo üoors and ceilings), Akra-Bazzi recurrences can describe the running time
of divide-and-conquer algorithms that break a problem into different-sized sub-
problems. The master theorem, however, allows you to ignore üoors and ceilings,
but the Akra-Bazzi method for solving Akra-Bazzi recurrences needs an additional
requirement to deal with üoors and ceilings.
But before diving into the Akra-Bazzi method itself, let’s understand the lim-
itations involved in ignoring üoors and ceilings in Akra-Bazzi recurrences. As
you’re aware, algorithms generally deal with integer-sized inputs. The mathemat-
ics for recurrences is often easier with real numbers, however, than with integers,
where we must cope with üoors and ceilings to ensure that terms are well deûned.
The difference may not seem to be much4especially because that’s often the truth
with recurrences4but to be mathematically correct, we must be careful with our