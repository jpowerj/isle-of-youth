(sec-4-9)=
# Chapter notes

Divide-and-conquer as a technique for designing algorithms dates back at least to 1962 in an article by Karatsuba and Ofman [242], but it might have been used
well before then. According to Heideman, Johnson, and Burrus [211], C. F. Gauss
devised the ûrst fast Fourier transform algorithm in 1805, and Gauss’s formulation
breaks the problem into smaller subproblems whose solutions are combined.

Strassen’s algorithm [424] caused much excitement when it appeared in 1969.
Before then, few imagined the possibility of an algorithm asymptotically faster than
the basic MATRIX-MULTIPLY procedure. Shortly thereafter, S. Winograd reduced
the number of submatrix additions from 18 to 15 while still using seven submatrix
multiplications. This improvement, which Winograd apparently never published
(and which is frequently miscited in the literature), may enhance the practicality
of the method, but it does not affect its asymptotic performance. Probert [368]
described Winograd’s algorithm and showed that with seven multiplications, 15
additions is the minimum possible.

Strassen's $\Theta(n^{\lg 7})$ bound for matrix multiplication held until 1987, when Coppersmith and Winograd [103] made a significant advance, improving the