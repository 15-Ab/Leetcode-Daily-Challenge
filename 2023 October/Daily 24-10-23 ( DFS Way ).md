# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Using DFS. 
 [I have solved it using BFS also.](https://leetcode.com/problems/find-largest-value-in-each-tree-row/solutions/4201876/daily-24-10-23/)

# Approach
<!-- Describe your approach to solving the problem. -->
Applying DFS way
- While going in depth, we will add the first leftmost element of each level as max of that depth level
- - other elements of that level will be traversed we will update the max value (if required) of that depth level.
- At each level of depth there will be one element which will be max at that level
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O(t)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$t$$ : total nodes.
- Space complexity : $$O(h)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

$$h$$ : height of tree.

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
    // Applying DFS way
    // While going in depth, we will add the first leftmost element of each level as max of that depth level, and other elements of that level will be traversed we will update the max value (if required) of that depth level.
    // At each level of depth there will be one element which will be max at that level

    public List<Integer> largestValues(TreeNode root) {
        ArrayList<Integer> l = new ArrayList<>();
        DFS( 0, l, root);
        return l;
    }

    void DFS( int depth, ArrayList<Integer> l, TreeNode root){
        if( root == null){
            return;
        }
        
        // I am adding the first(leftmost) element of each level
        // initialise max of that level by first element
        if( depth + 1 > l.size()){
            l.add(root.val);
        }
        // else if other elements are traversed : then simply update the max value of that depth level
        else{
            l.set(depth, Math.max(l.get(depth), root.val) );
        }

        DFS(depth+1, l, root.left);
        DFS(depth+1, l, root.right);
    }
}
```