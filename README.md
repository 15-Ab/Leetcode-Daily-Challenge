# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 12-01-24 [Problem Link](https://leetcode.com/problems/determine-if-string-halves-are-alike/description/)
## 1704. Determine if String Halves Are Alike

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code checks whether the two halves of a given string have an equal number of vowels. The comparison is case-insensitive, and the goal is to determine if the two halves are alike in terms of the number of vowels.


# Approach
<!-- Describe your approach to solving the problem. -->

**Converted to Lowercase:**
   - I Convert the input string `s` to lowercase for case-insensitive comparison.

**Initialize Vowel Counter:**
   - I initialized a counter variable `vowel` to keep track of the number of vowels.

**Check First Half:**
   - Iterated through the first half of the string (`s.length() / 2`).
   - If the current character is a vowel ('a', 'e', 'i', 'o', 'u'), incremented the `vowel` counter.

**Check Second Half:**
   - Iterated through the second half of the string (`s.length() / 2` to `s.length()`).
   - If the current character is a vowel, decremented the `vowel` counter.

**Check if Halves Are Alike:**
   - If the `vowel` counter is zero after both iterations, return `true`, indicating that the two halves have an equal number of vowels.
---
Have a look at the code , still have any confusion then please let me know in the comments Keep Solving.:)

# Complexity
- Time complexity : $O(c)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
 $c$ : number of characters in array
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public boolean halvesAreAlike(String s) {
        // Converted the string to lowercase (Note: Strings in Java are immutable)
        s = s.toLowerCase();

        // Initialized a counter for vowels
        int vowel = 0;

        // Checked the first half of the string
        for (int i = 0; i < s.length() / 2; i++) {
            // If the current character is a vowel, incremented the vowel counter
            if (s.charAt(i) == 'a' || s.charAt(i) == 'e' || s.charAt(i) == 'i' || s.charAt(i) == 'o' || s.charAt(i) == 'u') {
                vowel++;
            }
        }

        // Checked the second half of the string
        for (int i = s.length() / 2; i < s.length(); i++) {
            // If the current character is a vowel, decremented the vowel counter
            if (s.charAt(i) == 'a' || s.charAt(i) == 'e' || s.charAt(i) == 'i' || s.charAt(i) == 'o' || s.charAt(i) == 'u') {
                vowel--;
            }
        }

        // If the vowel counter is 0, the two halves are alike; otherwise, they are not alike
        return vowel == 0;
    }
}

```