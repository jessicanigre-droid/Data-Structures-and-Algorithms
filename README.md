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






Algorithms.ipynb_

Day 1 : Two Numbers Add Up to Target

Problem: We have a list of numbers and a target. Find two numbers in the list that add up to the target, and return their positions.

Steps (Algorithm):

    Start with an empty notebook (dictionary).

    Go through each number one by one.

    For each number, check if the partner (target - current number) is already in the notebook.

    If yes then return both positions.

    If no then write down the current number and its position.

def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        partner = target - num
        if partner in seen:
            return [seen[partner], i]
        seen[num] = i
    return []

print(two_sum([2,7,11,15], 9))  # [0,1]

[0, 1]

Day 2 : Largest Sum in a Subarray (subset)

Problem: Find the part of the list (continuous numbers) that gives the biggest sum.

Steps (Algorithm):

Start with current_sum = 0 and max_sum = very small.

Add each number to current_sum.

If current_sum is bigger than max_sum, update max_sum.

If current_sum goes below 0, reset it to 0 (start fresh).

At the end, max_sum is the answer.

    List item
    List item

import numpy as np
def highest_subarray(x):
  h=[]
  for i in x:
    if i > 0:
      h.append(i)

def max_subarray(nums):
    current_sum = 0
    max_sum = float('-inf')
    for num in nums:
        current_sum += num
        max_sum = max(max_sum, current_sum)
        if current_sum < 0:
            current_sum = 0
    return max_sum

print(max_subarray([-2,1,-3,4,-1,2,1,-5,4]))  # 6

6

Day 3 : Sort Colors (0s, 1s, 2s)

Problem: You have a list with only 0s, 1s, and 2s. Sort them so all 0s come first, then 1s, then 2s.

Steps (Algorithm):

Use three pointers: low, mid, high.

While mid <= high:

    If number is 0 then swap with low, move both forward.

    If number is 1 then just move mid.

    If number is 2 then swap with high, move high backward.

Continue until sorted.


def sort_colors(nums):
    low, mid, high = 0, 0, len(nums) - 1
    while mid <= high:
        if nums[mid] == 0:
            nums[low], nums[mid] = nums[mid], nums[low]
            low += 1
            mid += 1
        elif nums[mid] == 1:
            mid += 1
        else:  # nums[mid] == 2
            nums[mid], nums[high] = nums[high], nums[mid]
            high -= 1
    return nums

print(sort_colors([2,0,2,1,1,0]))  # [0,0,1,1,2,2]

[0, 0, 1, 1, 2, 2]

Day 4 Problem :We are given a list of numbers and a target. Find all unique sets of four numbers that add up to the target. Steps (Algorithm)

Sort the list (makes it easier to avoid duplicates).

Use two loops to fix the first two numbers.

For the remaining two numbers, use the two-pointer technique (one pointer at the start, one at the end).

If the sum of all four numbers equals the target → save it.

Move pointers carefully to avoid duplicates.

def four_sum(nums, target):
    nums.sort()
    res = []
    n = len(nums)
    for i in range(n-3):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        for j in range(i+1, n-2):
            if j > i+1 and nums[j] == nums[j-1]:
                continue
            left, right = j+1, n-1
            while left < right:
                total = nums[i] + nums[j] + nums[left] + nums[right]
                if total == target:
                    res.append([nums[i], nums[j], nums[left], nums[right]])
                    left += 1
                    right -= 1
                    while left < right and nums[left] == nums[left-1]:
                        left += 1
                    while left < right and nums[right] == nums[right+1]:
                        right -= 1
                elif total < target:
                    left += 1
                else:
                    right -= 1
    return res

# Example
print(four_sum([1,0,-1,0,-2,2], 0))

[[-2, -1, 1, 2], [-2, 0, 0, 2], [-1, 0, 0, 1]]

Day 5 - Merge Intervals Problem : We are given a list of intervals (like meeting times). Merge all overlapping intervals into one.

Steps (Algorithm)

Sort intervals by their start time.

Start with the first interval.

For each new interval:

If it overlaps with the previous one → merge them (take min start, max end).

If not then add it as a new interval.

Continue until all intervals are processed.

def merge_intervals(intervals):
    intervals.sort(key=lambda x: x[0])
    merged = []
    for interval in intervals:
        if not merged or merged[-1][1] < interval[0]:
            merged.append(interval)
        else:
            merged[-1][1] = max(merged[-1][1], interval[1])
    return merged

# Example
print(merge_intervals([[1,3],[2,6],[8,10],[15,18]]))

[[1, 6], [8, 10], [15, 18]]

DAY 6

Given a string s of "(',')" and lowercase English characters. Your task is to remove your minimum number of paranteses ('('or')') , in any positions so that the resulting paraenteses string is valid and return any valid string.bold text

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






DAY 7

Algorithm: Sort String by Character Frequency

Start with an input string s.

Count frequencies: For each character in s, calculate how many times it appears.

Store results: Keep the characters and their frequencies in a data structure (like a dictionary or list of pairs).

Sort characters: Arrange the characters in decreasing order of frequency.

    If two characters have the same frequency, their order can be arbitrary.

Build output string: For each character in the sorted list, repeat it according to its frequency and append it to the result string.

Return the result string.

End.
