# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Answer:

Based on the lecture slides, when the leftmost element is chosen as the pivot, there are three possible outcomes for whether the pivot is a good one. A good pivot is one that lies near the middle of the sorted array, and the leftmost element will be a good pivot 50% of the time. If the leftmost element is smaller or larger than the good pivot, there is a 25% chance of picking that element in either case.

For the median-of-three method, the pivot is chosen from the first, middle, and last elements and choose the median value as our pivot. For this lets consider the pivots (S, G, L) where S represents a smaller pivot than the good one, G represents a good pivot, and L represents a larger pivot. Considering all possible outcomes


$LLL = (1/4)^3 = 1/64$\
$GGG = (1/2)^3 = 1/8 = 8/64$\
$SSS = (1/4)^3 = 1/64$\
$LGS = (1/4)^2 * (1/2) = 1/32 = 2/64$\
$LSS = (1/4)^3 = 1/64$\
$LLG = (1/4)^2 * (1/2) = 1/32 = 2/64$\
$GSS = (1/4)^2 * (1/2) = 1/32 = 2/64$\
$LGG = (1/4) * (1/2)^2 = 1/16 = 4/64$\
$GGS = (1/4) * (1/2)^2 = 1/16 = 4/64$\
$LLS = (1/4)^3 = 1/64$

A good pivot occurs when the good pivot (G) is one of the three selected pivots. For this we need to consider the following outcomes

$GGG$ has only one permutation resulting in $8/64$\
$GGS$ has $GGS, GSG, SGG$ resulting in $3 * (4/64) = 12/64$\
$LGG$ has $LGG, GLG, GGL$ resulting in $3 * (4/64) = 12/64$\
$LGS$ has $LGS, LSG, GLS, GSL, SGL, SLG$ resulting in $6 * 2/64 = 12/64$

If we add all these outcomes with good pivot we get $8/64 + (3 * (12/64)) = 44/64 = 0.6875$ that turns out to be close to $0.6875 * 100 = 68.75$%

So the probability of using median of three to pick our pivot is 68.75%. Whereas the probability for the leftmost approach is 50% meaning that median of three method is better than leftmost approach by 18.75% 


References:

Lecture slides are used to start doing the proof

quicksort-pivot-vijaykodru

I looked at my repository for reference on how I made the proof last time

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice
