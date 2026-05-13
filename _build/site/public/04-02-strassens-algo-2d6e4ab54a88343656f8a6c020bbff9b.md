(sec-4-2)=
# 4.2 Strassen's algorithm for matrix multiplication

You might find it hard to imagine that any matrix multiplication algorithm could take less than $\Theta(n^3)$ time, since the natural definition of matrix multiplication requires $n^3$ scalar multiplications. Indeed, many mathematicians presumed that it was not possible to multiply matrices in $o(n^3)$ time until 1969, when V. Strassen [424] published a remarkable recursive algorithm for multiplying $n \times n$ matrices. Strassen’s algorithm runs in $\Theta(n^{\lg 7})$ time. Since $\lg 7 = 2.8073549 \ldots$, Strassen's algorithm runs in $O(n^{2.81})$ time, which is asymptotically better than the $\Theta(n^3)$ {sc}`Matrix-Multiply` and {sc}`Matrix-Multiply-Recursive` procedures.

The key to Strassen’s method is to use the divide-and-conquer idea from the
MATRIX-MULTIPLY-RECURSIVE procedure, but make the recursion tree less
bushy. We’ll actually increase the work for each divide and combine step by a
constant factor, but the reduction in bushiness will pay off. We won’t reduce the
bushiness from the eight-way branching of recurrence (4.9) all the way down to
the two-way branching of recurrence (2.3), but we’ll improve it just a little, and
that will make a big difference. Instead of performing eight recursive multiplica-
tions of n=2  n=2 matrices, Strassen’s algorithm performs only seven. The cost
of eliminating one matrix multiplication is several new additions and subtractions
of n=2  n=2 matrices, but still only a constant number. Rather than saying <addi-
tions and subtractions= everywhere, we’ll adopt the common terminology of call