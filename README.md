# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 15-01-24 [Problem Link](https://leetcode.com/problems/find-players-with-zero-or-one-losses/description/?envType=daily-question&envId=2024-01-15)
## 2225. Find Players With Zero or One Losses


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My Java code aims to find the winners and players who have lost only once in a series of matches. It uses a HashMap to store the count of losses for each player and a HashSet to store the winners.

# Approach
<!-- Describe your approach to solving the problem. -->
###### HashMap and HashSet Initialization

- Initialized `loser` as a HashMap to store the count of losses for each player.
- Initialized `winner` as a HashSet to store the winners.

###### Iterated through Matches

- For each match in the `matches` array:
  - Add the first player of the match to the `winner` set.
  - If the second player is not in the `loser` map, add it with a count of 1.
  - If the second player is already in the `loser` map, increment its count by 1.

###### Identified `Not Lost` Players

- Created a list `notlost` to store players who haven't lost.
- Iterated through the `winner` set:
  - If a player is not in the `loser` map, added them to the `notlost` list.

###### Identified Players `Lost Only` Once

- Created a list `lostone` to store players who have lost only once.
- Iterate through the `loser` map:
  - If a player has lost only once (count = 1), added them to the `lostone` list.

###### Sort Lists

- Sorted both `notlost` and `lostone` lists.

###### Created a Result List

- Created a list of lists `jawab` to store the final result.
- Added `notlost` and `lostone` lists to `jawab`.

###### Return Result

- Returned the `jawab` list containing the players who haven't lost and those who have lost only once.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)


# Complexity
- Time complexity : $O(N + M + K*log(K))$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$N$ : number of matches 

$M$ : number of players 

$K$ : number of players who have lost only once

$K*log(K)$ : sorting of lists

- Space complexity : $O(M+K)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public List<List<Integer>> findWinners(int[][] matches) {
        // HashMap to store the count of losses for each player
        HashMap<Integer, Integer> loser = new HashMap<>();
        // HashSet to store the winners
        HashSet<Integer> winner = new HashSet<>();

        // Iterated through each match
        for (int[] r : matches) {
            // Added the first player of the match to the winner set
            winner.add(r[0]);
            // If the second player is not in the loser map, added it with a count of 1
            // If the second player is already in the loser map, incremented its count by 1
            loser.putIfAbsent(r[1], 0);
            loser.put(r[1], loser.get(r[1]) + 1);
        }

        // Lists to store players who haven't lost and those who have lost only once
        List<Integer> notlost = new ArrayList<>();
        List<Integer> lostone = new ArrayList<>();

        // Iterated through the winner set
        for (int w : winner) {
            // If a player is not in the loser map, added them to the notlost list
            if (!loser.containsKey(w)) {
                notlost.add(w);
            }
        }

        // Iterated through the loser map
        for (int lo : loser.keySet()) {
            // If a player has lost only once (count = 1), added them to the lostone list
            if (loser.get(lo) == 1) {
                lostone.add(lo);
            }
        }

        // Sorted both notlost and lostone lists
        Collections.sort(notlost);
        Collections.sort(lostone);

        // List of lists to store the final result
        List<List<Integer>> jawab = new ArrayList<>();
        jawab.add(notlost);
        jawab.add(lostone);

        // Returned the result
        return jawab;
    }
}

```
