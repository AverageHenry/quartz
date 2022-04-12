# Printing All Permutations
### Printing Permutations With Repetitions Allowed
##### Example: Print all decimal strings of length n.
```python
def decimal_strings_of_length_n(n):

	def dshelper(slate):
		# Base Case:
		if len(slate) == n:
			print(slate)
		else: # Recursive case
			# Test for digits 0-9
			for i in range(10):
				slate.append(i)
				dshelper(slate)
				slate.pop()

	# Call helper function from the top manager's perspective
	dshelper([])
```

Time: O (10<sup>n</sup> x n)
Space: O (n)

### Printing Permutations Without Repetitions
##### Example: Given a set (or string) of n distinct characters, print all permutations (of size n, no repetitions allowed)
![[content/InterviewKickstartNotes/Recursion Foundations/Images/permutations_no_duplicates.png]]
Time: O (n! x n) --> Since repetition is not allowed in our input, the number of possibilities is n!, since n x n-1 x n-2 x ... 1 == n!. We know that we will have n! leaf nodes, and each leaf node is doing n work (printing the slate of length n), so the total work being done is n! x n.

Space: O (n) --> This is recursive DFS. We only use the call stack, and we know our call stack cannot contain more than n function calls for this algorithm.