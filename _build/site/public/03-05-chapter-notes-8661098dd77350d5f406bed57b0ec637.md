(sec-3-5)=
# Chapter Notes

Knuth [259] traces the origin of the O-notation to a number-theory text by P. Bachmann in 1892. The o-notation was invented by E. Landau in 1909 for his discussion
of the distribution of prime numbers. The � and ‚ notations were advocated by
Knuth [265] to correct the popular, but technically sloppy, practice in the litera-
ture of using O-notation for both upper and lower bounds. As noted earlier in
this chapter, many people continue to use the O-notation where the ‚-notation is
more technically precise. The soft-oh notation eO in Problem 3-6 was introduced

by Babai, Luks, and Seress [31], although it was originally written as O. Some
authors now deûne eO.g.n// as ignoring factors that are logarithmic in g.n/, rather
than in n. With this deûnition, we can say that n2n D eO.2n /, but with the deû-
nition in Problem 3-6, this statement is not true. Further discussion of the history
and development of asymptotic notations appears in works by Knuth [259, 265]
and Brassard and Bratley [70].
Not all authors deûne the asymptotic notations in the same way, although the
various deûnitions agree in most common situations. Some of the alternative def-
initions encompass functions that are not asymptotically nonnegative, as long as
their absolute values are appropriately bounded.
Equation (3.29) is due to Robbins [381]. Other properties of elementary math-
ematical functions can be found in any good mathematical reference, such as
Abramowitz and Stegun [1] or Zwillinger [468], or in a calculus book, such as
Apostol [19] or Thomas et al. [433]. Knuth [259] and Graham, Knuth, and Patash-
nik [199] contain a wealth of material on discrete mathematics as used in computer
science.