# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 09-01-24 [Problem Link](https://leetcode.com/problems/leaf-similar-trees/description/?submissionId=1141098031)
## 872. Leaf-Similar Trees


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The leaf sequence of a tree refers to the sequence of values encountered when performing a depth-first traversal and reaching a leaf node. My intuition is to compare the leaf sequences of both trees to check if they are identical.

# Approach
<!-- Describe your approach to solving the problem. -->
- Leaf Sequence Extraction :
- - My code defines two static lists (t1 and t2) to store the leaf values of the two trees.
- - Two helper methods (leaf1 and leaf2) are implemented to perform a depth-first traversal of each tree and populate the corresponding leaf lists.
- Leaf Traversal :
- - The 'leaf1' method traverses 'root1', identifies leaf nodes, and adds their values to the list 't1'.
- - Similarly, the 'leaf2' method traverses 'root2', identifies leaf nodes, and adds their values to the list 't2'.
- Comparison :
- - After both leaf lists are populated, the code compares the sizes of 't1' and 't2'.
- - If the sizes are different, the leaf sequences cannot be similar, and the code returns false.
- - If the sizes are the same, the code proceeds to compare each element of t1 with the corresponding element in t2.
- - If any pair of corresponding elements is not equal, the leaf sequences are not similar, and the code returns false.
- Result :
- - If the sizes and elements of t1 and t2 are equal, the leaf sequences are considered similar, and the code returns true.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)


# Complexity
- Time complexity : $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$n$$ : number of nodes

- Space complexity : $$O(n + r)$$
$$r = max(h1, h2) $$ ( since recursion stack is used for DFS trversal )
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$h1$$ : height of tree 1 
$$h2$$ : height of tree 2 

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
class Solution {
    // Static lists to store the leaf values of the two trees
    static List<Integer> t1;
    static List<Integer> t2;

    // Main method to check if the leaf sequences of two trees are similar
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        // Initialize the static lists to store leaf values
        t1 = new ArrayList<>();
        t2 = new ArrayList<>();

        // Populate t1 with leaf values of root1
        leaf1(root1);

        // Populate t2 with leaf values of root2
        leaf2(root2);

        // Compare the sizes of the two lists
        if (t1.size() != t2.size()) {
            return false;
        }

        // Compare each element of the two lists
        for (int i = 0; i < t1.size(); i++) {
            if (t1.get(i) != t2.get(i)) {
                return false;
            }
        }

        // If sizes and elements are equal, the leaf sequences are similar
        return true;
    }

    // Helper method to populate t1 with leaf values of a tree
    static void leaf1(TreeNode t) {
        // Base case: if the current node is null, return
        if (t == null) {
            return;
        }

        // If the current node is a leaf, add its value to t1
        if (t.left == null && t.right == null) {
            t1.add(t.val);
        }

        // Recursively call leaf1 on the left and right subtrees
        leaf1(t.left);
        leaf1(t.right);
    }

    // Helper method to populate t2 with leaf values of a tree
    static void leaf2(TreeNode t) {
        // Base case: if the current node is null, return
        if (t == null) {
            return;
        }

        // If the current node is a leaf, add its value to t2
        if (t.left == null && t.right == null) {
            t2.add(t.val);
        }

        // Recursively call leaf2 on the left and right subtrees
        leaf2(t.left);
        leaf2(t.right);
    }
}

```
