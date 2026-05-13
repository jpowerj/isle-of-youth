(sec-4-5)=
# 4.5 The master method for solving recurrences

The master method provides a "cookbook" method for solving algorithmic recurrences of the form

$$
T(n) = aT(n/b) + f(n),
$$

where $a > 0$ and $b > 1$ are constants. We call $f(n)$ a **driving function**, and we call a recurrence of this general form a **master recurrence**. To use the master method, you need to memorize three cases, but then you'll be able to solve many master recurrences quite easily.
