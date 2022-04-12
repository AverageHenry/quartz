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
```