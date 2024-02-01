# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 01-02-24 [Problem Link](https://leetcode.com/problems/divide-array-into-arrays-with-max-difference/description/?envType=daily-question&envId=2024-02-01)
## 2966. Divide Array Into Arrays With Max Difference

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of my code is to divide an array `nums` into subarrays of size 3, sort each subarray, and check whether the differences between adjacent elements in each subarray are within a given threshold `k`. If the differences exceed the threshold for any subarray, my function returns an empty 2D array. Otherwise, it returns the 2D array containing the sorted subarrays.

# Approach
<!-- Describe your approach to solving the problem. -->
**Sorted the Array :**
   - Sorted the input array `nums` using `Arrays.sort(nums)`.

**Initialized Result Array :**
   - Determined the length of the input array `n`.
   - Created a 2D array `a` to store the divided subarrays. The number of rows in `a` is calculated as `n/3` since each subarray has 3 elements.

**Iterated through Sorted Array in Chunks of 3 :**
   - Used a for loop to iterate through the sorted array in chunks of 3.
   - Calculated the row index `r` for the result array based on the current index `i`.

**Check Differences and Store Subarrays :**
   - Created a temporary array `t` to store the current chunk of 3 elements.
   - Checked if the differences between elements in the chunk (`t[2] - t[1]`, `t[2] - t[0]`, `t[1] - t[0]`) exceed the threshold `k`.
   - If the condition is met for any chunk, returned an empty 2D array.
   - Otherwise, stored the sorted subarray `t` in the result array `a`.

**Return the Result Array :**
   - After processing all chunks, returned the result array `a`.

My code divides the array into sorted subarrays of size 3, checks if the differences between elements in each subarray are within a given threshold, and returns the result accordingly. My approach is focused on breaking down the problem into smaller parts and efficiently handling the sorting and validation for each subarray.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n*logn)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of the input array
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int[][] divideArray(int[] nums, int k) {
        // Sorting the input array
        Arrays.sort(nums);
        
        // Calculating the length of the result array
        int n = nums.length;
        
        // Creating a 2D array to store the divided arrays
        // Each subarray will have 3 elements
        int[][] a = new int[n/3][3];
        
        // Iterating through the sorted array in chunks of 3
        for (int i = 0; i <= n - 3; i += 3) {
            // Calculating the row index for the result array
            int r = i / 3;
            
            // Creating a temporary array to store the current chunk of 3 elements
            int[] t = new int[3];
            t[0] = nums[i];
            t[1] = nums[i+1];
            t[2] = nums[i+2];
            
            // Checking if the difference between any two elements in the chunk is greater than k
            if (t[2] - t[1] > k || t[2] - t[0] > k || t[1] - t[0] > k) {
                // If the condition is not met, returning an empty 2D array
                return new int[0][0];
            }
            
            // Storing the current chunk in the result array
            a[r] = t;
        }
        
        // Returning the result array
        return a;
    }
}

```