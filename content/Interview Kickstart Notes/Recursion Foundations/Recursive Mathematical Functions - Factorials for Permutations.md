# Recursive Mathematical Functions - Factorials for Permutations

---

## Basic Combinatorics
### The Factorial Function
* How many ways can you arrange n different objects in a straight line?
	* Example: [a, b, c, d] would have 4 x 3 x 2 x 1 different ways.
	* n x (n - 1) x (n - 2) x (n - 3) x ... x 1 = n!
	* This is known as a *Permutation*.
	* The number of permutations for n objects is n!.
* So far, no repetitions have been allowed. What if they were?
	* If repetitions were allowed, [a, b, c, d] would have 4 x 4 x 4 x 4 different ways.
	* n x n x n x ... x n = n<sup>n</sup>
	* This is known as an *Arrangement*.
	* The number of arrangements possible for n objects is n<sup>n</sup>.
	* Example: How many binary strings of length n are possible?
		* 2 x 2 x 2 x 2 x 2 x ... x 2 = 2<sup>n</sup>
	* How about the number of 4-digit passcodes that are possible?
		* 10 x 10 x 10 x 10 = 10<sup>4</sup>

### Calculating the value of n! using [[content/Interview Kickstart Notes/Design Strategies/Decrease & Conquer]]
#### Top-down Recursive Solution
```python
def fact(n):
	if n == 0:
		return 1
	else:
		# Chip away at the problem by reducing it to size - 1
		# Ask worker clone to solve the smaller problem
		# Construct the solution to the overall problem using that
		return n * fact(n - 1)
```
#### Bottom-up Iterative Solution
```python
def fact(n):
	result = 1
	for i in range(1, n):
		result *= i
		
	return result
```
