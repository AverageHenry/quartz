# Recursion Lecture Notes

### Agenda

Recursion is a bit of a misnomer for this lecture. 
- Recursion has been seen in sorting: Insertion Sort, Merge Sort, and QuickSort.
- Recursion has been seen in searching: Binary Search.
- Binary Trees are an example of a recursive data structure. It is easy to write recursive algorithms on recursive data structures.
- You will see examples of recursion in Graphs and Dynamic Programming.

With that being said, **recursion pervades the whole curriculum**.

- The distinctive thing about this lecture is that the "class of problems" that are going to be seen are **Combinatorial Enumeration** problems, with **Backtracking** problems as well.
- Writing recursive code for these problems is more tricky.

---

## Exhaustive Enumeration
Exhaustive Enumeration requires a systematic enumeration/generation of all possible objects (permutation or combinations).

This leads to a **combinatorial explosion** - exponential time complexity. Hence, this is *impractical for even moderate input sizes*.

Still, for many problems of this nature, e cannot do better than this.

##### Given a set of n objects, we:
- Sorted them ([[content/Interview Kickstart Notes/Sorting Foundations/_Sorting Overview|Sorting Foundations]]).
- Will enumerate all permutations and combinations.

##### How many permutaions are possible for a set of n distinct objects?
n! --> n x (n - 1) x (n - 2) x ... x 1

##### How many combinations are possible for a set of n distinct objects?
2<sup>n</sup> 

---

### General Template
You have to fill in a series of blanks, and there is an exponential number of ways to do it.

" __  __  __  __  __  __ __"

This series of blanks represent a combinatorial object (some permutation or combination).

You proceed left to right, and as a lazy manager, only take responsibility for filling in the first blank. Delegate the rest of the work to your subordinates.

Write up a general strategy used by any arbitrary worker in the heirarchy as a recursive function.

This is what the general template will look like in code:

```python
def helper(partial_solution, subproblem_definition): # partial_solution is a "slate"
	# Base Case: Leaf Worker
	if subproblem_definition is empty:
		# Partial solution is a complete P/C
		Add the complete solution to the "global bag"
		return
	# Recursive Case: Interal Node Workers
	else:
		# Let c1, c2, c3... ck be the number of choices for filling into the leftmost blank
		For each of those choices ci:
			Add ci to the slate (append)
			helper(enlarged_slate, smaller_subproblem)
			
def overall(a_set_of_n_objects):
	result = []
	helper(blank_slate, complete_problem_of_size_n)
	return result
```

### Question 1: Letter Case Permutation ([[www.google.com|Leetcode #784]])
![[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/Pasted image 20220412000103.png]]

##### [[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/letter_case_permutations.png|Solution using a mutable slate]]

##### Time Complexity: O (2<sup>n</sup> x n)
##### Space Complexity: **O (n)**  

### Question 2: Subsets - No Duplicates
![[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/Pasted image 20220412010727.png]]
##### [[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/generate_subsets_no_repetition.png|Solution using mutable slate]]
### Question 3: Permutations - No Repetition
![[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/Pasted image 20220412110645.png]]

##### [[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/permutations_no_repetitions.png|Solution using a mutable slate]]
Time Complexity: O (n! x n)
Space Complexity: O (n! x n)

#### Question 4: Permutations II - With Repetition
![[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/Pasted image 20220412130408.png]]
##### [[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/permutations_with_repetition.png|Solution:]]
- Solution would be the same as Permutations I. The only difference is you add a hashtable/hashset to see if we have already processed a number. If so, we continue, if not, we proceed to make a recursive call and then add the number to our hashtable/hashset.
- Time Complexity: O (n! x n)
- Space Complexity: O (n! x n) --> Keep in mind that in the worst case (all numbers are distinct), we store every number in the array into the hashtable at every level in our recursion tree, so that would take up n<sup>2</sup> space.
- NOTE: An alternative solution to this would be to sort the input beforehand and count the number of occurrences, then call the helper function based on the number of occurrences of the current number. We would then skip the duplicate values by passing **i + count** to the helper function. This approach would use less space, but take more time to run.

### Question 5: Subsets II - With Repetition
![[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/Pasted image 20220412141003.png]]

##### [[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/subsets_with_repetition.png|Solution]]

---
## Backtracking
When we say backtracking in this case, we mean **returning back to the calling function**.
It is an algorithm design strategy for adding constraints in a combinatorial enumeration problem.

Sometimes, we can evaluate the the partially constructed solutions to a problem:
- If none of the ways to fill in the remaining blanks can lead to a solution (or if we can identify the one, single solution that will emerge), we do not need to work to fill in the remaining blanks.
- Instead, we backtrack from that internal node, thus pruning away the subtree rooted at it. This can be considered a **Constraint Filter**. To implement this, all we have to do is add a [[Pasted image 20220412162853.png|Backtracking Case]] to our recursion template.
- Though it leads to an exponential improvement in combinatorial search, the resulting time is not polynomial, but an "improved exponential time" (it is difficult to give an exact expression for the time complexity). It is best treated as a heuristic rather than something amenable to worst-case analysis.

Check out this [[content/Interview Kickstart Notes/Recursion Lecture Notes/Images/Combinatorial Path.png|Combinatorial Path]]. It shows how cominatorial problems are built on top of one another.