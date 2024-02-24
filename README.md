# Leetcode Daily Challenge Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Always here to assist you guys.

## Today's 24-02-24 [Problem Link](https://leetcode.com/problems/find-all-people-with-secret/description/?envType=daily-question&envId=2024-02-24)
## 2092. Find All People With Secret

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
**Disjoint Set** : I utilized the Disjoint Set (Union-Find) data structure to manage connected components.

**Union by Rank** : Optimized union operations by merging sets based on their ranks.

**Path Compression** : Enhanced find operations with path compression to shorten the path to the root.

# Approach
<!-- Describe your approach to solving the problem. -->
**Initialized the Disjoint Set** : I created a Disjoint Set to represent individual sets for each element.

**Connected Initial Person** : Connected the specified initial person to the root of the disjoint set.

**Organized the Meetings** : I sorted meetings by time using a TreeMap to process them chronologically.

**Processed Meetings** : For each meeting, connected people in the disjoint set and reset unconnected nodes.

**Find Connected People** : Identified all people connected to the root of the disjoint set.

**Result** : Provided the list of people connected to the specified initial person.

My approach ensured efficient management of connected components, enabling the identification of individuals connected to a given starting point.

---
Have a look at the code , still have any confusion then please let me know in the comments ... Keep Solving.:)
# Complexity
- Time complexity : $O(m * log n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$m$ : number of meetings
$n$ : number of peoples
- Space complexity : $O(n + m)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
// Implementation of Disjoint Set (Union-Find) data structure
class DisjointSet {
  private int[] parent;
  private int[] rank;

  // Constructor to initialize the disjoint set with individual sets for each element
  public DisjointSet(int size) {
    parent = new int[size];
    rank = new int[size];
    for (int i = 0; i < size; ++i)
      parent[i] = i;
  }

  // Union operation with rank optimization to merge sets
  public void unionByRank(int u, int v) {
    final int rootU = find(u);
    final int rootV = find(v);
    if (rootU == rootV)
      return;
    if (rank[rootU] < rank[rootV]) {
      parent[rootU] = rootV;
    } else if (rank[rootU] > rank[rootV]) {
      parent[rootV] = rootU;
    } else {
      parent[rootU] = rootV;
      ++rank[rootV];
    }
  }

  // Find operation to determine the root of the set to which an element belongs
  public boolean isConnected(int u, int v) {
    return find(u) == find(v);
  }

  // Resetting the parent of a node, useful for disconnecting nodes from a set
  public void resetNode(int u) {
    parent[u] = u;
  }

  // Recursive find operation with path compression for efficient set determination
  private int find(int u) {
    return parent[u] == u ? u : (parent[u] = find(parent[u]));
  }
}

// Solution class that utilizes the DisjointSet to find all people connected to a specific person
class Solution {

  // Method to find all people connected to a specific person based on meeting times
  public List<Integer> findAllPeople(int numOfPeople, int[][] meetings, int initialPerson) {
    List<Integer> result = new ArrayList<>();
    DisjointSet disjointSet = new DisjointSet(numOfPeople);
    TreeMap<Integer, List<Pair<Integer, Integer>>> timeToPairs = new TreeMap<>();

    // Connecting the initial person to the root of the disjoint set
    disjointSet.unionByRank(0, initialPerson);

    // Organizing meetings based on time
    for (int[] meeting : meetings) {
      timeToPairs.putIfAbsent(meeting[2], new ArrayList<>());
      timeToPairs.get(meeting[2]).add(new Pair<>(meeting[0], meeting[1]));
    }

    // Processing meetings and connect people in the disjoint set
    for (List<Pair<Integer, Integer>> pairs : timeToPairs.values()) {
      Set<Integer> connectedPeople = new HashSet<>();
      for (Pair<Integer, Integer> pair : pairs) {
        final int personX = pair.getKey();
        final int personY = pair.getValue();
        disjointSet.unionByRank(personX, personY);
        connectedPeople.add(personX);
        connectedPeople.add(personY);
      }
      // Resetting nodes not connected to the root of the set
      for (final int person : connectedPeople)
        if (!disjointSet.isConnected(person, 0))
          disjointSet.resetNode(person);
    }

    // Finding all people connected to the root of the disjoint set
    for (int i = 0; i < numOfPeople; ++i)
      if (disjointSet.isConnected(i, 0))
        result.add(i);

    return result;
  }
}
```