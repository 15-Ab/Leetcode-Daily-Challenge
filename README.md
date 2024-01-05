# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 05-01-24 [Problem Link](https://leetcode.com/problems/longest-increasing-subsequence/description/?envType=daily-question&envId=2024-01-05)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- Dynamic Programming
- - My algorithm must use dynamic programming to efficiently update and maintain the longest increasing subsequence.
- Greedy Choice
- - My algorithm must makes a greedy choice to update the current longest increasing subsequence (a) based on the incoming elements from the input array (nums).


# Approach
<!-- Describe your approach to solving the problem. -->
- ArrayList 'a'
- - I used 'a' to store the current longest increasing subsequence.
- - It starts as an empty ArrayList.
- Iterating through nums
- - My code iterates through each element 's' in the input array nums.
- - For each element :
- - - If a is empty or s is greater than the last element in a, add s to a (greedy choice as it contributes to increasing subsequence).
- - - Otherwise, found the correct position for s in a using the bs function, and update the element at that position with s.
- Binary Search Function 'bs':
- - The 'bs' function performs a binary search on the sorted ArrayList 'a' to find the index of 's' or the index where 's' should be inserted.
- - If 's' is found, it returns the index. If not found, it returns the negation of the insertion point. This insertion point is used to update the current increasing subsequence.
- Return Result :
- - Finally, I returned the length of the longest increasing subsequence is the size of the ArrayList a.
---
- If you're still having trouble understanding what the binary search functions does here, I would suggest you to please go through this site  [search here for binarySearch](https://docs.oracle.com/javase%2F7%2Fdocs%2Fapi%2F%2F/java/util/Collections.html)
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $$O(l*log(l))$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(l)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$l$$ : length of array.
# Code
```
class Solution {
    public int lengthOfLIS(int[] nums) {
        
        ArrayList<Integer> a = new ArrayList<>();
        for( int s : nums){
            if( a.isEmpty() || s > a.get( a.size() - 1) ){
                a.add(s);
            } 
            else{
                a.set( bs(a, s) , s);
            }
        }
        return a.size();
    }

    static int bs( ArrayList<Integer> a, int s){
        int in = Collections.binarySearch(a, s);
        if( in < 0){
            return - in - 1;
        }
        return in;
    }
}
```

# Alternate Approach

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- Dynamic Programming Array (gp):

- - My code creates a dynamic programming array (gp) to store the length of the longest increasing subsequence ending at each index i of the array nums.
- Initialization
- - The array gp is initialized with all elements set to 1. This is because each element in nums singularly represents a subsequence of length 1.
- Comparison and Update
- - My code iterates through each element of nums, comparing it with previous elements and updating the gp array based on the increasing subsequence property.
- Final Result
- - The result is the maximum value present in the gp array, which represents the length of the longest increasing subsequence.


# Approach
<!-- Describe your approach to solving the problem. -->
- Dynamic Programming Array (gp) :
- - gp[i] represents the length of the longest increasing subsequence ending at index i.
- - gp[i] will store the numbers form index '0' to 'i-1' which is smaller than nums[i] = that would be  the length of increasing sunsequence with nums[i] as largest of that sequence
- Initialization of gp :
- - Initially, all elements in gp are set to 1 because each element in nums forms a subsequence of length 1.
- - filled with '1' as every element singularly represents a subsequence of length '1'
- Iterative Comparison and Update :
- - My code uses a nested loop to iterate through each pair of indices (i, j) where j is less than i.
- - For each pair, if nums[i] > nums[j], it means that nums[i] can be included in the increasing subsequence ending at index i, and the length is updated accordingly
- Maximum Length in gp :
- - The final result is the maximum value present in the gp array, representing the length of the longest increasing subsequence.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)
# Complexity
- Time complexity : $$O(l^2)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(l)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$l$$ : length of array.
# Code
```
class Solution {
    public int lengthOfLIS(int[] nums) {
        
        int[] gp = new int[nums.length]; // gp[i] will store the numbers form index '0' to 'i-1' which is smaller than nums[i] = that would be  the length of increasing sunsequence with nums[i] as largest of that sequence
       Arrays.fill(gp, 1); // fill with '1' as every element singularly represents a subsequence of length '1'
       for( int i = 1; i < nums.length; i++){
           for( int j = 0; j < i; j++){
               if( nums[i] > nums[j]){
                   gp[i] = Math.max( gp[i] , gp[j] + 1);
               }
           }
       }
        return Arrays.stream(gp).max().getAsInt(); // this will give the maximum value present in array 
    }
}
```
