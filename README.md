# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 03-04-24 [Problem Link](https://leetcode.com/problems/word-search/description/?envType=daily-question&envId=2024-04-03)
## 79. Word Search

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
I should utiliz Depth-First Search (DFS) to systematically explore the board, aiming to find the given word by traversing adjacent cells.

# Approach
<!-- Describe your approach to solving the problem. -->

**Main Method (exist) :**
- Iterated through each cell on the board.
- Initiated DFS exploration from each cell to search for the word.
- Returned true if the word is found, otherwise false.

**DFS Method (explore) :**
- Checked if the current cell is within bounds.
- Verified if the character at the current cell matches the word's character.
- Recursively explored adjacent cells to find the next character of the word.
- Marked visited cells to avoid revisiting and backtrack when necessary.
- If the entire word is found, returned true; otherwise, returned false.
     
--- 
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $ O(m \times n \times 4^l) $
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ : number of rows
$n$ : number of columns
$l$ : length of the word
- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
  // Main method to check if the word exists on the board
  public boolean exist(char[][] board, String word) {
    for (int row = 0; row < board.length; ++row){
      for (int col = 0; col < board[0].length; ++col){
        if (explore(board, word, row, col, 0)){
          return true;
        }
      }
    }
    return false;
  }

  // DFS method to explore the board and search for the word
  private boolean explore(char[][] board, String word, int row, int col, int index) {
    // Check if the current cell is out of bounds
    if (row < 0 || row == board.length || col < 0 || col == board[0].length){
      return false;
    }
    
    // Checking if the current cell matches the character of the word
    if (board[row][col] != word.charAt(index) || board[row][col] == '*'){
      return false;
    }
    
    // Checking if the entire word has been found
    if (index == word.length() - 1){
      return true;
    }

    // Temporarily marking the current cell as visited
    final char temp = board[row][col];
    board[row][col] = '*';

    // Recursively exploring adjacent cells to find the next character of the word
    final boolean isFound = explore(board, word, row + 1, col, index + 1) || 
                            explore(board, word, row - 1, col, index + 1) || 
                            explore(board, word, row, col + 1, index + 1) || 
                            explore(board, word, row, col - 1, index + 1);
    
    // Backtrack by restoring the original value of the current cell
    board[row][col] = temp;

    return isFound;
  }
}
```