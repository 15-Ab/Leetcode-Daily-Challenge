# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 07-02-24 [Problem Link](https://leetcode.com/problems/sort-characters-by-frequency/description/?envType=daily-question&envId=2024-02-07)
## 451. Sort Characters By Frequency

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The intuition behind my code is to sort the characters in a given string based on their frequency. To achieve this, I utilized a HashMap to store the frequency of each character in the input string. The maximum frequency is tracked to later iterate through frequencies and build the final answer string.

# Approach
<!-- Describe your approach to solving the problem. -->
**Constructed Frequency Map :**
- A HashMap (`m`) is initialized to store the frequency of each character.
- The input string is iterated, and for each character, its frequency in the map is updated.
- The maximum frequency (`max`) is maintained to determine the order of frequencies in the final result.

**Sorted by Frequency :**
- Initialized an empty string (`jawab`) to store the final result.
- Iterated through frequencies in descending order (from the maximum frequency to 1).
- For each frequency, iterated through characters in the frequency map.
- Appended each character to the answer string the number of times equal to its frequency.

**Returned the Result :**
- The final answer string is returned.

My approach ensured that the characters in the result string are sorted based on their frequency, with characters having higher frequencies appearing first.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $ O(max * u)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$max$ : maximum frequency

$u$ : number of unique characters in the input string
- Space complexity : $O(u)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Static variables to store character frequency map, maximum frequency, and the final answer
    static HashMap<Character, Integer> m;
    static int max;
    static String jawab;

    // Method to sort characters in a string based on their frequency
    public String frequencySort(String s) {

        // Initializing the character frequency map and maximum frequency
        m = new HashMap<>();
        max = 0;

        // Populating the character frequency map and update the maximum frequency
        for (char c : s.toCharArray()) {
            m.put(c, m.getOrDefault(c, 0) + 1);
            max = Math.max(max, m.get(c));
        }

        // Initializing the final answer string
        jawab = "";

        // Iterating over frequencies in descending order
        for (int i = max; i > 0; i--) {

            // Iterating over characters in the frequency map
            for (char c : m.keySet()) {

                // Appending the character to the answer string for its corresponding frequency
                if (m.get(c) == i) {
                    for (int d = 0; d < i; d++) {
                        jawab += c;
                    }
                }
            }
        }

        // Returning the final answer string
        return jawab;
    }
}

```