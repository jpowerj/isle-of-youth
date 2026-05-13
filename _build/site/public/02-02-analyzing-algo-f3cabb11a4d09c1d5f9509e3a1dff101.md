(sec-2-2)=
# 2.2 Analyzing Algorithms

**Analyzing** an algorithm has come to mean predicting the resources that the algorithm requires. You might consider resources such as memory, communication bandwidth, or energy consumption. Most often, however, you'll want to measure computational time. If you analyze several candidate algorithms for a problem, you can identify the most efficient one. There might be more than just one viable candidate, but you can often rule out several inferior algorithms in the process.

Before you can analyze an algorithm, you need a model of the technology that it runs on, including the resources of that technology and a way to express their costs. Most of this book assumes a generic one-processor, **random-access machine (RAM)** model of computation as the implementation technology, with the understanding that algorithms are implemented as computer programs. In the RAM model, instructions execute one after another, with no concurrent operations. The RAM model assumes that each instruction takes the same amount of time as any other instruction and that each data access -- using the value of a variable or storing into a variable -- takes the same amount of time as any other data access. In other words, in the RAM model each instruction or data access takes a constant amount of time -- even indexing into an array.[^9]

Strictly speaking, we should precisely define the instructions of the RAM model and their costs. To do so, however, would be tedious and yield little insight into algorithm design and analysis. Yet we must be careful not to abuse the RAM model. For example, what if a RAM had an instruction that sorts? Then you could sort in just one step. Such a RAM would be unrealistic, since such instructions do not appear in real computers. Our guide, therefore, is how real computers are designed. The RAM model contains instructions commonly found in real computers: arithmetic (such as add, subtract, multiply, divide, remainder, floor, ceiling), data movement (load, store, copy), and control (conditional and unconditional branch, subroutine call and return).

The data types in the RAM model are integer, floating point (for storing real-number approximations), and character. Real computers do not usually have a separate data type for the boolean values `True` and `False`. Instead, they often test whether an integer value is 0 (`False`) or nonzero (`True`), as in C. Although we typically do not concern ourselves with precision for floating-point values in this book (many numbers cannot be represented exactly in floating point), precision is crucial for most applications. We also assume that each word of data has a limit on the number of bits. For example, when working with inputs of size $n$, we typically

assume that integers are represented by c log2 n bits for some constant c  1. We
require c  1 so that each word can hold the value of n, enabling us to index
the individual input elements, and we restrict c to be a constant so that the word
size does not grow arbitrarily. (If the word size could grow arbitrarily, we could
store huge amounts of data in one word and operate on it all in constant time4an
unrealistic scenario.)
Real computers contain instructions not listed above, and such instructions rep-
resent a gray area in the RAM model. For example, is exponentiation a constant-
time instruction? In the general case, no: to compute x n when x and n are general
integers typically takes time logarithmic in n (see equation (31.34) on page 934),
and you must worry about whether the result ûts into a computer word. If n is an
exact power of 2, however, exponentiation can usually be viewed as a constant-time
operation. Many computers have a <shift left= instruction, which in constant time
shifts the bits of an integer by n positions to the left. In most computers, shifting
the bits of an integer by 1 position to the left is equivalent to multiplying by 2, so
that shifting the bits by n positions to the left is equivalent to multiplying by 2n .
Therefore, such computers can compute 2n in 1 constant-time instruction by shift-
ing the integer 1 by n positions to the left, as long as n is no more than the number
of bits in a computer word. We’ll try to avoid such gray areas in the RAM model
and treat computing 2n and multiplying by 2n as constant-time operations when
the result is small enough to ût in a computer word.
The RAM model does not account for the memory hierarchy that is common
in contemporary computers. It models neither caches nor virtual memory. Sev-
eral other computational models attempt to account for memory-hierarchy effects,
which are sometimes signiûcant in real programs on real machines. Section 11.5
and a handful of problems in this book examine memory-hierarchy effects, but for
the most part, the analyses in this book do not consider them. Models that include
the memory hierarchy are quite a bit more complex than the RAM model, and so
they can be difûcult to work with. Moreover, RAM-model analyses are usually
excellent predictors of performance on actual machines.
Although it is often straightforward to analyze an algorithm in the RAM model,
sometimes it can be quite a challenge. You might need to employ mathematical
tools such as combinatorics, probability theory, algebraic dexterity, and the ability
to identify the most signiûcant terms in a formula. Because an algorithm might
behave differently for each possible input, we need a means for summarizing that
behavior in simple, easily understood formulas.

## Analysis of insertion sort

How long does the {sc}`Insertion-Sort` procedure take? One way to tell would be for you to run it on your computer and time how long it takes to run. Of course, you'd

ûrst have to implement it in a real programming language, since you cannot run our
pseudocode directly. What would such a timing test tell you? You would ûnd out
how long insertion sort takes to run on your particular computer, on that particular
input, under the particular implementation that you created, with the particular
compiler or interpreter that you ran, with the particular libraries that you linked
in, and with the particular background tasks that were running on your computer
concurrently with your timing test (such as checking for incoming information over
a network). If you run insertion sort again on your computer with the same input,
you might even get a different timing result. From running just one implementation
of insertion sort on just one computer and on just one input, what would you be able
to determine about insertion sort’s running time if you were to give it a different
input, if you were to run it on a different computer, or if you were to implement it
in a different programming language? Not much. We need a way to predict, given
a new input, how long insertion sort will take.
Instead of timing a run, or even several runs, of insertion sort, we can determine
how long it takes by analyzing the algorithm itself. We’ll examine how many times
it executes each line of pseudocode and how long each line of pseudocode takes
to run. We’ll ûrst come up with a precise but complicated formula for the running
time. Then, we’ll distill the important part of the formula using a convenient no-
tation that can help us compare the running times of different algorithms for the
same problem.
How do we analyze insertion sort? First, let’s acknowledge that the running time
depends on the input. You shouldn’t be terribly surprised that sorting a thousand
numbers takes longer than sorting three numbers. Moreover, insertion sort can take
different amounts of time to sort two input arrays of the same size, depending on
how nearly sorted they already are. Even though the running time can depend on
many features of the input, we’ll focus on the one that has been shown to have
the greatest effect, namely the size of the input, and describe the running time of a
program as a function of the size of its input. To do so, we need to define the terms "running time" and "input size" more carefully. We also need to be clear about
whether we are discussing the running time for an input that elicits the worst-case
behavior, the best-case behavior, or some other case.

The best notion for **input size** depends on the problem being studied. For many
problems, such as sorting or computing discrete Fourier transforms, the most nat-
ural measure is the number of items in the input4for example, the number n of
items being sorted. For many other problems, such as multiplying two integers,
the best measure of input size is the total number of bits needed to represent the
input in ordinary binary notation. Sometimes it is more appropriate to describe the
size of the input with more than just one number. For example, if the input to an
algorithm is a graph, we usually characterize the input size by both the number

of vertices and the number of edges in the graph. We’ll indicate which input size
measure is being used with each problem we study.
The running time of an algorithm on a particular input is the number of in-
structions and data accesses executed. How we account for these costs should be
independent of any particular computer, but within the framework of the RAM
model. For the moment, let us adopt the following view. A constant amount of
time is required to execute each line of our pseudocode. One line might take more
or less time than another line, but we’ll assume that each execution of the kth line
takes ck time, where ck is a constant. This viewpoint is in keeping with the RAM
model, and it also reüects how the pseudocode would be implemented on most
actual computers. 10
Let’s analyze the I NSERTION-SORT procedure. As promised, we’ll start by de-
vising a precise formula that uses the input size and all the statement costs ck .
This formula turns out to be messy, however. We’ll then switch to a simpler no-
tation that is more concise and easier to use. This simpler notation makes clear
how to compare the running times of algorithms, especially as the size of the input
increases.
To analyze the I NSERTION-SORT procedure, let’s view it on the following page
with the time cost of each statement and the number of times each statement is
executed. For each i D 2; 3; : : : ; n, let ti denote the number of times the while
loop test in line 5 is executed for that value of i . When a for or while loop exits
in the usual way4because the test in the loop header comes up FALSE4the test is
executed one time more than the loop body. Because comments are not executable
statements, assume that they take no time.
The running time of the algorithm is the sum of running times for each state-
ment executed. A statement that takes ck steps to execute and executes m times
contributes ck m to the total running time.11 We usually denote the running time of
an algorithm on an input of size n by T .n/. To compute T .n/, the running time
of I NSERTION-SORT on an input of n values, we sum the products of the cost and
times columns, obtaining

T .n/ D c1 n C c2 .n  1/ C c4 .n  1/ C c5
nX
i D2
ti C c6
nX
i D2
.ti  1/
C c7
nX
i D2
.ti  1/ C c8 .n  1/ :
Even for inputs of a given size, an algorithm’s running time may depend on
which input of that size is given. For example, in I NSERTION-SORT, the best case
occurs when the array is already sorted. In this case, each time that line 5 executes,
the value of key4the value originally in AŒi �4is already greater than or equal to
all values in AŒ1 W i  1�, so that the while loop of lines 537 always exits upon the
ûrst test in line 5. Therefore, we have that ti D 1 for i D 2; 3; : : : ; n, and the
best-case running time is given by
T .n/ D c1 n C c2 .n  1/ C c4 .n  1/ C c5 .n  1/ C c8 .n  1/
D .c1 C c2 C c4 C c5 C c8 /n  .c2 C c4 C c5 C c8 / : (2.1)
We can express this running time as an C b for constants a and b that depend on
the statement costs ck (where a D c1 Cc2 Cc4 Cc5 Cc8 and b D c2 Cc4 Cc5 Cc8 ).
The running time is thus a linear function of n.
The worst case arises when the array is in reverse sorted order4that is, it starts
out in decreasing order. The procedure must compare each element AŒi � with each
element in the entire sorted subarray AŒ1 W i  1�, and so ti D i for i D 2; 3; : : : ; n.
(The procedure ûnds that AŒj � > key every time in line 5, and the while loop exits
only when j reaches 0.) Noting that
nX
i D2
i D
 nX
i D1
i
!
 1
D n.n C 1/
2  1 (by equation (A.2) on page 1141

We can express this worst-case running time as an2 C bn C c for constants a, b,
and c that again depend on the statement costs ck (now, a D c5 =2 C c6 =2 C c7 =2,
b D c1 C c2 C c4 C c5 =2  c6 =2  c7 =2 C c8 , and c D .c2 C c4 C c5 C c8 /). The
running time is thus a quadratic function of n.

Typically, as in insertion sort, the running time of an algorithm is fixed for a
given input, although we’ll also see some interesting "randomized" algorithms
whose behavior can vary even for a fixed input.

## Worst-case and average-case analysis

Our analysis of insertion sort looked at both the best case, in which the input array
was already sorted, and the worst case, in which the input array was reverse sorted.
For the remainder of this book, though, we’ll usually (but not always) concentrate
on ûnding only the worst-case running time, that is, the longest running time for
any input of size n. Why? Here are three reasons:
 The worst-case running time of an algorithm gives an upper bound on the run-
ning time for any input. If you know it, then you have a guarantee that the
algorithm never takes any longer. You need not make some educated guess
about the running time and hope that it never gets much worse. This feature is
especially important for real-time computing, in which operations must com-
plete by a deadline.
 For some algorithms, the worst case occurs fairly often. For example, in search-
ing a database for a particular piece of information, the searching algorithm’s
worst case often occurs when the information is not present in the database. In
some applications, searches for absent information may be frequent.

The <average case= is often roughly as bad as the worst case. Suppose that
you run insertion sort on an array of n randomly chosen numbers. How long
does it take to determine where in subarray AŒ1 W i  1� to insert element AŒi �?
On average, half the elements in AŒ1 W i  1� are less than AŒi �, and half the
elements are greater. On average, therefore, AŒi � is compared with just half
of the subarray AŒ1 W i  1�, and so ti is about i=2. The resulting average-case
running time turns out to be a quadratic function of the input size, just like the
worst-case running time.
In some particular cases, we’ll be interested in the average-case running time of
an algorithm. We’ll see the technique of probabilistic analysis applied to various
algorithms throughout this book. The scope of average-case analysis is limited,
because it may not be apparent what constitutes an <average= input for a particular
problem. Often, we’ll assume that all inputs of a given size are equally likely. In
practice, this assumption may be violated, but we can sometimes use a randomized
algorithm, which makes random choices, to allow a probabilistic analysis and yield
an expected running time. We explore randomized algorithms more in Chapter 5
and in several other subsequent chapters.
Order of growth
In order to ease our analysis of the I NSERTION-SORT procedure, we used some
simplifying abstractions. First, we ignored the actual cost of each statement, using
the constants ck to represent these costs. Still, the best-case and worst-case run-
ning times in equations (2.1) and (2.2) are rather unwieldy. The constants in these
expressions give us more detail than we really need. That’s why we also expressed
the best-case running time as an C b for constants a and b that depend on the state-
ment costs ck and why we expressed the worst-case running time as an2 C bn C c
for constants a, b, and c that depend on the statement costs. We thus ignored not
only the actual statement costs, but also the abstract costs ck .
Let’s now make one more simplifying abstraction: it is the rate of growth, or
order of growth, of the running time that really interests us. We therefore consider
only the leading term of a formula (e.g., an2 ), since the lower-order terms are rela-
tively insigniûcant for large values of n. We also ignore the leading term’s constant
coefûcient, since constant factors are less signiûcant than the rate of growth in de-
termining computational efûciency for large inputs. For insertion sort’s worst-case
running time, when we ignore the lower-order terms and the leading term’s con-
stant coefûcient, only the factor of n2 from the leading term remains. That factor,
n2 , is by far the most important part of the running time. For example, suppose that
an algorithm implemented on a particular machine takes n2 =100 C 100n C 17 mi-
croseconds on an input of size n. Although the coefûcients of 1=100 for the n2 term
and 100 for the n term differ by four orders of magnitude, the n2 =100 term domi

nates the 100n term once n exceeds 10,000. Although 10,000 might seem large, it
is smaller than the population of an average town. Many real-world problems have
much larger input sizes.
To highlight the order of growth of the running time, we have a special notation
that uses the Greek letter ‚ (theta). We write that insertion sort has a worst-case
running time of ‚.n2 / (pronounced "theta of $n$-squared" or just "theta $n$-squared").
We also write that insertion sort has a best-case running time of ‚.n/ ("theta of $n$"
or "theta $n$"). For now, think of ‚-notation as saying "roughly proportional when $n$ is large," so that ‚.n2 / means "roughly proportional to $n^2$ when $n$ is large" and ‚.n/ means "roughly proportional to n when n is large" We'll use ‚-notation informally in this chapter and define it precisely in Chapter 3.

We usually consider one algorithm to be more efficient than another if its worst-case running time has a lower order of growth. Due to constant factors and lower-order terms, an algorithm whose running time has a higher order of growth might take less time for small inputs than an algorithm whose running time has a lower order of growth. But on large enough inputs, an algorithm whose worst-case running
time is ‚.n2 /, for example, takes less time in the worst case than an algorithm
whose worst-case running time is ‚.n3 /. Regardless of the constants hidden by
the ‚-notation, there is always some number, say n0 , such that for all input sizes
n  n0 , the ‚.n2 / algorithm beats the ‚.n3 / algorithm in the worst case.

## Exercises

### 2.2-1

Express the function n3 =1000 C 100n2  100n C 3 in terms of ‚-notation.

### 2.2-2

Consider sorting n numbers stored in array AŒ1 W n� by ûrst ûnding the smallest
element of AŒ1 W n� and exchanging it with the element in AŒ1�. Then ûnd the
smallest element of AŒ2 W n�, and exchange it with AŒ2�. Then ûnd the smallest
element of AŒ3 W n�, and exchange it with AŒ3�. Continue in this manner for the
ûrst n  1 elements of A. Write pseudocode for this algorithm, which is known
as selection sort. What loop invariant does this algorithm maintain? Why does it
need to run for only the ûrst n  1 elements, rather than for all n elements? Give the
worst-case running time of selection sort in ‚-notation. Is the best-case running
time any better?

### 2.2-3

Consider linear search again (see Exercise 2.1-4). How many elements of the input
array need to be checked on the average, assuming that the element being searched
for is equally likely to be any element in the array? How about in the worst case?

Using ‚-notation, give the average-case and worst-case running times of linear
search. Justify your answers.

### 2.2-4

How can you modify any sorting algorithm to have a good best-case running time?

[^9]: We assume that each element of a given array occupies the same number of bytes and that the elements of a given array are stored in contiguous memory locations. For example, if array $A[1:n]$ starts at memory address 1000 and each element occupies four bytes, then element $A[i]$ is at address $1000 + 4(i-1)$. In general, computing the address in memory of a particular array element requires at most one subtraction (no subtraction for a 0-origin array), one multiplication (often implemented as a shift operation if the element size is an exact power of 2), and one addition. Furthermore, for code that iterates through the elements of an array in order, an optimizing compiler can generate the address of each element using just one addition, by adding the element size to the address of the preceding element.