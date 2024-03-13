# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 13-03-24 [Problem Link](https://leetcode.com/problems/find-the-pivot-integer/description/?envType=daily-question&envId=2024-03-13)
## 2485. Find the Pivot Integer

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of the `pivotInteger` function is to find a pivot integer 'x' for a given integer 'n', where the sum of integers from 1 to 'x' is equal to the sum of integers from 'x + 1' to 'n'.

# Approach
<!-- Describe your approach to solving the problem. -->
The derivation involves solving a quadratic equation based on the summation of arithmetic series. The key steps are as follows:

**Summation Equation** : $1 + 2 + ... + x = x + ... + n$

**Quadratic Equation** : $(1 + x) \times \frac{x}{2} = (x + n) \times \frac{n - x + 1}{2}$

**Simplify and Solved** : Manipulated the equation to get $2 * x^2 = n^2 + n$ and solved for 'x'.

**Calculated and Checked** : Calculated 'y' as $\frac{n^2 + n}{2}$ and find the square root 'x'. Checked if $x^2$ equals 'y'.

**Result** : Returned 'x' if it's a perfect square; otherwise, return -1.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  public int pivotInteger(int n) {

    /* Sum of the series: 1 + 2 + ... + x = x + ... + n
     Equation derivation :
     (1 + x) * x / 2 = (x + n) * (n - x + 1) / 2
     Simplifying  :
     x + x^2 = nx - x^2 + x + n^2 - nx + n
     2 * x^2 = n^2 + n
     Solving for x:
     x = sqrt((n^2 + n) / 2)
    */
    
    // Calculating values and checking for a perfect square
    final int y = (n * n + n) / 2;
    final int x = (int) Math.sqrt(y);
    
    // Returning result based on perfect square condition
    return x * x == y ? x : -1;
  }
}
```