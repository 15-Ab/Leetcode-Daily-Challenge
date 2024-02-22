# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 22+02=24 [Problem Link](https://leetcode.com/problems/find-the-town-judge/description/?envType=daily-question&envId=2024-02-22)
## 997. Find the Town Judge

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem aims to find the judge in a town based on trust relationships between the people. The judge is someone who is trusted by everyone else but does not trust anyone.

# Approach
<!-- Describe your approach to solving the problem. -->

**Initialized the Trust Counts Array :** Created an array to store the trust counts for each person. The array `a` will have a size of `n+1` to accommodate indices from 1 to n.

**Updated the Trust Counts :** Iterated through the trust array and updated the trust counts in the array. Decreased the count for the person making the trust (outgoing trust) and increased the count for the person receiving the trust (incoming trust).

**Found the Judge :** Iterated through the people (from 1 to n) and checked if a person has incoming trusts equal to (n - 1). If found, that person is considered the judge since the judge is trusted by everyone else and does not trust anyone.

**Result :** If a judge is found, returned the person's index. If no judge is found, returned -1.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)

# Complexity
- Time complexity :  $O(N+E)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of people

$E$ : number of trust relationships
- Space complexity : $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Creating a static array to store the trust counts for each person.
    static int[] a;

    // Method to find the judge
    public int findJudge(int n, int[][] trust) {
        
        // Initializing the array to store trust counts
        a = new int[n + 1];

        // Iterating through the trust array and update the trust counts in the array
        for (int[] t : trust) {
            // Decreasing the count for the person making the trust (outgoing trust)
            a[t[0]]--;
            // Increasing the count for the person receiving the trust (incoming trust)
            a[t[1]]++;
        }

        // Iterating through the people (1 to n) to find the judge
        for (int i = 1; i <= n; i++) {
            // If a person has incoming trusts equal to (n - 1), they are considered as the judge
            if (a[i] == n - 1) {
                return i;
            }
        }

        // If no judge is found, returning -1
        return -1;
    }
}
```