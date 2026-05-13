(sec-2-1)=
# 2.1 Insertion Sort

Our first algorithm, insertion sort, solves the **sorting problem** introduced in Chapter 1:

**Input:** A sequence of $n$ numbers $\langle a_1, a_2, \ldots, a_n \rangle$

**Output:** A permutation (reordering) $\langle a'_1, a'_2, \ldots, a'_n \rangle$ of the input sequence such that $a'_1 \leq a'_2 \leq \cdots \leq a'_n$.

The numbers to be sorted are also known as the **keys**. Although the problem is conceptually about sorting a sequence, the input comes in the form of an array with $n$ elements. When we want to sort numbers, it’s often because they are the keys associated with other data, which we call **satellite data**. Together, a key and satellite data form a **record**. For example, consider a spreadsheet containing student records with many associated pieces of data such as age, grade-point average, and number of courses taken. Any one of these quantities could be a key, but when the

spreadsheet sorts, it moves the associated record (the satellite data) with the key.
When describing a sorting algorithm, we focus on the keys, but it is important to
remember that there usually is associated satellite data.
In this book, we’ll typically describe algorithms as procedures written in a pseu-
docode that is similar in many respects to C, C++, Java, Python,1 or JavaScript.
(Apologies if we’ve omitted your favorite programming language. We can’t list
them all.) If you have been introduced to any of these languages, you should have
little trouble understanding algorithms <coded= in pseudocode. What separates
pseudocode from real code is that in pseudocode, we employ whatever expres-
sive method is most clear and concise to specify a given algorithm. Sometimes
the clearest method is English, so do not be surprised if you come across an En-
glish phrase or sentence embedded within a section that looks more like real code.
Another difference between pseudocode and real code is that pseudocode often ig-
nores aspects of software engineering4such as data abstraction, modularity, and
error handling4in order to convey the essence of the algorithm more concisely.
We start with insertion sort, which is an efûcient algorithm for sorting a small
number of elements. Insertion sort works the way you might sort a hand of playing
cards. Start with an empty left hand and the cards in a pile on the table. Pick up
the ûrst card in the pile and hold it with your left hand. Then, with your right hand,
remove one card at a time from the pile, and insert it into the correct position in
your left hand. As Figure 2.1 illustrates, you ûnd the correct position for a card
by comparing it with each of the cards already in your left hand, starting at the
right and moving left. As soon as you see a card in your left hand whose value is
less than or equal to the card you’re holding in your right hand, insert the card that
you’re holding in your right hand just to the right of this card in your left hand. If
all the cards in your left hand have values greater than the card in your right hand,
then place this card as the leftmost card in your left hand. At all times, the cards
held in your left hand are sorted, and these cards were originally the top cards of
the pile on the table.
The pseudocode for insertion sort is given as the procedure I NSERTION-SORT
on the facing page. It takes two parameters: an array A containing the values to
be sorted and the number n of values of sort. The values occupy positions AŒ1�
through AŒn� of the array, which we denote by AŒ1 W n�. When the I NSERTION-
SORT procedure is ûnished, array AŒ1 W n� contains the original values, but in sorted
order.