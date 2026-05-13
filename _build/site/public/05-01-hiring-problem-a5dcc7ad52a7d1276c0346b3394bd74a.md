(sec-5-1)=
# 5.1 The hiring problem

Suppose that you need to hire a new office assistant. Your previous attempts at hiring have been unsuccessful, and you decide to use an employment agency. The
employment agency sends you one candidate each day. You interview that person
and then decide either to hire that person or not. You must pay the employment
agency a small fee to interview an applicant. To actually hire an applicant is more
costly, however, since you must ûre your current ofûce assistant and also pay a
substantial hiring fee to the employment agency. You are committed to having, at
all times, the best possible person for the job. Therefore, you decide that, after
interviewing each applicant, if that applicant is better qualiûed than the current
ofûce assistant, you will ûre the current ofûce assistant and hire the new applicant.
You are willing to pay the resulting price of this strategy, but you wish to estimate
what that price will be.

The procedure {sc}`Hire-Assistant` on the facing page expresses this strategy for hiring in pseudocode. The candidates for the office assistant job are numbered 1 through $n$ and interviewed in that order. The procedure assumes that after interviewing candidate $i$, you can determine whether candidate $i$ is the best candidate you have seen so far. It starts by creating a dummy candidate, numbered 0, who is less qualified than each of the other candidates.

The cost model for this problem differs from the model described in Chapter 2. We focus not on the running time of {sc}`Hire-Assistant`, but instead on the fees paid for interviewing and hiring. On the surface, analyzing the cost of this algorithm