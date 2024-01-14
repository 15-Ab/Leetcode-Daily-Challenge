# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 14-01-24 [Problem Link](https://leetcode.com/problems/determine-if-two-strings-are-close/description/?envType=daily-question&envId=2024-01-14)
## 1657. Determine if Two Strings Are Close


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
As the goal of this code is to determine if two strings are "close." Two strings are considered "close" if they have the same set of characters and the frequency of each character is the same in both strings.

# Approach
<!-- Describe your approach to solving the problem. -->
-  Checked if the lengths of both input strings (`word1` and `word2`) are equal. If not, return `false` since strings of different lengths cannot be "close."

- Created two HashMaps (`m1` and `m2`) to store the frequency of each character in `word1` and `word2` respectively.

- Iterated through each character in `word1` and update the frequency in `m1`.

- Iterated through each character in `word2` and update the frequency in `m2`.

- Checked if the sets of characters in both HashMaps are equal. If not, return `false` since the characters must be the same for the strings to be "close."

- Extracted the frequency lists from both HashMaps and sort them.

- Checked if the sorted frequency lists are equal. If they are, return `true`; otherwise, return `false`.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(nlogn)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : size of array 
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public boolean closeStrings(String word1, String word2) {
        // Checked if the lengths of the two words are different, they cannot be "close."
        if (word1.length() != word2.length()) {
            return false;
        }

        // HashMaps to store character frequencies for each word.
        HashMap<Character, Integer> m1 = new HashMap<>();
        HashMap<Character, Integer> m2 = new HashMap<>();

        // Counted character frequencies in word1.
        for (char ch : word1.toCharArray()) {
            m1.merge(ch, 1, Integer::sum);
        }

        // Counted character frequencies in word2.
        for (char ch : word2.toCharArray()) {
            m2.merge(ch, 1, Integer::sum);
        }

        // Checked if the sets of characters are the same in both words.
        if (!m1.keySet().equals(m2.keySet())) {
            return false;
        }

        // Extracted frequency lists for each word.
        ArrayList<Integer> f1 = new ArrayList<>(m1.values());
        ArrayList<Integer> f2 = new ArrayList<>(m2.values());

        // Sorted frequency lists.
        Collections.sort(f1);
        Collections.sort(f2);

        // Checked if the sorted frequency lists are equal.
        return f1.equals(f2);
    }
}
```