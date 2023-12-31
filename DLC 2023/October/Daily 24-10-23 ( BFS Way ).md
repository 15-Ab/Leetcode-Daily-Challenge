# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Using BFS.
[I have solved it using DFS also.](https://leetcode.com/problems/find-largest-value-in-each-tree-row/solutions/4201938/daily-24-10-23-dfs/)

# Approach
<!-- Describe your approach to solving the problem. -->
Simply doing row-wise traversal while checking max of each row.
        
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $$O(t)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(t)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$t$$ is the total nodes.

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
    public List<Integer> largestValues(TreeNode root) {

        if( root == null){
            return new ArrayList<>();
        }
        ArrayList<Integer> l = new ArrayList<>();
        Queue<TreeNode> q = new ArrayDeque<>(Arrays.asList(root));

        // Simply doing row-wise traversal : checking max of each row
        
        while( !q.isEmpty()){
            int m = Integer.MIN_VALUE;
            for( int i = q.size(); i > 0; i--){
                TreeNode p = q.poll();
                m = Math.max(m, p.val);
                if( p.left != null){
                    q.offer(p.left);
                }
                if( p.right != null){
                    q.offer(p.right);
                }
            }
            l.add(m);
        }
        return l;
    }
}
```