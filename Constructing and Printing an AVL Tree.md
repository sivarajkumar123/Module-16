# Ex. No: 16A - Constructing and Printing an AVL Tree in Python

## AIM:
To write a Python program to construct an **AVL tree** and print the nodes of it using the appropriate packages and built-in function.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define a function `getDictTree(tree)` to return the **dict_tree** of an AVL tree.

**Step 3**: Define a function `Construct_AVL(L)` to:
- Create an **AVL tree** from the list `L`.
- Get and print the **dict_tree** using `getDictTree(tree)`.

**Step 4**: Define a list `L` with integer values.

**Step 5**: Call `Construct_AVL(L)` to build the tree and print the result.

**Step 6**: End the program.

---
## Program

```
from TreeAVL.AVL import AVL

def getDictTree(self):
 return self.dict_tree

def Construct_AVL(L):
  tree = AVL(L)
  print(getDictTree(tree))
```

## OUTPUT
![Screenshot 2025-05-05 012058](https://github.com/user-attachments/assets/62360160-f527-4f28-9a3f-54549dac38f5)

## RESULT
Thus, the program inserts the values into an AVL Tree while maintaining balance, and prints the nodes — completed successfully.
