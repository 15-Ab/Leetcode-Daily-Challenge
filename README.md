# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 15-01-24 [Problem Link](https://leetcode.com/problems/insert-delete-getrandom-o1/description/?envType=daily-question&envId=2024-01-16)
## 380. Insert Delete GetRandom O(1)


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
This `RandomizedSet` class aims to efficiently manage a set of unique integers while supporting insert, remove, and getRandom operations. The underlying data structure used by me is a HashSet, ensuring constant-time complexity for basic set operations.

# Approach
<!-- Describe your approach to solving the problem. -->
#### `insert` Operation:
   - **Objective:** Added a new element to the set if it doesn't already exist.
   - **Implementation:**
     - Checked if the element is already present in the HashSet (`h`).
     - If not present, added the element to the HashSet.

#### `remove` Operation:
   - **Objective:** Removed a specified element from the set if it exists.
   - **Implementation:**
     - Checked if the element is present in the HashSet.
     - If present, removed the element.

#### `getRandom` Operation:
   - **Objective:** Returned a random element from the set.
   - **Implementation:**
     - Generated a random index (`ri`) within the size of the HashSet.
     - Iterated through the HashSet using an iterator.
     - When the iterator reaches the element at index `ri`, returned that element.

#### Key Points:
   - The use of a HashSet ensures uniqueness and constant-time complexity for insert and remove operations.
   - The getRandom operation leverages the fact that HashSet doesn't guarantee any specific order, allowing random access with constant time.
   - The random index is generated using `Random().nextInt(h.size())`.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)


# Complexity
- Time complexity : $O(1)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$n$ : number of unique elements stored in the HashSet

# Code
```
class RandomizedSet {

    // HashSet to store unique integers
    static HashSet<Integer> h;

    // Constructor initializes the HashSet
    public RandomizedSet() {
        h = new HashSet<>();
    }
    
    // Method to insert a value into the set
    public boolean insert(int val) {
        // If the set already contains the value, returned false (no insertion)
        if (h.contains(val)) {
            return false;
        } else {
            // Otherwise, added the value to the set and returned true (insertion successful)
            h.add(val);
            return true;
        }
    }
    
    // Method to remove a value from the set
    public boolean remove(int val) {
        // If the set contains the value, removed it and return true (removal successful)
        if (h.contains(val)) {
            h.remove(val);
            return true;
        } else {
            // Otherwise, returned false (value not present, no removal)
            return false;
        }
    }
    
    // Method to get a random element from the set
    public int getRandom() {
        // Generated a random index within the size of the set
        int randomIndex = new Random().nextInt(h.size());
        int currentIndex = 0;

        // Iterated over the set to find the element at the random index
        for (int element : h) {
            // If the current index matches the random index, returned the element
            if (currentIndex == randomIndex) {
                return element;
            }
            currentIndex++;
        }

        // Returned -1 if the set is empty or for any other unexpected condition
        return -1;
    }
}

/**
 * Your RandomizedSet object will be instantiated and called as such:
 * RandomizedSet obj = new RandomizedSet();
 * boolean param_1 = obj.insert(val);
 * boolean param_2 = obj.remove(val);
 * int param_3 = obj.getRandom();
 */

```
