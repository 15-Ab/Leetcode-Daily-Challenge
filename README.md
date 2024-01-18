# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 18-01-24 [Problem Link](https://leetcode.com/problems/climbing-stairs/description/?envType=daily-question&envId=2024-01-18)
## 70. Climbing Stairs


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem is a classic dynamic programming problem, often referred to as the "Climbing Stairs" problem. The goal is to find the number of distinct ways to climb a staircase with n steps. At each step, one can either climb 1 or 2 steps. The task is to determine the total number of unique combinations to reach the top.

# Approach
<!-- Describe your approach to solving the problem. -->
**Base Cases :**
- If there are 0 steps, there is only one way to climb (doing nothing).
- If there is 1 step, there is only one way to climb (taking one step).

**Dynamic Programming Array :**
- Created an array step of size `n + 1` to store the number of ways to climb stairs at each step.
- Initialized the base cases (`step[0] = 1` and `step[1] = 1`).

**Dynamic Programming Loop :** 
- Used a loop to iterate from the 2nd step to the nth step.
- For each step `i`, the number of ways to reach that step is the sum of the ways to reach the previous two steps (`step[i - 1] + step[i - 2]`).

**Result :**

The final result is stored in `step[n]`, which represents the total number of unique ways to climb n stairs.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(s)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$O(s)$ :  steps to reach the top
- Space complexity : $O(s)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int climbStairs(int n) {
        // Base cases
        if (n == 0) {
            return 1;
        }
        if (n < 0) {
            return 0;
        }

        // Array to store the number of ways to climb stairs at each step
        int[] step = new int[n + 1];
        
        // Base cases for 0 and 1 steps
        step[0] = 1;
        step[1] = 1;

        // Dynamic programming loop to calculate the number of ways
        for (int i = 2; i <= n; i++) {
            step[i] = step[i - 1] + step[i - 2];
        }

        // Returning the result for climbing n stairs
        return step[n];
    }
}

```
