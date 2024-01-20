# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 20-01-24 [Problem Link](https://leetcode.com/problems/sum-of-subarray-minimums/description/?envType=daily-question&envId=2024-01-20)
## 907. Sum of Subarray Minimums


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to find the sum of minimums for all subarrays of the given array. To achieve this, I used two stacks to keep track of elements to the left (`l`) and right (`r`) of each element, and two arrays (`baya` and `daya`) to store the count of elements to the left and right, respectively.

# Approach
<!-- Describe your approach to solving the problem. -->
**My initialized Stacks and Arrays :**
- Created two stacks (`l` and `r`) to keep track of indices for elements to the left and right.
- Initialized two arrays (`baya` and `daya`) to store the count of elements to the left and right, respectively.


**Process Elements to the Left (`l` Stack) :**
- Iterated through the array from left to right.
- Used the stack `l` to keep track of indices of elements encountered.
- For each element, popped elements from the stack until finding an element greater than the current one.
- Updated the `baya` array with the count of elements to the left.

**Process Elements to the Right (`r` Stack) :**
- Iterated through the array from right to left.
- Used the stack `r` to keep track of indices of elements encountered.
- For each element, popped elements from the stack until finding an element greater than or equal to the current one.
- Updated the `daya` array with the count of elements to the right.

**Calculated Sum of Minimums :**
- I iterated through the array.
- For each element, calculated the product of counts from `baya`, `daya`, and the element itself.
- Accumulated the products to obtain the sum of minimums.

**Applied Modulo Operation :**
- To avoid integer overflow, applied the modulo operation (1,000,000,007) to the sum.

**Returned the Result :**
Returned the final sum of minimums after the modulo operation.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(l)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$l$ : length of the input array
- Space complexity : $O(l)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public int sumSubarrayMins(int[] arr) {
        
        // Arrays to store the count of subarrays where the current element is the minimum
        long[] baya = new long[arr.length]; // Count of elements to the left
        long[] daya = new long[arr.length]; // Count of elements to the right

        // Stacks to keep track of indices for elements to the left and right
        Stack<Integer> l = new Stack<>();
        Stack<Integer> r = new Stack<>();

        // Processing elements to the left
        for (int i = 0; i < arr.length; i++) {
            // Popping elements from the stack until finding a greater element
            while (!l.isEmpty() && arr[i] < arr[l.peek()]) {
                l.pop();
            }
            
            baya[i] = i + 1; // Default count is the distance to the leftmost element

            if (!l.isEmpty()) {
                baya[i] = i - l.peek(); // Updating count based on the position of the greater element
            }
            
            l.push(i); // Pushing the current index to the stack
        }

        // Processing elements to the right
        for (int i = arr.length - 1; i >= 0; i--) {
            // Popping elements from the stack until finding a greater or equal element
            while (!r.isEmpty() && arr[i] <= arr[r.peek()]) {
                r.pop();
            }
            
            daya[i] = arr.length - i; // Default count is the distance to the rightmost element

            if (!r.isEmpty()) {
                daya[i] = r.peek() - i; // Updating count based on the position of the greater or equal element
            }
            
            r.push(i); // Pushing the current index to the stack
        }

        // Calculating the sum of subarrays' minimums using the counts and the modulo
        long minSum = 0;
        for (int i = 0; i < arr.length; i++) {
            minSum = ( minSum + (baya[i] * arr[i] * daya[i]) % 1_000_000_007 ) % 1_000_000_007 ;
        }
        
        return (int) minSum  ; // Return the result after taking the modulo
    }
}

```
