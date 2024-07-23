Kadane's Algorithm : Maximum Subarray Sum in an Array

Question :- Given an integer array `nums`, find the subarray with the largest sum, and return _its sum_.

**Example 1:**

**Input:** nums = [-2,1,-3,4,-1,2,1,-5,4]
**Output:** 6
**Explanation:** The subarray [4,-1,2,1] has the largest sum 6.


**Example 2:**

**Input:** nums = [1]

**Output:** 1

**Explanation:** The subarray [1] has the largest sum 1.


**Example 3:**

**Input:** nums = [5,4,-1,7,8]

**Output:** 23

**Explanation:** The subarray [5,4,-1,7,8] has the largest sum 23.


**Brute Force Approach** :- 

```python
import sys

def maxSubArray(arr):
    max_sum = -sys.maxsize - 1
    for i in range(len(arr)):
        for j in range(i, len(arr)):
            sum_so_far = 0
            for k in range(i, j+1):
                sum_so_far += arr[k]
            max_sum = max(max_sum, sum_so_far)
    return max_sum
```

**Time Complexity:** O($N^3$)

**Space Complexity:** O(1)


**Optimal Approach** :-

```python
def maxSubArray(arr):
    max_sum = arr[0]
    sum_so_far = 0
    for num in arr:
        sum_so_far += num
        if sum_so_far > max_sum:
            max_sum = sum_so_far
        if sum_so_far < 0:
            sum_so_far = 0
    return max_sum
```

**Time Complexity:** O(N)

**Space Complexity:** O(1)


The idea of **Kadane’s algorithm** is to maintain a variable **max_ending_here** that stores the maximum sum contiguous subarray ending at current index and a variable **max_so_far** stores the maximum sum of contiguous subarray found so far, Everytime there is a positive-sum value in **max_ending_here** compare it with **max_so_far** and update **max_so_far** if it is greater than **max_so_far**.

