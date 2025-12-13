# Data-Structures-and-Algorithms
Practice exercises for multiple programming languages and frameworks.
#DAY 1
Day 1 : Two Numbers Add Up to Target

Problem: We have a list of numbers and a target. Find two numbers in the list that add up to the target, and return their positions.

Steps (Algorithm):

1. Start with an empty notebook (dictionary).

2. Go through each number one by one.

3. For each number, check if the partner (target – current number) is already in the notebook.

4. If yes → return both positions.

5. If no → write down the current number and its position.



DAY 2
Steps (Algorithm):

 Start with current_sum = 0 and max_sum = very small.
 
 Add each number to current_sum.

  If current_sum is bigger than max_sum, update max_sum.

  If current_sum goes below 0, reset it to 0 (start fresh).
  
 At the end, max_sum is the answer.


 
 Day 3 – Sort Colors (0s, 1s, 2s)
Problem: You have a list with only 0s, 1s, and 2s. Sort them so all 0s come first, then 1s, then 2s.

Steps (Algorithm):

  Use three pointers: low, mid, high.

  While mid <= high:

  If number is 0 → swap with low, move both forward.

  If number is 1 → just move mid.

  If number is 2 → swap with high, move high backward.

  Continue until sorted.


Day 4
Problem :We are given a list of numbers and a target. Find all unique sets of four numbers that add up to the target.
Steps (Algorithm)

Sort the list (makes it easier to avoid duplicates).

Use two loops to fix the first two numbers.

For the remaining two numbers, use the two-pointer technique (one pointer at the start, one at the end).

If the sum of all four numbers equals the target → save it.

Move pointers carefully to avoid duplicates.



Day 5 - Merge Intervals
Problem : We are given a list of intervals (like meeting times). Merge all overlapping intervals into one.

Steps (Algorithm)

Sort intervals by their start time.

Start with the first interval.

For each new interval:

If it overlaps with the previous one → merge them (take min start, max end).

If not then add it as a new interval.

Continue until all intervals are processed.



DAY 6
Algorithm
Convert the string to a list (so removals are easy).

First pass (left to right):

  Maintain a counter balance of unmatched (seen so far.

  If char is (: increment balance.

  If char is ):

   If balance == 0: mark this) for removal (it's invalid).

   Else: decrement balance (it matches a previous ().

Second pass (right to left):

   balance now equals the number of extra ( to remove.

   Traverse backward and remove ( until balance is zero.

Join remaining characters and return.
