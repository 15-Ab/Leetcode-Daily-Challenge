# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 19-01-24 [Problem Link](https://leetcode.com/problems/minimum-falling-path-sum/description/?envType=daily-question&envId=2024-01-19)
## 931. Minimum Falling Path Sum


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My idea is to start from the second last row of the matrix and iteratively calculate the minimum falling path sum for each element. We update each element by adding the minimum value among its three neighboring elements from the next row (bottom, bottom-left, and bottom-right).

Finally, I found the minimum value in the first row, which represents the minimum falling path sum for the entire matrix.

# Approach
<!-- Describe your approach to solving the problem. -->
- Iterated from the second last row (`r = rows - 2`) to the first row (`r >= 0`).
- For each element in the current row (`matrix[r][c]`), calculated the minimum falling path sum by considering the three neighboring elements from the next row (bottom, bottom-left, and bottom-right).
- Updated the current element with the sum of its value and the minimum calculated in the previous step.
- After completing the iteration, found the minimum value in the first row, which represents the minimum falling path sum for the entire matrix.
- Returned the minimum falling path sum found in previous step.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(r*c)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$r$ : rows

$c$ : columns

- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```

class Solution {
    public int minFallingPathSum(int[][] matrix) {
        // Getting the number of rows and columns in the matrix
        int rows = matrix.length;
        int cols = matrix[0].length;

        // Iterating from the second last row to the first row
        for (int r = rows - 2; r >= 0; r--) {
            // Iterating through each element in the row
            for (int c = 0; c < cols; c++) {
                int min = Integer.MAX_VALUE;

                // Checking the bottom-left element (if available)
                if (c > 0) {
                    min = Math.min(min, matrix[r + 1][c - 1]);
                }

                // Checking the bottom element
                int bottom = matrix[r + 1][c];
                min = Math.min(min, bottom);

                // Checking the bottom-right element (if available)
                if (c < cols - 1) {
                    min = Math.min(min, matrix[r + 1][c + 1]);
                }

                // Updating the current element with the sum of its value and the minimum of the three neighbors
                matrix[r][c] = matrix[r][c] + min;
            }
        }

        // Finding the minimum value in the first row, which represents the minimum falling path sum
        int minimum = Integer.MAX_VALUE;
        for (int i = 0; i < cols; i++) {
            minimum = Math.min(minimum, matrix[0][i]);
        }

        return minimum;
    }
}
```
