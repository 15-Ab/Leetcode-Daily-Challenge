# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 30-01-24 [Problem Link](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/?envType=daily-question&envId=2024-01-30)
## 150. Evaluate Reverse Polish Notation

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Given an expression in Reverse Polish Notation (RPN), I evaluated the expression and return the result.

My solution uses a stack to keep track of the numeric values during the evaluation of the RPN expression.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialized the Stack :** Created a stack to store numeric values.

**Iterated Through Tokens :** Loop through each token in the RPN expression.
  - If the token is a numeric value, pushed it onto the stack.  
  - If the token is an operator (+, -, *, /), poped two values from the stack, performed the operation, and pushed the result back onto the stack.

**Final Result :** After processing all tokens, the final result is the only element remaining in the stack. Poped it and returned.

##### Helper Method
My solution includes a helper method `isNumeric` to check if a given string represents a numeric value.

My approach leverages the stack data structure to efficiently process and evaluate the RPN expression, handling both numeric values and operators appropriately.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)


# Complexity
- Time complexity : $O(t)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$t$ : number of tokens in the input expression

- Space complexity : $O(t)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {

    // Static stack to store numeric values during evaluation
    static Stack<Integer> num;

    // Method to evaluate Reverse Polish Notation (RPN) expression
    public int evalRPN(String[] tokens) {
        
        // Initializing the stack
        num = new Stack<>();

        // Looping through each token in the expression
        for (int i = 0; i < tokens.length; i++) {
            String s = tokens[i];

            // If the token is a numeric value, pushing it onto the stack
            if (isNumeric(s)) {
                num.push(Integer.parseInt(s));
            } else {
                // If the token is an operator, popping two values from the stack
                int p1 = num.pop();
                int p2 = num.pop();
                int jawab = 0;

                // Performing the operation based on the operator
                if (s.charAt(0) == '+') {
                    jawab = p2 + p1;
                } else if (s.charAt(0) == '-') {
                    jawab = p2 - p1;
                } else if (s.charAt(0) == '*') {
                    jawab = p2 * p1;
                } else if (s.charAt(0) == '/') {
                    jawab = p2 / p1;
                }

                // Pushing the result back onto the stack
                num.push(jawab);
            }
        }

        // The final result is the only element remaining in the stack
        return num.pop();
    }

    // Method to check if a string represents a numeric value
    static boolean isNumeric(String strNum) {
        if (strNum == null) {
            return false;
        }
        try {
            // Attempting to parse the string as a double
            double d = Double.parseDouble(strNum);
        } catch (NumberFormatException nfe) {
            // If an exception is caught, the string is not numeric
            return false;
        }
        // If parsing is successful, the string is numeric
        return true;
    }
}

```