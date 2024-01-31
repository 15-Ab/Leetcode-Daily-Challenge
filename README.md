# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 31-01-24 [Problem Link](https://leetcode.com/problems/daily-temperatures/description/?envType=daily-question&envId=2024-01-31)
## 739. Daily Temperatures

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This problem is to find the next higher temperature for each day in a given array of temperatures. To efficiently solve this problem, I used a stack to keep track of the indices of temperatures that we have encountered so far. My idea is to iterate through the array, and for each day, pop the indices from the stack where the corresponding temperatures are lower than the current day's temperature. For each popped index, I calculated the time difference to the current day and updated the result array with this information.


# Approach
<!-- Describe your approach to solving the problem. -->
- Initialized an array `jawab` to store the result, where `jawab[i]` will represent the number of days until a warmer temperature is encountered for the day at index `i`.

- Initialized an empty stack `s` to keep track of indices.

- Iterated through the given array of temperatures using a loop.

- For each day, checked if the stack is not empty and the current temperature is greater than the temperature at the index at the top of the stack.

  - If true, popped the index from the stack, and calculated the time difference between the current day and the popped index. Updated `jawab` with this information.

  - Continued this process until the stack is empty or the top of the stack has a temperature greater than or equal to the current day's temperature.

- Pushed the current index onto the stack.

- After the loop, the `jawab` array contained the desired result, representing the number of days until a warmer temperature is encountered for each day.

- Returned the `jawab` array as the final result.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(e)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

$e$ :  number of elements in the given array of temperatures
- Space complexity : $O(e)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Static array to store the result
    static int[] jawab;

    // Method to calculate daily temperatures
    public int[] dailyTemperatures(int[] temperatures) {
        
        // Initializing the result array with the length of temperatures array
        jawab = new int[temperatures.length];
        
        // Stack to keep track of indices of temperatures
        Stack<Integer> s = new Stack<>();

        // Iterating through the temperatures array
        for (int i = 0; i < temperatures.length; i++) {

            // Checking if the stack is not empty and the current temperature is greater than the temperature at the index at the top of the stack
            while (!s.isEmpty() && temperatures[i] > temperatures[s.peek()]) {
                // Popping the index from the stack and calculate the time difference to the current day
                int g = s.pop();
                jawab[g] = i - g;
            }

            // Pushing the current index onto the stack
            s.push(i);
        }

        // Returning the result array
        return jawab;
    }
}

```