# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 22-01-24 [Problem Link](https://leetcode.com/problems/set-mismatch/description/?envType=daily-question&envId=2024-01-22)
## 645. Set Mismatch


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->
**Marked the Elements :**
- Iterated through the array.
- Marked the presence of elements by changing the sign of the element at the index equal to the absolute value of the current element.

**Identified Duplicate :**
- If the element at the calculated index is already negative, it means the absolute value of the current element is a duplicate.

**Identifying Missing :**
- Found the positive element in the array, which corresponds to the missing element.

**Result Array :**
- Created an array `jawab` to store the identified duplicate and missing elements.

**Return Result :**
   - Returned the `jawab` array as the final output.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(l)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$l$ : length of array
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Variables to store the duplicate, missing, and the final result
    static int duplicate;
    static int missing;
    static int[] result = new int[2];

    public int[] findErrorNums(int[] nums) {

        // Iterating through the array
        for (int s : nums) {
            // Marking the element at the index equal to the absolute value of 's' as negative
            if (nums[Math.abs(s) - 1] > 0) {
                nums[Math.abs(s) - 1] *= -1;
            } else {
                // If the element is already negative, it is the duplicate
                duplicate = Math.abs(s);
            }
        }
        
        // Finding the positive element in the array, which corresponds to the missing element
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > 0) {
                missing = i + 1;
                break;
            }
        }
        
        // Storing the results in the 'result' array
        result[0] = duplicate;
        result[1] = missing;
        return result;
    }
}

```