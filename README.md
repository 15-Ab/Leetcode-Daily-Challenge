# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 17-03-24 [Problem Link](https://leetcode.com/problems/insert-interval/description/?envType=daily-question&envId=2024-03-17)
## 57. Insert Interval

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of this code is to insert a new interval into a list of intervals while merging any overlapping intervals. 

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialization** : 
- Initialized an empty list `jawab` to store the merged intervals.

**Iterated Over Intervals** : 
- Iterated through the given list of intervals.
- Added intervals that ended before the start of the new interval directly to the result list `jawab`.

**Merged Overlapping Intervals** : 
- While iterating, merged intervals that overlap with the new interval.
- Updated the start and end values of the new interval accordingly.

**Added Merged Interval** :
- Added the merged new interval to the result list `jawab`.

**Added Remaining Intervals** :
- Added any remaining intervals from the input list to `jawab`.

**Result** :
- Converted the ArrayList `jawab` to a 2D array and return the result.

My approach ensures that the intervals are merged efficiently while maintaining the order of intervals. It optimizes the insertion process with a time complexity of O(n), where n is the number of intervals in the input.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n+m)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of intervals
$m$ : number of merged intervals
- Space complexity : $O(n+m)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    static List<int[]> jawab; // Declaring a static List to hold the intervals

    // Method to insert a new interval into a list of intervals
    public int[][] insert(int[][] intervals, int[] newInterval) {
        int n = intervals.length;
        jawab = new ArrayList<>(); // Initializing the List to store the result
        int i = 0;

        // Adding intervals before the newInterval
        while (i < n && intervals[i][1] < newInterval[0]) {
            jawab.add(intervals[i++]);
        }

        // Merging overlapping intervals with the newInterval
        while (i < n && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
            newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
            i++;
        }

        // Adding the merged newInterval
        jawab.add(newInterval);

        // Adding intervals after the newInterval
        while (i < n) {
            jawab.add(intervals[i++]);
        }

        // Converting List to 2D array and returning the result
        return jawab.toArray(new int[jawab.size()][]);
    }
}
```