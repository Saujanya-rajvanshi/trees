# trees

## INDEX 
- [basic](#basic)
- [height and depth](#height-and-depth)
- [binary tree](#binary-tree)


## basic 

* non - linear data structure
* organize data in hierarchical structure
* individual element is called node
* node stores the actual data , and link to next element
* N number of nodes have maximunum (N-1) number of links 

<img width="563" height="335" alt="image" src="https://github.com/user-attachments/assets/70b9ee06-0f82-4242-a701-6c82a61df99c" />

### height and depth 
In a tree data structure, height and depth are related but different concepts.

---
1. Height
Definition: The height of a node is the number of edges on the longest path from that node to a leaf.
Leaf node: Height = 0.
Height of tree: Height of the root node.
Formula:
Height(node)=1+max⁡(Height(leftChild),Height(rightChild))\text{Height}(node) = 1 + \max(\text{Height}(leftChild), \text{Height}(rightChild))Height(node)=1+max(Height(leftChild),Height(rightChild))
```
Example:    A
           / \
          B   C
         / \
        D   E
```
Height(D) = 0
Height(B) = 1
Height(A) = 2

---

---
2. Depth
Definition: The depth of a node is the number of edges from the root to that node.
Root node: Depth = 0.
Formula:
Depth(node)=Depth(parent)+1\text{Depth}(node) = \text{Depth}(parent) + 1Depth(node)=Depth(parent)+1
```
Example:    A (depth 0)
           / \
          B   C
         / \
        D   E
```
Depth(A) = 0
Depth(B) = 1
Depth(D) = 2

---

##### binary tree 

### 🌳 Binary Tree — Notes (with diagrams)

---

## 1️⃣ Binary Tree

**Definition:**
A binary tree is a special type of tree in which **each node can have at most 2 children**.
* nodes are as left as possible 

* Left child
* Right child

**Possible children count per node:** `0, 1, or 2`

**Diagram:**

```
        A
       / \
      B   C
     /
    D
```

---
### 🌳 Types of Binary Tree 

1️⃣ **Full Binary Tree**
→ Every node has **0 or 2 children**

2️⃣ **Complete Binary Tree**
→ All levels filled except last, filled **left to right**

3️⃣ **Perfect Binary Tree**
→ All internal nodes have **2 children** and all leaves at **same level**

4️⃣ **Degenerate Binary Tree**
→ Each node has **only one child** (like a linked list)

5️⃣ **Skewed Binary Tree**
→ All nodes skewed to **one side** (left or right)

6️⃣ **Balanced Binary Tree**
→ Height difference of left & right subtree ≤ **1**

7️⃣ **Binary Search Tree (BST)**
→ Left < Root < Right

✅ **Fast memory trick:**
**F C P D S B B**
(Full, Complete, Perfect, Degenerate, Skewed, Balanced, BST)

------
