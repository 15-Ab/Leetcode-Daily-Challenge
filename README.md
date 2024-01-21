# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 21-01-24 [Problem Link](https://leetcode.com/problems/house-robber/description/?envType=daily-question&envId=2024-01-21)
## 198. House Robber


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My Java code aims to find the maximum amount that can be robbed from an array of houses, where adjacent houses cannot be robbed simultaneously.

# Approach
<!-- Describe your approach to solving the problem. -->
**Base Cases :**
- Handled base cases for arrays with lengths 0, 1, 2, and 3.

**Initialization :**
- Initialized a pointer `p` to track the position in the array.
- Updated the value at index 2 by adding the value at index 0.

**Dynamic Programming :**
- Iterated from index 3 to the end of the array.
- Updated the value at the current index by adding the maximum of the values at indices `i-2` and `i-3`.

**Result Calculation :**
- Returned the maximum value between the last two elements of the modified array.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(l)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$l$ : length of the input array
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
public class Solution {
    
    public int rob(int[] nums) {

        // Base cases for small arrays
        if (nums.length == 0) {
            return 0;
        }
        if (nums.length == 1) {
            return nums[0];
        }
        if (nums.length == 2) {
            return Math.max(nums[0], nums[1]);
        }
        if (nums.length == 3) {
            return Math.max(nums[0] + nums[2], nums[1]);
        }

        // Initializing a pointer 'p' to track the position
        int p = 0;
        // Updating the value at index 2 by adding the value at index 0
        nums[2] += nums[0];

        // Iterating from index 3 to the end of the array
        for (int i = 3; i < nums.length; i++) {
            // Updating the value at the current index by adding the maximum of the two preceding values
            nums[i] += Math.max(nums[i - 2], nums[i - 3]);
        }

        // Returning the maximum value between the last two elements of the modified array
        return Math.max(nums[nums.length - 1], nums[nums.length - 2]);
    }
}

```