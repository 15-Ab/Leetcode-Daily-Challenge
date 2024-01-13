# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 12-01-24 [Problem Link](https://leetcode.com/problems/minimum-number-of-steps-to-make-two-strings-anagram/description/?envType=daily-question&envId=2024-01-13)
## 1347. Minimum Number of Steps to Make Two Strings Anagram

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
As the goal is to find the minimum number of steps required to make two strings, s and t, anagrams of each other. An anagram is a word or phrase formed by rearranging the letters of another. In this context, it means transforming one string into another by changing the order of its characters.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Created a HashMap (`m`) to store the frequency of characters in string `s`.
2. Iterated through each character in string `s` and update its frequency in the HashMap.
3. Initialized a variable `extra` to track the number of extra characters needed in string `t` to make it an anagram of `s`.
4. Iterated through each character in string `t`:
   - If the character exists in the HashMap and has a positive frequency, decrement its frequency in the HashMap.
   - If the character is not found or has no remaining occurrences in the HashMap, increment the `extra` count.
5. The final value of `extra` represents the minimum number of steps needed to make strings `s` and `t` anagrams.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(l)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$l$ : length of string
- Space complexity : $O(l)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    
    public int minSteps(String s, String t) {
        // Created a HashMap to store the frequency of characters in string s
        HashMap<Character, Integer> m = new HashMap<>();
        
        // Counted the frequency of each character in string s
        for (char c : s.toCharArray()) {
            m.putIfAbsent(c, 0);
            m.put(c, m.getOrDefault(c, 0) + 1);
        }
        
        // Variable to track the extra characters in string t
        int extra = 0;
        
        // Checked characters in string t against the frequency in the HashMap
        for (char c : t.toCharArray()) {
            // If the character exists in the HashMap and has a positive frequency
            if (m.getOrDefault(c, 0) > 0) {
                // Decrease the frequency in the HashMap
                m.put(c, m.get(c) - 1);
            } else {
                // If the character is not found or has no remaining occurrences in the HashMap, increment extra
                extra++;
            }
        }
        
        // Returned the total count of extra characters in string t
        return extra;
    }
}

```