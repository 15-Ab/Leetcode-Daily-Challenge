# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 10-03-24 [Problem Link](https://leetcode.com/problems/intersection-of-two-arrays/description/?envType=daily-question&envId=2024-03-10)
## 349. Intersection of Two Arrays

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the intersection of two arrays, `nums1` and `nums2`. The code uses a set to efficiently check for common elements between the arrays.

# Approach
<!-- Describe your approach to solving the problem. -->
**List Initialization :**
   - Initialized an empty list (`ans`) to store the elements of the intersection.

**Set Conversion :**
   - Converted the first array (`nums1`) to a set (`set`) for efficient element lookup.

**Intersection Check :**
   - Iterated through each element (`num`) in the second array (`nums2`).
   - Checked if the current element is present in the set (`set`).
   - If present, removed the element from the set and add it to the `ans` list.

**Array Conversion :**
   - Converted the list of intersection elements (`ans`) to an integer array.

**Return :**
   - Returned the final integer array containing the intersection.
   - 
---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity : $O(m + n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : length of first array


$m$ : length of second array
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
 
  public int[] intersection(int[] nums1, int[] nums2) {
    // Creating a list to store the intersection elements.
    List<Integer> ans = new ArrayList<>();

    // Converting nums1 to a set for faster lookup.
    Set<Integer> set = Arrays.stream(nums1).boxed().collect(Collectors.toSet());

    // Iterating through each element in nums2.
    for (final int num : nums2)
      // Checking if the element is present in the set (intersection).
      if (set.remove(num))
        // Adding the common element to the result list.
        ans.add(num);

    // Converting the list to an array and return it.
    return ans.stream().mapToInt(Integer::intValue).toArray();
  }
}

```