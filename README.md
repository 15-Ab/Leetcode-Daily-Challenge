# बसंत पंचमी की हार्दिक शुभकामनाएं।

# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 14-02-24 [Problem Link](https://leetcode.com/problems/rearrange-array-elements-by-sign/description/)
## 2149. Rearrange Array Elements by Sign

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Separated the positive and negative, then update original.

# Approach
<!-- Describe your approach to solving the problem. -->
- I stored the positive and negative in separate arrays in order of there occurence.

- Then simply updated the original 'nums' array by updating alternately with positive and negative numbers.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

# Complexity
- Time complexity : $O(l)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(2*(l/2))$ = $O(l)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$l$ is the length of array

# Code
```
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
    }
}
```
