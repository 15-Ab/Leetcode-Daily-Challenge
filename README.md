# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 16-02-24 [Problem Link](https://leetcode.com/problems/least-number-of-unique-integers-after-k-removals/description/?envType=daily-question&envId=2024-02-16)
## 1481. Least Number of Unique Integers after K Removals

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the least number of unique integers in an array after removing 'k' elements.

# Approach
<!-- Describe your approach to solving the problem. -->

- Created a HashMap to store the frequency of each number in the array.

- Populated the HashMap with the frequency of each number.

- Created a Priority Queue (min-heap) with the values (frequencies) from the HashMap.

- Iterated through the Priority Queue and decremented 'k' by the frequency of each element until 'k' becomes zero.

- If 'k' is negative after the loop, it means more elements were removed than necessary. Returned the remaining number of unique integers plus one.

- If 'k' is zero or positive after the loop, returned the remaining number of unique integers.

My code efficiently found the solution by using a HashMap to store frequencies and a Priority Queue to process the frequencies in ascending order.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(N + N*log N + K*log N) {\equiv} O( N *log N )$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of unique elements in the array

$K$ : given
- Space complexity : $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
import java.util.HashMap;
import java.util.PriorityQueue;
import java.util.Queue;

class Solution {

    // HashMap to store the frequency of each number in the array
    HashMap<Integer, Integer> m;
    // Priority Queue to store the frequencies in ascending order
    Queue<Integer> mH;

    // Method to find the least number of unique integers after removing 'k' elements
    public int findLeastNumOfUniqueInts(int[] arr, int k) {
        
        // Initializing the HashMap
        m = new HashMap<>();
        // Populating the HashMap with the frequency of each number in the array
        for (int n : arr) {
            m.put(n, m.getOrDefault(n, 0) + 1);
        }

        // Initializing the Priority Queue with the values (frequencies) from the HashMap
        mH = new PriorityQueue<>(m.values());

        // Continuing removing the smallest frequencies until 'k' becomes zero
        while (k > 0) {
            k -= mH.poll();
        }

        // If 'k' is negative, it means more elements were removed than necessary
        // In this case, returning the remaining number of unique integers plus one
        if (k < 0) {
            return mH.size() + 1;
        } else {
            // If 'k' is zero or positive, returning the remaining number of unique integers
            return mH.size();
        }
    }
}

```