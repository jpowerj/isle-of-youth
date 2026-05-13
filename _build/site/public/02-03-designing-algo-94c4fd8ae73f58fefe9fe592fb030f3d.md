(sec-2-3)=
# 2.3 Designing Algorithms

You can choose from a wide range of algorithm design techniques. Insertion sort uses the **incremental** method: for each element $A[i]$, insert it into its proper place in the subarray $A[1:i]$, having already sorted the subarray $A[1:i-1]$.

This section examines another design method, known as "divide-and-conquer," which we explore in more detail in Chapter 4. We'll use divide-and-conquer to design a sorting algorithm whose worst-case running time is much less than that of insertion sort. One advantage of using an algorithm that follows the divide-and-conquer method is that analyzing its running time is often straightforward, using techniques that we’ll explore in Chapter 4.

(sec-2-3-1)=
### 2.3.1 The divide-and-conquer method

Many useful algorithms are recursive in structure: to solve a given problem, they
recurse (call themselves) one or more times to handle closely related subprob-
lems. These algorithms typically follow the divide-and-conquer method: they
break the problem into several subproblems that are similar to the original prob-
lem but smaller in size, solve the subproblems recursively, and then combine these
solutions to create a solution to the original problem.
In the divide-and-conquer method, if the problem is small enough4the base
case4you just solve it directly without recursing. Otherwise4the recursive case
4you perform three characteristic steps:
Divide the problem into one or more subproblems that are smaller instances of the
same problem.
Conquer the subproblems by solving them recursively.
Combine the subproblem solutions to form a solution to the original problem.
The merge sort algorithm closely follows the divide-and-conquer method. In
each step, it sorts a subarray AŒp W r�, starting with the entire array AŒ1 W n� and
recursing down to smaller and smaller subarrays. Here is how merge sort operates:
