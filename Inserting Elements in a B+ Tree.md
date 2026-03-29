# Ex. No: 16D - Inserting Elements in a B+ Tree in Python

## AIM:
To write a Python function `def insert(self, key, value):` to insert elements into a **B+ Tree**.

---

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Define a `BPlusTreeNode` class to represent each node in the B+ Tree:
- Store keys and corresponding values.
- Maintain child pointers.
- Track if the node is a leaf.

**Step 3**: Define a `BPlusTree` class to manage the overall structure:
- Implement methods to insert new keys and values.
- Handle node splitting when the node exceeds the allowed degree.

**Step 4**: Implement `insert(self, key, value)`:
- Locate the correct leaf node for insertion.
- Insert key-value pair.
- If the node overflows, split the node and propagate the split up if necessary.

**Step 5**: Implement methods to handle:
- Finding the appropriate node for insertion.
- Splitting full nodes.
- Linking leaf nodes for fast range queries.

**Step 6**: Print the B+ Tree level-wise after insertion.

---

## Program

```
# Searching a key on a B-tree in Python
# Create a node
class BTreeNode:
  def __init__(self, leaf=False):
    self.leaf = leaf
    self.keys = []
    self.child = []

# Tree
class BTree:
  def __init__(self, t):
    self.root = BTreeNode(True)
    self.t = t

    # Insert node
  def insert(self, k):
    root = self.root
    if len(root.keys) == (2 * self.t) - 1:
      temp = BTreeNode()
      self.root = temp
      temp.child.insert(0, root)
      self.split_child(temp, 0)
      self.insert_non_full(temp, k)
    else:
      self.insert_non_full(root, k)

    # Insert nonfull
  def insert_non_full(self, x, k):
    i = len(x.keys) - 1
    if x.leaf:
      x.keys.append((None, None))
      while i >= 0 and k[0] < x.keys[i][0]:
        x.keys[i + 1] = x.keys[i]
        i -= 1
      x.keys[i + 1] = k
    else:
      while i >= 0 and k[0] < x.keys[i][0]:
        i -= 1
      i += 1
      if len(x.child[i].keys) == (2 * self.t) - 1:
        self.split_child(x, i)
        if k[0] > x.keys[i][0]:
          i += 1
      self.insert_non_full(x.child[i], k)

    # Split the child
  def split_child(self, x, i):
    t = self.t
    y = x.child[i]
    z = BTreeNode(y.leaf)
    x.child.insert(i + 1, z)
    x.keys.insert(i, y.keys[t - 1])
    z.keys = y.keys[t: (2 * t) - 1]
    y.keys = y.keys[0: t - 1]
    if not y.leaf:
      z.child = y.child[t: 2 * t]
      y.child = y.child[0: t - 1]

  # Print the tree
  def print_tree(self, x, l=0):
    print("Level ", l, " ", len(x.keys), end=":")
    for i in x.keys:
      print(i, end=" ")
    print()
    l += 1
    if len(x.child) > 0:
      for i in x.child:
        self.print_tree(i, l)

def main():
  B = BTree(3)

  for i in range(10):
    B.insert((i, 2 * i))
  print("B Tree :")
  B.print_tree(B.root)
  B.insert((11,))
  print("\nB Tree after insertion")
  B.print_tree(B.root)

if __name__ == '__main__':
  main()
```

## OUTPUT
![Screenshot 2025-05-05 013141](https://github.com/user-attachments/assets/6132be85-19b8-4ae4-99d6-81116a0d5bc7)

## RESULT
Thus, the function insert(self, k) inserts nodes into a B-Tree while maintaining its properties — completed successfully.
