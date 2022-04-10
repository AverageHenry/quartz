# Recursion as a Lazy Manager's Strategy

---

## Recursion
Solving large problems by reducing them to smaller problems **of the same form**.

Reduce a large problem to one or more subproblems that are
- Identical in nature
- Somewhat simpler to solve

Then use the same decomposition technique to divide the subproblems into new ones that are even simpler... until they become so simple that you can solve them without further subdivision.

Reassemble the solved components to obtain the complete solution to the original problem.

![[content/InterviewKickstartNotes/Recursion Foundations/Pasted image 20220409150029.png]]

### Question: How many subsets of a set of size n are there?
- There are 2<sup>n</sup> subsets.
	- {} -> {} 1
	- {a} --> {}, {a} 2
	- {a, b} --> {}, {a}, {b}, {a, b} 4
	- ...
