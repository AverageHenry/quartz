# Counting Sort
---
### Use Case: 
Used to sort an array with many entries of 'small' values.

---

### Algorithm Overview:
- Create a data structure to count the occurrence of each number (or object). This will most likely be a **[[Hash Table]]** or an array of size **k** (ranging from min to max) initialized to all zeroes.
- After counting the frequency of values, loop over the keys in numerical order and add the key to an output list a number of times based on the frequency of the key.
- Return the output list.

---

#### Time Complexity: O (n + k)
#### Space Complexity: O (k)
Where **k** is the # of keys in the hash table and **n** is the input size.

---

What if we're dealing with objects where stability matters? (Student objects, for example):
![[content/Interview Kickstart Notes/Sorting Foundations/Pasted image 20211114233536.png]]