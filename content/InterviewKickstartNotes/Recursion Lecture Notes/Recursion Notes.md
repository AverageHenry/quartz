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
- Sorted them ([[content/InterviewKickstartNotes/Sorting Foundations/_Sorting Overview|Sorting Foundations]]).
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
![[Pasted image 20220412000103.png]]

##### Here is the solution using a mutable slate:

![[content/InterviewKickstartNotes/Recursion Lecture Notes/letter_case_permutations.png]]

##### Time Complexity: O (2<sup>n</sup> x n)
##### Space Complexity: **O (n)**  

### Question 2: Subsets - No Duplicates
![[Pasted image 20220412010727.png]]
![[content/InterviewKickstartNotes/Recursion Lecture Notes/generate_all_subsets.png]]
### Question 3: Permutations
![[Pasted image 20220412110645.png]]
![[content/InterviewKickstartNotes/Recursion Lecture Notes/permutations_no_repetitions.png]]
