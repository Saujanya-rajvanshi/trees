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

## 🌳 Binary Tree 

- [definition](#Definition)
- [types](#types)
- [extended binary tree](#xtended-binary-tree)
- [properties of binary tree](#properties-of-binary-tree)
- [representing binary tree](#representing-binary-tree)
- [binary tree traversal](#binary-tree-traversal)

---

## 1️⃣ Binary Tree

### Definition:
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

```
FULL        COMPLETE        PERFECT        DEGENERATE        LEFT SKEWED     RIGHT SKEWED     BALANCED        BST
  o            o               o               o                 o               o               o               5
 / \          / \             / \               \               /                 \             / \             / \
o   o        o   o           o   o               o             o                   o           o   o           3   7
            /               / \                   \           /                     \         / \             2   4
           o               o   o                   o         o                       o       o   o
```

✅ **Fast memory trick:**
**F C P D S B B**
(Full, Complete, Perfect, Degenerate, Skewed, Balanced, BST)

---

##### extended binary tree

## Extended Binary Tree 

**Definition**

* An **Extended Binary Tree (EBT)** is formed by converting a binary tree into a **full binary tree** by adding **dummy (external) nodes** wherever a child is missing.

**Node Types**

* **Internal nodes** → original tree nodes
* **External nodes** → added dummy nodes (represent NULL children)

**Key Points**

* Every **internal node has exactly 2 children**
* Every **external node is a leaf**
* All NULL subtrees are replaced by external nodes
* Useful in **expression trees** and **theoretical analysis**

**Properties**

* External nodes = Internal nodes + 1
* Internal nodes are **non-leaf**
* External nodes have **no children**

---

### **Diagram (Original → Extended) in ONE ROW**

```
Original Binary Tree                 Extended Binary Tree
        A                                   A
       / \                                 / \
      B   C                               B   C
     /   / \                             / \ / \
    D   G   H                           D  □ G  H
                                           / \ / \
                                          □  □ □  □
```

**Legend**

* `○ / letters` → Internal nodes
* `□` → External (dummy) nodes

---
---
## properties of binary tree

**1. Maximum nodes at level `l`**

* Max nodes = **2ˡ**
* Root is at **level 0**

**2. Maximum nodes in a binary tree of height `h`**

* Max nodes = **2^(h+1) − 1**/
* Height = longest path from root to leaf

**3. Minimum nodes in a binary tree of height `h`**

* Min nodes = **h + 1**
* (Skewed binary tree)

**4. Maximum height of a binary tree with `N` nodes**

* Max height = **N − 1**
* (Completely skewed tree)

**5. Minimum height of a binary tree with `N` nodes**

* Min height = **⌈log₂(N + 1)⌉ − 1**
* (Perfect / complete binary tree)
  
---

## representing binary tree 

can be represenyed in two ways 
1. array representation - [array representation](#array-representation)
2. linked representation - [linked representation](#linked-representation)

## array representation

* Array Representation of Binary Tree
* Used mainly for perfect / complete binary trees
* Nodes stored in level-order traversal
* Each node gets a unique array index
* Easy parent–child index calculation

```
┌───────────────────────────────┐      ┌────────────────────────────────┐
│  CASE 1: Index starts with 1  │      │   CASE 2: Index starts with 0  │
├───────────────────────────────┤      ├────────────────────────────────┤
│ Root index = 1                │      │ Root index = 0                 │
│                               │      │                                │
│ Parent(i) = ⌊ i / 2 ⌋          │      │ Parent(i) = ⌊ (i − 1) / 2 ⌋     │
│                               │      │                                │
│ Left child = 2i               │      │ Left child = 2i + 1            │
│                               │      │                                │
│ Right child = 2i + 1          │      │ Right child = 2i + 2           │
└───────────────────────────────┘      └────────────────────────────────┘

```
```
    8
   / \
  6   5
 /\   /\
9  4  3 7

arr = [8,6,5,9,4,3,7]
```

### perfect binary array representation case
```
    8
   / \
  6   5
 /\   /\
9    3  7
 
arr = [8,6,5,9, ,3,7]   // write all null values
```

### complete binary tree array representation

```
    8
   / \
  6   5
 /\   /\
9    
 
arr = [8,6,5,9, , , ]   // write all null values in the last 
```

### Advantages of Array Representation of Binary Tree

* Stored in **contiguous memory** → cache-friendly, faster access
* **No pointers required** → saves memory
* Allows **direct/random access** to nodes using index

### Limitations of Array Representation of Binary Tree

* Requires **contiguous memory** → not suitable for large trees
* **Insertion & deletion are costly** (array shifting needed)
* Many **NULL entries** in sparse trees → poor space utilization


## linked representation
_________________________________________________________________
| address of eft child |    data       |  address of right child |
__________________________________________________________________


### Advantages of Linked Representation of Binary Tree

* Tree can **grow or shrink dynamically** (uses only required memory)
* **Insertion and deletion are easy** (only pointer changes)
* **Efficient for sparse trees** (no wasted space for NULL nodes)

### Disadvantages of Linked Representation of Binary Tree

* Requires **extra memory for pointers**
* **Access/search is slower** (must start from root and traverse)


## binary tree traversal

### Binary Tree Traversals — **Short Notes**

**Binary Tree Traversal**
Process of visiting **all nodes** of a binary tree in a specific order.

**Types (3):**

1. **Pre-Order** → **Roo**t → Left → Right
2. **In-Order** →  Left → **Root** → Right
3. **Post-Order** → Left → Right → **Root**

---

### Traversal Orders 

#### 1️⃣ Pre-Order Traversal (R – L – R)

```
A – B – D – I – J – F – C – G – K – H
```

#### 2️⃣ In-Order Traversal (L – R – R)

```
I – D – J – B – F – A – G – K – C – H
```

#### 3️⃣ Post-Order Traversal (L – R – R)

```
I – J – D – F – B – K – G – H – C – A
```


