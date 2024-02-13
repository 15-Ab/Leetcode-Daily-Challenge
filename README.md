# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 13-02-24 [Problem Link](https://leetcode.com/problems/find-first-palindromic-string-in-the-array/description/?envType=daily-question&envId=2024-02-13)
## 2108. Find First Palindromic String in the Array

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of this problem is to find the first palindrome in an array of words. A palindrome is a string that reads the same forward and backward (ignoring spaces, punctuation, and capitalization). 

My intuition was to iterate through each word in the array and check if it is a palindrome using a helper method.

# Approach
<!-- Describe your approach to solving the problem. -->
- Method ``firstPalindrome` :
  - This method took an array of words as input.
  - It iterated through each word in the array using a for-each loop.
  - For each word, it called the `isPalin` method to check if the word is a palindrome.
  - If a palindrome is found, the method immediately returned that word.
  - If no palindrome is found in the entire array, it returned an empty string.

- Method `isPalin` :
  - This static method checked if a given string is a palindrome.
  - It initialized two pointers (`l` and `r`) at the beginning and end of the string, respectively.
  - It iterated while `l` is less than `r`.
  - Within the loop, it compared characters at positions `l` and `r`.
  - If the characters are not equal, the string is not a palindrome, and the method returned `false`.
  - If the characters are equal, it incremented `l` and decremented `r` to check the next pair of characters.
  - If the loop completed without returning `false`, the string is a palindrome, and the method `returned` true.


Overall, my approach involved iterating through the array of words and checking each word for palindromic properties using the `isPalin` method. The first palindrome encountered is returned, or an empty string is returned if no palindrome is found in the array.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(N*M)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of words

$M$ : maximum length of a word
- Space complexity : $o(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    // This method finds the first palindrome in the given array of words
    public String firstPalindrome(String[] words) {
        
        // Iterating through each word in the array
        for (String s : words) {
            // Checking if the current word is a palindrome using the isPalin method
            if (isPalin(s)) {
                // If it is a palindrome, returning the word
                return s;
            }
        }
        // If no palindrome is found, returning an empty string
        return "";
    }

    // This method checks if the given string is a palindrome
    static boolean isPalin(String s) {
        // Initializing two pointers, one at the beginning and one at the end of the string
        int l = 0;
        int r = s.length() - 1;

        // Continuing checking characters from both ends towards the center
        while (l < r) {
            // If characters at the current positions are not equal, the string is not a palindrome
            if (s.charAt(l) != s.charAt(r)) {
                return false;
            }
            // Moving the pointers towards the center
            l++;
            r--;
        }
        // If the loop completes, the string is a palindrome
        return true;
    }
}
```