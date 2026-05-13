---
numbering: false
---

# Preface

Digitization of Cormen, Leiserson, Rivest, and Stein (2022), *Introduction to Algorithms (Fourth Edition)*, by Jeff Jacobs, Assistant Teaching Professor of Data Science and Analytics, Georgetown University.

Not so long ago, anyone who had heard the word "algorithm" was almost certainly a computer scientist or mathematician. With computers having become prevalent in our modern lives, however, the term is no longer esoteric. If you look around your home, you'll find algorithms running in the most mundane places: your microwave oven, your washing machine, and, of course, your computer. You ask algorithms to make recommendations to you: what music you might like or what route to take when driving. Our society, for better or for worse, asks algorithms to suggest sentences for convicted criminals. You even rely on algorithms to keep you alive, or at least not to kill you: the control systems in your car or in medical equipment.[^1] The word "algorithmm" appears somewhere in the news seemingly every day.

Therefore, it behooves you to understand algorithms not just as a student or practitioner of computer science, but as a citizen of the world. Once you understand algorithms, you can educate others about what algorithms are, how they operate, and what their limitations are.

This book provides a comprehensive introduction to the modern study of computer algorithms. It presents many algorithms and covers them in considerable depth, yet makes their design accessible to all levels of readers. All the analyses are laid out, some simple, some more involved. We have tried to keep explanations clear without sacrificing depth of coverage or mathematical rigor.

Each chapter presents an algorithm, a design technique, an application area, or a related topic. Algorithms are described in English and in a pseudocode designed to be readable by anyone who has done a little programming. The book contains 231 figures -- many with multiple parts -- illustrating how the algorithms work. Since we emphasize *efficiency* as a design criterion, we include careful analyses of the running times of the algorithms.

The text is intended primarily for use in undergraduate or graduate courses in algorithms or data structures. Because it discusses engineering issues in algorithm design, as well as mathematical aspects, it is equally well suited for self-study by technical professionals.

In this, the fourth edition, we have once again updated the entire book. The changes cover a broad spectrum, including new chapters and sections, color illustrations, and what we hope you’ll find to be a more engaging writing style.

**To the teacher**

We have designed this book to be both versatile and complete. You should find it useful for a variety of courses, from an undergraduate course in data structures up
through a graduate course in algorithms. Because we have provided considerably
more material than can fit in a typical one-term course, you can select the material
that best supports the course you wish to teach.

You should find it easy to organize your course around just the chapters you need. We have made chapters relatively self-contained, so that you need not
worry about an unexpected and unnecessary dependence of one chapter on another.
Whereas in an undergraduate course, you might use only some sections
from a chapter, in a graduate course, you might cover the entire chapter.

We have included 931 exercises and 162 problems. Each section ends with exercises, and each chapter ends with problems. The exercises are generally short questions
that test basic mastery of the material. Some are simple self-check thought
exercises, but many are substantial and suitable as assigned homework. The problems
include more elaborate case studies which often introduce new material. They
often consist of several parts that lead the student through the steps required to arrive
at a solution.

As with the third edition of this book, we have made publicly available solutions to some, but by no means all, of the problems and exercises. You can find these solutions on our website, http://mitpress.mit.edu/algorithms/. You will want to check this site to see whether it contains the solution to an exercise or problem that you
plan to assign. Since the set of solutions that we post might grow over time, we
recommend that you check the site each time you teach the course.

We have starred ($\star$) the sections and exercises that are more suitable for graduate students than for undergraduates. A starred section is not necessarily more difficult
than an unstarred one, but it may require an understanding of more advanced mathematics. Likewise, starred exercises may require an advanced background or more than average creativity.

**To the student**

We hope that this textbook provides you with an enjoyable introduction to the field of algorithms. We have attempted to make every algorithm accessible and interesting.
To help you when you encounter unfamiliar or difficult algorithms, we
describe each one in a step-by-step manner. We also provide careful explanations
of the mathematics needed to understand the analysis of the algorithms and supporting
figures to help you visualize what is going on.

Since this book is large, your class will probably cover only a portion of its material. Although we hope that you will find this book helpful to you as a course
textbook now, we have also tried to make it comprehensive enough to warrant space on your future professional bookshelf.

What are the prerequisites for reading this book?

* You need some programming experience. In particular, you should understand recursive procedures and simple data structures, such as arrays and linked lists (although @sec-10-2 covers linked lists and a variant that you may find new).
* You should have some facility with mathematical proofs, and especially proofs by mathematical induction. A few portions of the book rely on some knowledge
of elementary calculus. Although this book uses mathematics throughout, Part I
and Appendices A–D teach you all the mathematical techniques you will need.
Our website, http://mitpress.mit.edu/algorithms/, links to solutions for some of
the problems and exercises. Feel free to check your solutions against ours. We ask,
however, that you not send your solutions to us.
To the professional
The wide

[^1]: To understand many of the ways in which algorithms inufluence our daily lives, see @fry_hello_2018.