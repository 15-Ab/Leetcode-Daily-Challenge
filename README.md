# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

### Sorry for past two days as I was offline completely. Now I'll remain regular. Thanks for your pateince.

## Today's 27-02-24 [Problem Link](https://leetcode.com/problems/diameter-of-binary-tree/description/?envType=daily-question&envId=2024-02-27)
## 543. Diameter of Binary Tree

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem is to find the diameter of a binary tree, where the diameter is defined as the length of the longest path between any two nodes in a tree. The path may or may not pass through the root.

# Approach
<!-- Describe your approach to solving the problem. -->
My code defined a `Solution` class with a static variable `maxDiameter` to store the maximum diameter encountered during traversal.

**Diameter Calculation Method (`diameterOfBinaryTree`) :**
   - This method is the entry point for calculating the diameter of the binary tree.
   - It resetted the `maxDiameter` variable to 0 before each calculation.
   - Called the `calculateMaxDepth` method to perform the traversal and update the `maxDiameter`.
   - Returned the final calculated diameter.

**Depth Calculation Method (`calculateMaxDepth`) :**
   - This method recursively calculated the maximum depth of the binary tree.
   - Base Case : If the current node is null, return 0.
   - Recursively calculated the maximum depth of the left and right subtrees.
   - Updated `maxDiameter` if the sum of left and right depths is greater than the current `maxDiameter`.
   - Returned the current node's depth (1 plus the maximum of left and right depths).

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of nodes in the binary tree
- Space complexity : $O(h)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$h$ : height of the binary tree

# Code
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */

// Solution class for calculating the diameter of a binary tree.
class Solution {
    
    // Static variable to store the maximum diameter.
    static int maxDiameter = 0;

    /**
     * Calculates the diameter of the binary tree.
     *
     * @param root The root of the binary tree.
     * @return The diameter of the binary tree.
     */
    public int diameterOfBinaryTree(TreeNode root) {
        // Resetting the static variable before each calculation.
        maxDiameter = 0;
        calculateMaxDepth(root);
        return maxDiameter;
    }

    /**
     * Calculates the maximum depth of the binary tree.
     *
     * @param node The current node in the binary tree.
     * @return The maximum depth of the binary tree.
     */
    static int calculateMaxDepth(TreeNode node) {
        // Base case: if the node is null, return 0.
        if (node == null) {
            return 0;
        }

        // Recursively calculating the maximum depth of the left and right subtrees.
        int leftDepth = calculateMaxDepth(node.left);
        int rightDepth = calculateMaxDepth(node.right);

        // Updating the maximum diameter if needed.
        maxDiameter = Math.max(maxDiameter, leftDepth + rightDepth);

        // Returning the current node's depth.
        return 1 + Math.max(leftDepth, rightDepth);
    }
}
```