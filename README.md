# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 02-03-24 [Problem Link](https://leetcode.com/problems/squares-of-a-sorted-array/description/?envType=daily-question&envId=2024-03-02)
## 977. Squares of a Sorted Array

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The given code aims to calculate the sorted squares of an array of integers. It uses a two-pointer approach to efficiently process the input array and produce the result array containing the squares in sorted order.

# Approach
<!-- Describe your approach to solving the problem. -->
- Initialize variables: 
   - `size`: Get the size of the input array.
   - `result`: Initialize an array to store the sorted squares.
   - `index`: Initialize an index to populate the result array in reverse order.

- Two-pointer traversal :
   - Use two pointers, `left` starting from the beginning and `right` starting from the end of the array.
   - Compare the absolute values of elements at `left` and `right` pointers.

- Square and store :
   - If the absolute value at `left` is greater, square it and store it in the `result` array at the specified `index`.
   - If the absolute value at `right` is greater, square it and store it in the `result` array at the specified `index`.

- Move pointers :
   - Adjust the pointers (`left` or `right`) based on the comparison.

- Repeat until traversal is complete.

- Return the `result` array containing the sorted squares.

My approach ensures that the result array is populated with sorted squares in a time-efficient manner, utilizing the two-pointer technique.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : size of the input array
- Space complexity : $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Method to calculate sorted squares of input numbers
    public int[] sortedSquares(int[] nums) {
        // Getting the size of the input array
        final int size = nums.length;
        
        // Initializing an array to store the result
        int[] result = new int[size];
        
        // Initializing an index for storing results in reverse order
        int index = size - 1;

        // Looping through the input array using two pointers (left and right)
        for (int left = 0, right = size - 1; left <= right;) {
            // Comparing the absolute values of numbers at left and right pointers
            if (Math.abs(nums[left]) > Math.abs(nums[right])) {
                // If the absolute value at left is greater, squaring it and storing in result
                result[index--] = nums[left] * nums[left++];
            } else {
                // If the absolute value at right is greater, squaring it and storing in result
                result[index--] = nums[right] * nums[right--];
            }
        }

        // Returning the array containing sorted squares
        return result;
    }
}
```