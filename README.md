# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 17-01-24 [Problem Link](https://leetcode.com/problems/unique-number-of-occurrences/description/?envType=daily-question&envId=2024-01-17)
## 1207. Unique Number of Occurrences


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of this problem is to determine whether the counts of occurrences of distinct elements in the array are unique. To achieve this, I'm using a HashMap to store the count of occurrences for each unique element and then use a HashSet to keep track of the unique counts. If, at any point, I encounter a count that already exists in the HashSet, I can conclude that the counts are not unique.

# Approach
<!-- Describe your approach to solving the problem. -->
- Created a `HashMap<Integer, Integer>` named `occurrenceCountMap` to store the count of occurrences for each unique element.
- Iterated through the input array (`arr`) and update the counts in the `occurrenceCountMap`.
Created a `HashSet<Integer>` named `uniqueCounts` to store the counts of occurrences.
- Iterated through the values in the `occurrenceCountMap` and check for uniqueness.
- - If the count is already present in the `uniqueCounts`, returned `false` (counts are not unique).
- - Otherwise, added the count to the `uniqueCounts`.
- If the loop completes without returning `false`, return `true` (counts are unique).
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(u)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$u$ : number of unique elements
- Space complexity : $O(u)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        // Creating a HashMap to store the count of occurrences of each unique element.
        HashMap<Integer, Integer> m = new HashMap<>();

        // Iterating through the array and update the counts in the HashMap.
        for (int i : arr) {
            m.put(i, m.getOrDefault(i, 0) + 1);
        }

        // Creating a HashSet to store the counts of occurrences.
        HashSet<Integer> h = new HashSet<>();

        // Iterating through the values in the HashMap and check for uniqueness.
        for (int count : m.values()) {
            // If the count is already present in the HashSet, returning false.
            if (h.contains(count)) {
                return false;
            }
            // Otherwise, adding the count to the HashSet.
            h.add(count);
        }

        // If the loop completes without returning false, returning true.
        return true;
    }
}

```
