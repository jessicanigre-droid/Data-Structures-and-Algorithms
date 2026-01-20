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





DAY 8
Count characters in s1.

   Build a frequency map of all characters in s1.

Use a sliding window of length len(s1) over s2.

   For each window, count characters.

   Compare with s1’s frequency map.

Optimization:

   Instead of recomputing counts for each window, update counts incrementally:

   Add the new character entering the window.

   Remove the old character leaving the window.

Check equality:

   If at any point the frequency maps match, return true.

   If no match after scanning, return false.



DAY 9: Palindrome Partitioning
Problem: Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.
Algorithm: Backtracking with recursion
1. Use backtracking to explore all possible partitions of the string
2. At each step, check if the current substring is a palindrome
3. If yes, add it to the current path and recursively partition the remaining string
4. When we reach the end of the string, add the current partition to results
5. Backtrack by removing the last added substring
Time Complexity: O(n * 2^n)
Space Complexity: O(n)




DAY 10: Minimum Window Substring
Problem: Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".
Algorithm: Sliding Window with Two Pointers
1. Use two pointers (left and right) to create a window
2. Expand window by moving right pointer, tracking character frequencies
3. When all characters from t are included, contract window from left
4. Track the minimum window that contains all characters
5. Return the smallest valid window found

Time Complexity:O(m + n)  
Space Complexity:O(m + n)





Day 13: Subsets (Power Set)
ALGORITHM: Iterative Bitmask Construction
1. Initialize result with empty subset: res = [[]]
2. For each element x in nums:
   a. Copy all existing subsets
   b. Append x to each existing subset  
   c. Add new subsets to result
3. Each iteration doubles the subsets (2^n total)



Day 14: Generate Parentheses
ALGORITHM: Backtracking with Validity Constraints
1. Track: current string, open_count, close_count
2. Can add "(" if open_count < n
3. Can add ")" if close_count < open_count  
4. Stop when len(current) == 2*n
5. Prune invalid partial solutions early



Day 15: LRU Cache
ALGORITHM: Doubly Linked List Simulation via OrderedDict
GET(key):
1. If key missing: return -1
2. Move key to end (most recently used)
3. Return value

PUT(key, value):
1. Move existing key to end OR insert new
2. If size > capacity: remove first element (LRU)



Day 16: First Missing Positive
ALGORITHM: Cyclic Sort (Index = Value-1)
1. For each index i:
   - While nums[i] ∈ [1,n] AND nums[nums[i]-1] != nums[i]:
     - Swap nums[i] with nums[nums[i]-1]
2. First i where nums[i] != i+1 → answer = i+1
3. If all correct: return n+1



Day 17: Spiral Matrix
ALGORITHM: Boundary Contraction
Initialize: top=0, bottom=m-1, left=0, right=n-1
While top≤bottom AND left≤right:
1. Traverse top row = top++
2. Traverse right column → right--
3. Traverse bottom row (if valid) = bottom--
4. Traverse left column (if valid) = left++



Day 18: Valid Sudoku
ALGORITHM: Three-Constraint Hashing
Maintain 27 sets:
- 9 row sets, 9 column sets, 9 3x3 box sets
For each cell (r,c):
1. box_idx = (r//3)*3 + (c//3)
2. If digit in ANY of 3 sets → INVALID
3. Add to all 3 sets



Day 19: Word Search
ALGORITHM: DFS Backtracking from Each Cell
For each cell (i,j):
1. If board[i][j] == word[0]:
   - Mark visited, DFS 4 directions with k=1
   - Unmark after exploration
2. Directions: up, down, left, right
3. Base: k == len(word) → True




Day 20: Flatten Binary Tree
ALGORITHM: Reverse Preorder Traversal (Right-Left-Root)
Use prev pointer:
1. Recurse right subtree
2. Recurse left subtree  
3. node.right = prev, node.left = None
4. prev = node
Maintains preorder: root to left to right


DAY 21: Palindrome Linked List

**Problem:** Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

**Algorithm:** Fast/Slow Pointer + Reverse Second Half
1. Use fast and slow pointers to find the middle of the list
2. Reverse the second half of the list
3. Compare first half with reversed second half node by node
4. If all values match, it's a palindrome
5. Return true if matched, false otherwise

**Time Complexity:** O(n)  
**Space Complexity:** O(1)



DAY 22: Reverse Nodes in k-Group

**Problem:** Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list. k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

**Algorithm:** Group Reversal with Pointer Manipulation
1. Identify groups of k nodes using a counter
2. Reverse each complete group by manipulating pointers
3. Connect reversed groups together maintaining list continuity
4. If remaining nodes < k, leave them unchanged
5. Return the new head

**Time Complexity:** O(n)  
**Space Complexity:** O(1)





DAY 23: Merge Two Sorted Lists
**Problem:** You are given the heads of two sorted linked lists list1 and list2. Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists. Return the head of the merged linked list.
**Algorithm:** Two-Pointer Merge
1. Use a dummy node to start the merged list
2. Compare values from both lists, attach smaller node
3. Move pointer of the list from which node was taken
4. Continue until one list is exhausted
5. Attach remaining nodes from non-empty list
6. Return dummy.next

**Time Complexity:** O(m + n)  
**Space Complexity:** O(1)



DAY 24: Add Two Numbers (Linked List)
**Problem:** You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
**Algorithm:** Digit-by-Digit Addition with Carry
1. Traverse both lists simultaneously
2. Add corresponding digits plus carry from previous addition
3. Create new node with sum % 10
4. Update carry as sum // 10
5. Continue until both lists are exhausted and carry is 0
6. Return the result list

**Time Complexity:** O(max(m, n))  
**Space Complexity:** O(max(m, n))



DAY 25: Swap Adjacent Nodes
**Problem:** Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed).
**Algorithm:** Pairwise Pointer Swapping
1. Use dummy node to handle edge cases
2. For each pair, identify first and second nodes
3. Adjust pointers: prev → second, first → second.next, second → first
4. Move prev pointer to first (now in second position)
5. Repeat until no more pairs exist
6. Return dummy.next

**Time Complexity:** O(n)  
**Space Complexity:** O(1)






DAY 26: Add Two Numbers (Same as Day 24)

**Problem:** You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list. You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Algorithm:** Digit-by-Digit Addition with Carry
1. Same algorithm as Day 24
2. Process digits in reverse order (already stored in reverse)
3. Handle carry propagation throughout
4. Create result nodes as we sum

**Time Complexity:** O(max(m, n))  
**Space Complexity:** O(max(m, n))







DAY 27: Swap Adjacent Nodes (Same as Day 25)

**Problem:** Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed).

**Algorithm:** Node Pointer Swapping (No Value Modification)
1. Same as Day 25 but emphasizes not modifying node values
2. Only manipulate the node pointers themselves
3. Maintain list structure integrity throughout
4. Use dummy node for cleaner edge case handling

**Time Complexity:** O(n)  
**Space Complexity:** O(1)






DAY 28: Largest Rectangle in Histogram

**Problem:** Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

**Algorithm:** Monotonic Stack
1. Maintain a stack of indices with increasing heights
2. When a smaller height is encountered, pop and calculate area
3. Width is determined by current index and index after popped element
4. Add sentinel (0) at end to clear remaining stack
5. Track maximum area throughout

**Time Complexity:** O(n)  
**Space Complexity:** O(n)






DAY 29: Min Stack

**Problem:** Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

**Algorithm:** Two Stacks (Main + Min Tracking)
1. Use one stack for all values
2. Use second stack to track minimum values
3. Push to min stack only when value ≤ current minimum
4. Pop from min stack only when popped value equals current min
5. getMin() returns top of min stack

**Time Complexity:** O(1) for all operations  
**Space Complexity:** O(n)





DAY 30: Implement Stack using Queues

**Problem:** Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top, pop, and empty).

**Algorithm:** Two Queues with Element Rotation
1. Use two queues (q1 and q2)
2. On push: add element to q2, then move all from q1 to q2, swap queues
3. This ensures newest element is always at front of q1
4. Pop and top operations become O(1) on q1
5. Empty check on q1

**Time Complexity:** Push O(n), Pop/Top O(1)  
**Space Complexity:** O(n)











DAY 31: BST Iterator

**Problem:** Implement the BSTIterator class that represents an iterator over the in-order traversal of a binary search tree (BST).

**Algorithm:** Controlled In-order Traversal with Stack
1. Initialize stack with all leftmost nodes from root
2. next(): Pop from stack (smallest element), add right subtree's leftmost nodes
3. This simulates in-order traversal on demand
4. hasNext(): Check if stack is non-empty
5. Space optimized - only store path to current node

**Time Complexity:** O(1) average per operation  
**Space Complexity:** O(h) where h is height










DAY 32: Trapping Rain Water

**Problem:** Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

**Algorithm:** Two Pointers from Both Ends
1. Use left and right pointers at both ends
2. Track left_max and right_max heights seen so far
3. Move pointer with smaller max height inward
4. Calculate trapped water as max_height - current_height
5. Update max heights as we progress

**Time Complexity:** O(n)  
**Space Complexity:** O(1)
















DAY 33: Maximum Depth of Binary Tree

**Problem:** Given the root of a binary tree, return its maximum depth. A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Algorithm:** Recursive DFS
1. Base case: null node returns depth 0
2. Recursive case: 1 + max(left subtree depth, right subtree depth)
3. Each node adds 1 to the maximum of its children's depths
4. Recursion naturally explores all paths

**Time Complexity:** O(n)  
**Space Complexity:** O(h) for recursion stack










DAY 35: Kth Smallest in BST

**Problem:** Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.

**Algorithm:** In-order Traversal (Sorted Order)
1. Perform in-order traversal (left, root, right)
2. In-order traversal of BST gives sorted sequence
3. Collect all values or count to k
4. Return the kth element (k-1 index in 0-indexed array)
5. Can optimize with early stopping at kth element

**Time Complexity:** O(n)  
**Space Complexity:** O(n)







DAY 36: Level Order Traversal

**Problem:** Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

**Algorithm:** BFS with Queue
1. Use queue to process nodes level by level
2. Track level size before processing each level
3. Process all nodes at current level
4. Add children to queue as you process nodes
5. Collect nodes at each level into separate lists

**Time Complexity:** O(n)  
**Space Complexity:** O(w) where w is max width










DAY 37: Sum Root to Leaf Numbers

**Problem:** You are given the root of a binary tree containing digits from 0 to 9 only. Each root-to-leaf path in the tree represents a number. Return the total sum of all root-to-leaf numbers.

**Algorithm:** DFS with Path Accumulation
1. Recursively traverse tree, building number digit by digit
2. At each node: current_number = previous * 10 + node.val
3. At leaf nodes, return the accumulated number
4. At internal nodes, return sum of left + right subtree results
5. Accumulate all leaf values

**Time Complexity:** O(n)  
**Space Complexity:** O(h) for recursion stack












DAY 38: Subtree of Another Tree

**Problem:** Given the roots of two binary trees root and subRoot, return true if there is a subtree of root with the same structure and node values of subRoot and false otherwise.

**Algorithm:** Recursive Tree Matching
1. Check if current node's tree matches subRoot (identical structure)
2. Use helper function to verify if two trees are identical
3. If not identical, recursively check left subtree
4. Also recursively check right subtree
5. Return true if any match is found

**Time Complexity:** O(m * n) where m, n are tree sizes  
**Space Complexity:** O(h) for recursion
