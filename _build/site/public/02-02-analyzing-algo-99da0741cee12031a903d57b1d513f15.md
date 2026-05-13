(sec-2-2)=
# 2.2 Analyzing Algorithms

Analyzing an algorithm has come to mean predicting the resources that the algo-
rithm requires. You might consider resources such as memory, communication
bandwidth, or energy consumption. Most often, however, you’ll want to measure
computational time. If you analyze several candidate algorithms for a problem

you can identify the most efûcient one. There might be more than just one viable
candidate, but you can often rule out several inferior algorithms in the process.
Before you can analyze an algorithm, you need a model of the technology that
it runs on, including the resources of that technology and a way to express their
costs. Most of this book assumes a generic one-processor, random-access ma-
chine (RAM) model of computation as the implementation technology, with the
understanding that algorithms are implemented as computer programs. In the RAM
model, instructions execute one after another, with no concurrent operations. The
RAM model assumes that each instruction takes the same amount of time as any
other instruction and that each data access4using the value of a variable or storing
into a variable4takes the same amount of time as any other data access. In other
words, in the RAM model each instruction or data access takes a constant amount
of time4even indexing into an array.9
Strictly speaking, we should precisely deûne the instructions of the RAM model
and their costs. To do so, however, would be tedious and yield little insight into al-
gorithm design and analysis. Yet we must be careful not to abuse the RAM model.
For example, what if a RAM had an instruction that sorts? Then you could sort
in just one step. Such a RAM would be unrealistic, since such instructions do
not appear in real computers. Our guide, therefore, is how real computers are de-
signed. The RAM model contains instructions commonly found in real computers:
arithmetic (such as add, subtract, multiply, divide, remainder, üoor, ceiling), data
movement (load, store, copy), and control (conditional and unconditional branch,
subroutine call and return).
The data types in the RAM model are integer, üoating point (for storing real-
number approximations), and character. Real computers do not usually have a
separate data type for the boolean values TRUE and FALSE. Instead, they often test
whether an integer value is 0 (FALSE) or nonzero (TRUE), as in C. Although we
typically do not concern ourselves with precision for üoating-point values in this
book (many numbers cannot be represented exactly in üoating point), precision is
crucial for most applications. We also assume that each word of data has a limit on
the number of bits. For example, when working with inputs of size n, we typically