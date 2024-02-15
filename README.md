# बसंत पंचमी की हार्दिक शुभकामनाएं।
# I'm bowing to the goddess of knowledge without whom I'm nothing.
# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

<<<<<<< Updated upstream
## Today's 14-02-24 [Problem Link](https://leetcode.com/problems/rearrange-array-elements-by-sign/description/)
## 2149. Rearrange Array Elements by Sign

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Separated the positive and negative, then update original.

# Approach
<!-- Describe your approach to solving the problem. -->
- I stored the positive and negative in separate arrays in order of there occurence.

- Then simply updated the original 'nums' array by updating alternately with positive and negative numbers.
=======
## Today's 15-02-24 [Problem Link](https://leetcode.com/problems/find-polygon-with-the-largest-perimeter/description/?envType=daily-question&envId=2024-02-15)
## 2971. Find Polygon With the Largest Perimeter

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The problem required finding the largest perimeter of a triangle from an array of integers. The perimeter of a triangle is the sum of its three sides. To maximize the perimeter, I to considered the largest possible combination of three sides from the given array.

# Approach
<!-- Describe your approach to solving the problem. -->
**Sorted the Array** 
- To consider the largest sides, I started by sorting the array in ascending order.

**Cumulative Sums** :
- Created an array (`h`) to store cumulative sums of the sorted elements. The cumulative sum represents the sum of all elements up to the current index.

**Iterated Through the Array** :
- Iterated through the sorted array, starting from the third element, as I need at least three elements to form a triangle. 
- For each element at index `i`, checked if the sum of the two smaller elements (`h[i-1]`) is greater than the current element (`nums[i]`). 
- If true, updated the `perimeter` with the maximum value between the current perimeter and the cumulative sum at index `i`.

**Return Result** :
- If a valid perimeter is found, returned the maximum perimeter; otherwise, returned -1.

My approach ensured that I consider the largest sides to maximize the perimeter of a valid triangle. Sorting the array helped in identifying the larger sides efficiently, and cumulative sums provided a quick way to calculate the sum of elements up to a certain index.
>>>>>>> Stashed changes

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
<<<<<<< Updated upstream
- Time complexity : $O(l)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(2*(l/2))$ = $O(l)$
=======
- Time complexity : $O(n*logn)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of elements in the array.
- Space complexity : $O(n)$
>>>>>>> Stashed changes
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$l$ is the length of array

# Code
```
<<<<<<< Updated upstream
class Solution {
    public int[] rearrangeArray(int[] nums) {

        int p[] = new int[nums.length/2]; // to store positive numbers
        int ip = 0;                       // to maintain current added index 
        int n[] = new int[nums.length/2]; // to store positive numbers
        int in = 0;                       // to maintain current added index 

        for( int i = 0; i < nums.length; i++){
            if( nums[i] > 0){
                p[ip++] = nums[i];

            }
            else{
                n[in++] = nums[i];
            }
        }
        ip = 0;     // resetting value to update 'nums' from these values
        in = 0;     // resetting value to update 'nums' from these values

        //System.out.println(Arrays.toString(p));
        //System.out.println(Arrays.toString(n));

        for( int i = 0; i < nums.length; i++){ // updating 'nums' with its positive and negative numbers adding alternately 
            if( i % 2 == 0){                  // for even index starting with first one, add positive numbers
                nums[i] = p[ip++];
            }
            else{                    // else add negative numbers
                nums[i] = n[in++];
            }
        }
        return nums;
=======
import java.util.Arrays;

public class Solution {
    
    // Method to find the largest perimeter from an array of integers
    public static long largestPerimeter(int[] nums) {
        
        // Sorting the array in ascending order
        Arrays.sort(nums);
        
        // Variable to store the perimeter
        long perimeter = 0;
        
        // Array to store cumulative sums of sorted elements
        long[] h = new long[nums.length];
        h[0] = nums[0];
        
        // Calculating cumulative sums
        for (int i = 1; i < nums.length; i++) {
            h[i] = h[i - 1] + nums[i];
        }
        
        // Iterating through the array to find the largest perimeter
        for (int i = 2; i < nums.length; i++) {
            if (h[i - 1] > nums[i]) {
                // If the sum of the two smaller sides is greater than the largest side
                // then updating the perimeter with the current sum
                perimeter = Math.max(perimeter, h[i]);
            }
        }
        
        // If no valid perimeter is found, returning -1
        if (perimeter == 0) {
            return -1;
        }
        
        // Returning the largest perimeter
        return perimeter;
>>>>>>> Stashed changes
    }
}
```
