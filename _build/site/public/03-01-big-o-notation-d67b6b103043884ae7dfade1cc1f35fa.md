(sec-3-1)=
# 3.1 O-notation, Ω-notation, and Θ-notation

When we analyzed the worst-case running time of insertion sort in Chapter 2, we started with the complicated expression

$$
\left( \right)n^2 + \left( \right) n - (c_2 + c_4 + c_5 + c_8)
$$

We then discarded the lower-order terms  .c1 C c2 C c4 C c5 =2  c6 =2  c7 =2 C c8 /n
and c2 C c4 C c5 C c8 , and we also ignored the coefûcient c5 =2 C c6 =2 C c7 =2
of n2 . That left just the factor n2 , which we put into ‚-notation as ‚.n2 /. We
use this style to characterize running times of algorithms: discard the lower-order
terms and the coefûcient of the leading term, and use a notation that focuses on the
rate of growth of the running time.
‚-notation is not the only such <asymptotic notation.= In this section, we’ll
see other forms of asymptotic notation as well. We start with intuitive looks at
these notations, revisiting insertion sort to see how we can apply them. In the next
section, we’ll see the formal deûnitions of our asymptotic notations, along with
conventions for using them.
Before we get into speciûcs, bear in mind that the asymptotic notations we’ll see
are designed so that they characterize functions in general. It so happens that the
functions we are most interested in denote the running times of algorithms. But
asymptotic notation can apply to functions that characterize some other aspect of
algorithms (the amount of space they use, for example), or even to functions that
have nothing whatsoever to do with algorithms.
O-notation
O-notation characterizes an upper bound on the asymptotic behavior of a function.
In other words, it says that a function grows no faster than a certain rate, based on
the highest-order term. Consider, for example, the function 7n3 C 100n2  20n C 6.
Its highest-order term is 7n3 , and so we say that this function’s rate of growth is n3 .
Because this function grows no faster than n3 , we can write that it is O.n3 /. You
might be surprised that we can also write that the function 7n3 C 100n2  20n C 6
is O.n4 /. Why? Because the function grows more slowly than n4 , we are correct
in saying that it grows no faster. As you might have guessed, this function is also
O.n5 /, O.n6 /, and so on. More generally, it is O.nc / for any constant c  3.
