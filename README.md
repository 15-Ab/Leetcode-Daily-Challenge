# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 06-03-24 [Problem Link](https://leetcode.com/problems/linked-list-cycle/description/?envType=daily-question&envId=2024-03-06)
## 141. Linked List Cycle

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to determine whether a given linked list has a cycle or not. A cycle in a linked list occurs when a node points to a previously visited node, creating a loop in the structure.

# Approach
<!-- Describe your approach to solving the problem. -->
**Edge Case Check :**
   - Checked if the given linked list is empty (head is null). If it is, returned `false` as there can't be a cycle in an empty list.

**HashSet for Visited Nodes :**
   - Initialized a HashSet (`visitedNodes`) to keep track of visited nodes.
   - Added the head of the linked list to the HashSet.

**Traverse the Linked List:**
   - Used a while loop to traverse the linked list.
   - At each step, checked if the next node is already present in the HashSet. If it is, there is a cycle, so return `true`.
   - If the next node is not in the HashSet, added it to the HashSet.
   - Moved to the next node in the linked list.

**Result :**
   - If the loop completes without finding a cycle, returned `false`.

My approach utilized a HashSet to efficiently detect cycles in a linked list.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of nodes in the linked list
- Space complexity : $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */

public class Solution {
    
    // Function to check if a linked list has a cycle
    public boolean hasCycle(ListNode head) {
        
        // Checking if the head is null (empty list)
        if (head == null) {
            return false;
        }
        
        // HashSet to store visited nodes
        HashSet<ListNode> visitedNodes = new HashSet<>();
        
        // Adding the head to the HashSet
        visitedNodes.add(head);

        // Looping through the linked list
        while (head != null) {
            
            // Checking if the next node is already in the HashSet (indicating a cycle)
            if (visitedNodes.contains(head.next)) {
                return true;
            }
            
            // Adding the next node to the HashSet
            visitedNodes.add(head.next);
            
            // Moving to the next node in the linked list
            head = head.next;
        }
        
        // If the loop completes without finding a cycle, returning false
        return false;
    }
}
```