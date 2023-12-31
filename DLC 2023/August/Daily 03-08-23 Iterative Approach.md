# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Can be solved by using Unitary method , keep a char in hand and add one-by-one . 

# Approach
<!-- Describe your approach to solving the problem. -->
This approach is iterative and similar to Permutations(46) : https://leetcode.com/problems/permutations/solutions/3851382/daily-02-08-23/

- iterate for all digits present in digits string
- a temporary list of string that will get modified after each iteration 
- for every string present in answer list add characters of currently iterated digit      
- change the answer list to currently updated answer list
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

---
Recursive Approach : https://leetcode.com/problems/letter-combinations-of-a-phone-number/solutions/3857876/recursive-approach-daily-03-08-23/

# Complexity
- Time complexity : $$O(n*4^n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(4^n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public List<String> letterCombinations(String digits) {   // recursive approach : similar to permutations 46
         if (digits.isEmpty()){
            return new ArrayList<>();
        }
      
       List<String> ans = new ArrayList<>();
        ans.add( "");                                              // initialise answer list as empty string

        String[] numTochar = { "", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz" };  // it stores the keypad in array form
                            // each index correponds to respective possible characters

        for( char s : digits.toCharArray() ){                       // iterate for all digits present in digits string
            List<String> a = new ArrayList<>();                     // a temporary list of string that will get modified after each iteration 
            for( String p : ans){                                   // for every string present in answer list ...
                for( char n : numTochar[ s - '0'].toCharArray() ){  // ... add characters of currently iterated digit
                    a.add( p + n);
                }
            }
            ans = a;                                                // update the answer list to currently updated answers
        }
        return ans;
    }
}
```