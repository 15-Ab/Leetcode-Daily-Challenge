# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 16-03-24 [Problem Link](https://leetcode.com/problems/contiguous-array/description/?envType=daily-question&envId=2024-03-16)
## 525. Contiguous Array

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem requires finding the maximum length of a contiguous subarray with an equal number of 0s and 1s. To approach this, I can utilize the concept of a running sum. 

# Approach
<!-- Describe your approach to solving the problem. -->
**Running Sum :** I maintained a running sum of the elements encountered so far, where I increment the sum by 1 for every 1 encountered and decrement it by 1 for every 0 encountered.

**Equal Number of 0s and 1s :** If the running sum is equal at two different indices, it implies that the number of 0s and 1s between those indices is the same.

**Maximum Length :** I aim to maximize the length of the subarray with an equal number of 0s and 1s.

By storing the running sum and its corresponding index in a map, I can efficiently determine the maximum length by checking if a running sum repeats. If it does, the difference between the current index and the index stored for that running sum gives the length of the subarray with equal 0s and 1s. 

Through this approach, I can efficiently find the maximum length of the required subarray.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(a)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$a$ : length of the input array
- Space complexity : $O(a)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  
  // Static variable to store the maximum length of subarray with equal number of 0s and 1s
  static int maxLength;
  
  // Method to find the maximum length of subarray with equal number of 0s and 1s
  public int findMaxLength(int[] nums) {

    // Initializing the maximum length to 0
    maxLength = 0;

    // Variable to keep track of the running sum
    int runningSum = 0;
    
    // Map to store the running sum and its corresponding index
    Map<Integer, Integer> sumToIndex = new HashMap<>();
    
    // Initializing the map with running sum 0 and index -1
    sumToIndex.put(0, -1);

    // Looping through the array
    for (int i = 0; i < nums.length; i++) {
      // Updating the running sum based on the current element
      runningSum += (nums[i] == 1) ? 1 : -1;
      // If the running sum is already present in the map
      if (sumToIndex.containsKey(runningSum)){
        // Updating the maximum length with the difference between the current index and the index stored in the map
        maxLength = Math.max(maxLength, i - sumToIndex.get(runningSum));
      }
      else{
        // If the running sum is not present in the map, adding it along with its index
        sumToIndex.put(runningSum, i);
      }
    }

    // Returning the maximum length of subarray with equal number of 0s and 1s
    return maxLength;
  }
}
```