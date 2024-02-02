# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 02-02-24 [Problem Link](https://leetcode.com/problems/sequential-digits/description/?envType=daily-question&envId=2024-02-02)
## 1291. Sequential Digits

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to efficiently find all sequential digits within a given range (low to high).
A sequential digit is a number where each digit is one more than the previous digit.


# Approach
<!-- Describe your approach to solving the problem. -->
- Created a string 'digits' containing all the digits from 1 to 9 in order.
- Converted 'low' and 'high' to strings to get their lengths.
- Iterated through possible lengths, from 'lowLength' to 'highLength'.
  - For each length, iterated through 'digits' to find the starting digit for the current length.
  - Extracted a substring of the current length from 'digits'.
  - Converted the substring to an integer.
  - Checked if the integer is within the given range ('low' to 'high').
  - If yes, added it to the result list.
- Finally, returned the list of sequential numbers as the output.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $O(81)$ $\approx$ $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(9)$ $\approx$ $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> sequentialDigits(int low, int high) {
        ArrayList<Integer> jawab = new ArrayList<>();
        String digits = "123456789";

        // Converting low and high to strings to get their lengths
        int lowLength = String.valueOf(low).length();
        int highLength = String.valueOf(high).length();

        // Iterating through possible lengths
        for (int length = lowLength; length <= highLength; length++) {
            // Iterating through the digits string
            for (int start = 0; start + length <= 9; start++) {
                // Extracting the substring of the current length
                String substring = digits.substring(start, start + length);

                // Converting the substring to an integer
                int num = Integer.parseInt(substring);

                // Checking if the number is within the given range
                if (num >= low && num <= high) {
                    // If yes, then adding it to the result list
                    jawab.add(num);
                }
            }
        }
         // Returning the final answer list
        return jawab;
    }
}
```
