# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 13-04-24 [Problem Link](https://leetcode.com/problems/maximal-rectangle/description/?envType=daily-question&envId=2024-04-13)
## 85. Maximal Rectangle

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem involves finding the maximal rectangle containing only 1s in a binary matrix. To solve this problem efficiently, I can utilize the concept of histograms. For each row in the matrix, I can treat it as the base of a histogram and calculate the height of bars in the histogram based on the consecutive 1s in that row. Then, I can apply the largest rectangle in histogram algorithm to find the maximal rectangle for each row. Finally, I return the maximum area among all rows as the result.

# Approach
<!-- Describe your approach to solving the problem. -->

- I initialized a variable to store the maximal rectangle area.
- Iterate through each row in the matrix:
    - Update the histogram of heights for each row. Treat 1s as bars and consecutive 1s as increasing heights in the histogram.
    - Calculate the maximal rectangle area using the largest rectangle in histogram algorithm for the current histogram.
    - Update the maximal rectangle area if the current area is greater.
- Return the maximal rectangle area as the result.

##### Largest Rectangle in Histogram Algorithm :
- I nitialized a stack to store the indices of histogram bars.
- Iterated through each bar in the histogram:
    - If the stack is empty or the current bar's height is greater than or equal to the height of the bar at the top of the stack, push the index of the current bar onto the stack.
    - If the current bar's height is less than the height of the bar at the top of the stack, keep popping bars from the stack until the stack is empty or the height of the bar at the top of the stack is less than the current bar's height. For each popped bar, calculate its area using the popped height as the height of the rectangle and the difference between the current index and the index of the bar at the top of the stack as the width of the rectangle. Update the maximal rectangle area if the calculated area is greater.
- After iterating through all bars, if there are bars left in the stack, repeat step 2 for each remaining bar.
- Returned the maximal rectangle area calculated.

--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(m*n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ : number of rows
$n$ : number of columns
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
  def maximalRectangle(self, matrix: List[List[str]]) -> int:
    if not matrix:
      return 0

    ans = 0
    hist = [0] * len(matrix[0])

    def largestRectangleArea(heights: List[int]) -> int:
      ans = 0
      stack = []

      for i in range(len(heights) + 1):
        while stack and (i == len(heights) or heights[stack[-1]] > heights[i]):
          h = heights[stack.pop()]
          w = i - stack[-1] - 1 if stack else i
          ans = max(ans, h * w)
        stack.append(i)

      return ans

    for row in matrix:
      for i, num in enumerate(row):
        hist[i] = 0 if num == '0' else hist[i] + 1
      ans = max(ans, largestRectangleArea(hist))

    return ans
```