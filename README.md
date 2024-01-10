# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 10-01-24 [Problem Link](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/description/)
## 2385. Amount of Time for Binary Tree to Be Infected


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code aims to calculate the amount of time it takes to visit all unique nodes in a tree, starting from a specified node. It uses Breadth-First Search (BFS) for traversing the tree and employs a visualization process to represent the tree as an adjacency list.

# Approach
<!-- Describe your approach to solving the problem. -->
**Visualization:**
   - The `visualisation` method performs a BFS traversal of the tree, creating an adjacency list representation of the tree. It uses a `HashMap` named `visual` where each node is mapped to its neighbors.

**BFS Traversal for Time Calculation:**
   - The `amountOfTime` method uses BFS to traverse the tree starting from the specified node (`start`).
   - It initializes a queue (`q`) with the starting node and a set (`dekhahua`) to keep track of visited nodes.
   - The variable `jawab` is used to store the result, initialized to -1.
   - In each iteration, the code explores the neighbors of the current node, marking them as visited and enqueuing them for further exploration.
   - The loop continues until all nodes are visited, and `jawab` is incremented at each level of the BFS traversal.

**Result:**
   - The final result is the value of `jawab`, representing the amount of time needed to visit all unique nodes in the tree starting from the specified node.


# Complexity
- Time complexity : $O(V+E)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(V+E)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$V$ : number of vertices

$E$ : number of edges

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
    // HashMap to store the visualization of the tree
    static HashMap<Integer, ArrayList<Integer>> visual;

    public int amountOfTime(TreeNode root, int start) {
        // Generated the visualization of the tree
        visualisation(root);

        // Queue for BFS traversal starting from the specified node
        Queue<Integer> q = new ArrayDeque<>(Arrays.asList(start));

        // HashSet to keep track of visited nodes
        HashSet<Integer> dekhahua = new HashSet<>(Arrays.asList(start));

        // Variable to store the result
        int jawab = -1;

        // Performed BFS traversal
        while(!q.isEmpty()) {
            for (int s = q.size(); s > 0; s--) {
                int t = q.poll();
                // Skip if the node is not in the visualization
                if (!visual.containsKey(t)) {
                    continue;
                }
                // Enqueued neighbors of the current node
                for (int n : visual.get(t)) {
                    if (dekhahua.contains(n)) {
                        continue; // Skip if the neighbor is already visited
                    }
                    dekhahua.add(n);
                    q.offer(n);
                }
            }
            jawab++;
        }
        return jawab;
    }

    // Method to generate the visualization of the tree
    void visualisation(TreeNode root) {
        // Queue for BFS traversal
        Queue<Pair<TreeNode, Integer>> q = new ArrayDeque<>(Arrays.asList(new Pair<>(root, -1)));

        // Initialized the HashMap
        visual = new HashMap<>();

        // Performed BFS traversal to generate the visualization
        while (!q.isEmpty()) {
            Pair<TreeNode, Integer> jora = q.poll();
            TreeNode n = jora.getKey();
            int p = jora.getValue();
            if (p != -1) {
                // Add edges to the visualization
                visual.putIfAbsent(p, new ArrayList<>());
                visual.putIfAbsent(n.val, new ArrayList<>());
                visual.get(p).add(n.val);
                visual.get(n.val).add(p);
            }
            // Enqueued left and right children for further exploration
            if (n.right != null) {
                q.add(new Pair<>(n.right, n.val));
            }
            if (n.left != null) {
                q.add(new Pair<>(n.left, n.val));
            }
        }
    }
}

```
