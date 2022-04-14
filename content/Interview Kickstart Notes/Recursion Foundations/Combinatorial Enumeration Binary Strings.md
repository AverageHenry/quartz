# Combinatorial Enumeration Binary Strings

---

## Given a set of n distinct objects, enumerate all possible 'combinatorial objects':
-  Can be Permutations or Combinations
-  If ordering matters, we will use permutations.
	- Repetitions allowed or
	- No repetitions allowed
-  If ordering doesn't matter, we will use combinations/subsets.

### Example: Enumerate/print all possible binary strings of length n.

![[content/Interview Kickstart Notes/Recursion Foundations/Images/Pasted image 20220410143338.png]]
This can be done Iteratively and Recursively using BFS. While the time complexity would be 2<sup>n</sup> x n, the space complexity would be 2<sup>n</sup>, which is a lot. Consider Recursive DFS instead:
![[content/Interview Kickstart Notes/Recursion Foundations/Images/Pasted image 20220410150210.png]]
Using Recursive DFS would still give us a time complexity of 2<sup>n</sup> x n, but our space will be significantly reduced to n, since there would be no more than n function calls in our call stack at any point in time.
