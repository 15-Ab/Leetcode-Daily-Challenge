# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 04-01-24 [Problem Link](https://leetcode.com/problems/minimum-number-of-operations-to-make-array-empty/description/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
- Frequency Count :
- - The code starts by creating a HashMap (m) to store the frequency of each number in the given array. This is crucial for determining how many times each number appears in the array.

- Divisibility by 3 :
- - The primary goal is to minimize the operations needed to make all elements 0. The code examines the frequency of each number and calculates the minimum operations required based on certain conditions.

# Approach
<!-- Describe your approach to solving the problem. -->
- HashMap for Frequency :
- - Iterate through the input array (nums).
Use a HashMap (m) to store the frequency of each number in the array.
- Calculate Operations :
- - Iterate through the keys of the HashMap (m).
- - For each key 'k' observe it's occurence :
- - - If the occurrence is 1, return -1 (as it's not possible to make it 0 by subtracting 2 or 3).
- - - if occurence of number is divisible by 3, total operations = occurences/3 
- - - if occurence of number is of form 3*n + 1, let's try to break it down
- - - - 3*n + 1 = 3*(n-1) + 4 = 3*(n-1) + 2*(2) -> n-1+2 operations = n+1 
- - - if occurence of number is of form 3*n + 2, let's try to break it down
- - - - 3*n + 2 = 3*(n) + 2*(1) -> n+1 operations 
- Return Result :
- - Return the total number of operations needed to make all numbers in the array divisible by 3. 
=======
## Today's 03-01-24 [Problem Link](https://leetcode.com/problems/number-of-laser-beams-in-a-bank/description/?envType=daily-question&envId=2024-01-03)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Basic multiplication.
# Approach
<!-- Describe your approach to solving the problem. -->
- I kept track of number of '1' in a row
- Now iterated over every row of array 
- - counted the number of '1' in current row
- - number of beams will the product of current number of device and previous number of devices
- -  added the product to answer
- -  now, the current one will become the previous one to next row
>>>>>>> 8326dfdfc4354991bd3c7f23df8fcaa854307652
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O(l)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
<<<<<<< HEAD

- Space complexity : $$O(u)$$

$$l$$ : size of array
$$u$$ : number of unique letters in array
=======
$$l$$ : length of array
- Space complexity : $$O(1)$$
>>>>>>> 8326dfdfc4354991bd3c7f23df8fcaa854307652
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
<<<<<<< HEAD
    public int minOperations(int[] nums) {
        boolean haveone = false;
        HashMap<Integer, Integer> m = new HashMap<>();
        for( int i = 0; i < nums.length; i++){
            m.put( nums[i], m.getOrDefault(nums[i], 0) + 1);
        }
        int operations = 0;

        // if occurence of number is divisible by 3, total operations = occurences/3 
        // if occurence of number is of form 3*n + 1, let's try to break it down
        //  3*n + 1 = 3*(n-1) + 4 = 3*(n-1) + 2*(2) -> n-1+2 operations = n+1 
        // if occurence of number is of form 3*n + 2, let's try to break it down
        //  3*n + 2 = 3*(n) + 2*(1) -> n+1 operations 
  
        for( int k : m.keySet()){
            if( m.get(k) == 1){
                return -1;
            }
            if( m.get(k) % 3 == 0){
                operations += m.get(k)/3;
            }
            else{
                operations += m.get(k)/3 + 1;
            }
        }
        return operations;
=======
    public int numberOfBeams(String[] bank) {
        int jawab = 0;      // to store answer
        int picheek = 0;    // to store number of '1' in previous state

        for( String r : bank){
            int ek = (int) r.chars().filter( g -> g == '1').count(); // counting the number of '1' in current row
            if( ek != 0){             // number of beams will the product of current number of device and previous number of devices
                jawab += picheek*ek; // adding the product to answer
                picheek = ek;        // now, the current one will become the previous one to next row
            }
        }
        return jawab;
>>>>>>> 8326dfdfc4354991bd3c7f23df8fcaa854307652
    }
}
```