# tree 

## INDEX 
- [basic](#basic)
- [height and depth](#height-and-depth)
- [binary tree](#binary-tree)
- [binary search tree](#binary-search-tree)
- [avl](#avl)
- [b tree](#b-tree)
- [threaded binary tree](#threaded-binary-tree)
- [huffman coding](#huffman-coding)
- [non recursive post order traversal](#non-recursive-post-order-traversal)
- [path lenth](#path-length)


## basic 

* non - linear data structure
* organize data in hierarchical structure
* individual element is called node
* node stores the actual data , and link to next element
* N number of nodes have maximunum (N-1) number of links 

<img width="563" height="335" alt="image" src="https://github.com/user-attachments/assets/70b9ee06-0f82-4242-a701-6c82a61df99c" />

### height and depth 
In a tree data structure, height and depth are related but different concepts.

```
1. Height
Definition: The height of a node is the number of edges on the longest path from that node to a leaf.
Leaf node: Height = 0.
Height of tree: Height of the root node.
Formula:
Height(node)=1+max⁡(Height(leftChild),Height(rightChild))\text{Height}(node) = 1 + \max(\text{Height}(leftChild), \text{Height}(rightChild))Height(node)=1+max(Height(leftChild),Height(rightChild))

Example:    A
           / \
          B   C
         / \
        D   E

Height(D) = 0
Height(B) = 1
Height(A) = 2

```

```
2. Depth
Definition: The depth of a node is the number of edges from the root to that node.
Root node: Depth = 0.
Formula:
Depth(node)=Depth(parent)+1\text{Depth}(node) = \text{Depth}(parent) + 1Depth(node)=Depth(parent)+1

Example:    A (depth 0)
           / \
          B   C
         / \
        D   E

Depth(A) = 0
Depth(B) = 1
Depth(D) = 2

```

##### binary tree 

## 🌳 Binary Tree 

- [definition](#Definition)
- [types](#types)
- [extended binary tree](#extended-binary-tree)
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

##### types
---
### 🌳 Types of Binary Tree 



1️⃣ **Full/strict Binary Tree**
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
→ Height difference of left & right subtree **1 , -1, 0**

7️⃣ **Binary Search Tree (BST)**
→ Left < Root < Right

```
FULL        COMPLETE        PERFECT        DEGENERATE        LEFT SKEWED     RIGHT SKEWED     BALANCED        BST
  o            o               o               o                 o               o               o               5
 / \          / \             / \               \               /                 \             / \             / \
o   o        o   o           o   o               o             o                   o           o   o           3   7
            /               /\   /\               \           /                     \         / \             / \  
           o               o  o o  o               o         o                       o       o   o           2   4
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

* Max nodes = **[2^(h+1) ]− 1**
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

**6. Minimum no. of leaf nodes of a binary tree with `T` internal nodes**

* min no. of leaf nodes : **L = T + 1**

  
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

---

### 📊 Array Representation of Binary Tree

| **Property**         | **Case 1: Index Starts with 1** | **Case 2: Index Starts with 0** |
| -------------------- | ------------------------------- | ------------------------------- |
| **Root Index**       | `1`                             | `0`                             |
| **Parent of i**      | ⌊ `i / 2` ⌋                     | ⌊ `(i − 1) / 2` ⌋               |
| **Left Child of i**  | `2i`                            | `2i + 1`                        |
| **Right Child of i** | `2i + 1`                        | `2i + 2`                        |

---


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
| address of Left child |    data       |  address of right child |
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
<img width="189" height="127" alt="image" src="https://github.com/user-attachments/assets/8e2d3919-31ad-4f64-bb9e-7184edd10a5b" />

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


## binary search tree 

* smaller value are on left
* grater value are on the right
* in order is always in increaing order

> Unique ordering of elements means duplicates are usually not allowed.
> In-order traversal of a BST gives sorted order of elements.
> Average height: O(log n) (for balanced BST).
> Worst case height: O(n) (when tree becomes skewed).

### BST operation 
1. search
2. insert
3. delete

### 🧮  BST Search Operation 

#### **What is BST Search?**

* Always start from **root**.
* If **key < node**, go to **left subtree**.
* If **key > node**, go to **right subtree**.
* If **key == node**, **found**.
* If you reach **NULL**, element **not present**.

---

### **Example**

**Search key = 10**

Steps:

1. Start at root **12**
   → `10 < 12` → go **left**
2. At node **7**
   → `10 > 7` → go **right**
3. At node **9**
   → `10 > 9` → go **right**
4. At node **10**
   → `10 == 10` → **FOUND**

✔️ Result: **10 is present in BST**

---

### **BST Search – Recursive (Steps format)**

```
Search(x, k)
1. if x == NULL or x.key == k → return x
2. if k < x.key → Search(x.left, k)
3. else → Search(x.right, k)
```

---

### **BST Search – Iterative (Steps format)**

```
Search(x, k)
1. while x ≠ NULL and x.key ≠ k
2.   if k < x.key → x = x.left
3.   else → x = x.right
4. return x
```

---

**Time Complexity**
* **Best / Average:** O(log N)
* **Worst (skewed tree):** O(N)

Here’s a concise breakdown of the **BST Insert Operation** along with clean pseudocode:

---

### 🧮 BST Insert Operation

- **Start with an empty tree.**
- Insert nodes one by one.
- For each node:
  - Compare with current node.
  - If smaller → go to left subtree.
  - If greater → go to right subtree.
  - Repeat until you find an empty spot.
- Insert the new node at that position.

**Example Sequence:**  
Insert → 12, 7, 9, 19, 5, 10  
Final structure:
```
        12
       /  \
     7     19
    / \
   5   9
         \
         10
```

---

#### Pseudocode: BST Insert

```plaintext
TreeInsert(T, z)  // T is the tree, z is the node to insert
{
    y = NIL       // y tracks the parent of x
    x = root[T]   // Start from the root

    while x ≠ NIL do
    {
        y = x
        if key[z] < key[x]
            x = left[x]
        else
            x = right[x]
    }

    p[z] = y       // Set parent of z

    if y = NIL
        root[T] = z        // Tree was empty
    else if key[z] < key[y]
        left[y] = z        // Insert as left child
    else
        right[y] = z       // Insert as right child
}
```

---

### 🧮 BST Delete Operation 

- **Case 1: Node with No Children (Leaf Node)**
  - Simply remove the node.
  - No structural changes needed.

- **Case 2: Node with One Child**
  - Remove the node.
  - Connect its child directly to the node’s parent.

- **Case 3: Node with Two Children**
  - Replace the node with either:
    - **Inorder Predecessor**: Largest value in left subtree.
    - **Inorder Successor**: Smallest value in right subtree.
  - Then delete the predecessor/successor node (which will now be Case 1 or 2).
<img width="667" height="265" alt="image" src="https://github.com/user-attachments/assets/33bf3447-d0e3-4579-ab60-fe21672364e8" />

---

---

#### BST Delete Operation – Pseudocode

```plaintext
TreeDelete(T, z)  // T is the tree, z is the node to delete
1. if z.left == NIL or z.right == NIL
2.     y = z                      // y is the node to be removed
3. else
4.     y = TreeSuccessor(z)      // y is z's successor
5. if y.left == NIL
6.     x = y.right               // x is y's child
7. else
8.     x = y.left
9. if x ≠ NIL
10.    x.parent = y.parent       // update x's parent
11. if y.parent == NIL
12.    T.root = x                // x becomes new root
13. else if y == y.parent.left
14.    y.parent.left = x         // x replaces y on left
15. else
16.    y.parent.right = x        // x replaces y on right
17. if y ≠ z
18.    z.key = y.key             // copy y's key to z
19.    copy y's satellite data into z

20. return y                     // return deleted node
```

---
---

### 📊 BST Time & Space Complexities

| Operation | Best Case | Average Case | Worst Case |
|-----------|-----------|--------------|------------|
| Search    | O(log n)  | O(log n)     | O(n)       |
| Insertion | O(log n)  | O(log n)     | O(n)       |
| Deletion  | O(log n)  | O(log n)     | O(n)       |

**Space Complexity:**  
- All operations: **O(n)**

---

### 🔍 BST vs Array vs Linked List

| Data Structure     | Search Time   | Shifting Needed on Insert/Delete |
|--------------------|---------------|----------------------------------|
| Sorted Array       | O(log n) ✓    | Yes ✓                            |
| Linked List        | O(n) ✓        | No ✓                             |
| Binary Search Tree | O(log n) ✓    | No ✓                             |

---


### 📊 BST balance & time Complexities

* height of each binary tree is +1/-1/0
* time complexity = O(log N)

<img width="174" height="160" alt="image" src="https://github.com/user-attachments/assets/61992294-b236-4ed8-b74c-a12599941693" />


#### Practical Applications of BST:
1. Databases: Many database systems use BSTs for indexing data, which allows for fast
retrieval of records based on keys.
2. Symbol Tables: Compilers and interpreters use BSTs to store and search for identifiers (e.g.,
variable names) efficiently.
3. File Systems: BSTs are employed in file systems to organize directory structures and quickly
locate files.
4. Caches: In computer architecture, BSTs are used in caches to efficiently manage and search for cached data.
5. Network Routing: Routing tables in network routers often use BSTs for efficient routing
decisions.

###### avl 

## 📊 AVL tree 
---
* for some unbalanced tree to make it balance
* to make time complexity O(log N)

**AVL Tree Balance Factor**:

- **Balance Factor (BF)** = height of left subtree − height of right subtree 
- A node is **balanced** if BF is between −1 and +1; outside this range means **rotation is needed**.

---

### 🌳 AVL Tree Rotation 

- **Purpose**: Restore balance in AVL trees when nodes become unbalanced.
- **Balance Factor**: Difference between heights of left and right subtrees.
- **Rotation Time**: O(1) per rotation; overall operations remain O(log n).

---
---

### 🌳 AVL Tree Rotations 

| Rotation Type | Trigger Condition                                      | Steps Involved       | Resulting Root |
|---------------|--------------------------------------------------------|----------------------|----------------|
| **LL Rotation** | Insertion in left subtree of left child                | Single Right Rotation | Middle node     |
| **RR Rotation** | Insertion in right subtree of right child              | Single Left Rotation  | Middle node     |
| **LR Rotation** | Insertion in right subtree of left child               | RR + LL (Double Rotation) | Middle node     |
| **RL Rotation** | Insertion in left subtree of right child               | LL + RR (Double Rotation) | Middle node     |

---

### 🧠 Rotation Examples

- **LL**: Insert 10 → 30 → 20 → imbalance at 30 → rotate right → root becomes 20  
- **RR**: Insert 10 → 20 → 30 → imbalance at 10 → rotate left → root becomes 20  
- **LR**: Insert 30 → 10 → 20 → imbalance at 30 → RR on 10 → LL on 30 → root becomes 20  
- **RL**: Insert 10 → 30 → 20 → imbalance at 10 → LL on 30 → RR on 10 → root becomes 20

---
```

UNBALANCED

LL                     RR                   LR                 RL 
   10                      10               30                10
    \                     /                 /                  \
     20                 20                10                    30
       \               /                   \                    /
       30            30                     20                 20

BALANCED

     20                     
    /  \                  
  10   30

```
---

### 🗑️ AVL Tree Deletion – 3 Cases

| Case | Description | Action |
|------|-------------|--------|
| **1. Leaf Node** | Node has no children | Delete directly; apply rotation if needed |
| **2. One Child** | Node has one child | Replace with child; delete child; rebalance if needed |
| **3. Two Children** | Node has two children | Replace with inorder successor; delete successor; rebalance if needed |

---

### ✅ AVL Tree Advantages over BST

| Advantage | Description |
|-----------|-------------|
| **Balanced Height** | Ensures O(log n) for search, insert, delete |
| **Guaranteed Performance** | Predictable time complexity for all operations |
| **Optimized for Search** | Fewer comparisons due to balanced structure |
| **Real-time Suitability** | Ideal for systems needing consistent performance |

**Disadvantage**: Slight overhead due to rebalancing after insert/delete.

---
         
 ##### b tree

 ## 🌳 B TREE

- A **self-balanced M-way search tree** with multiple keys and children per node.
- All **leaf nodes are at the same level**.
- Grows and shrinks from the **root**, unlike BSTs which grow downward.
- Time complexity for **search, insert, delete**: **O(log n)**.

---

### 📐 B-Tree Properties

| Property                          | Rule (Order M)                     |
|----------------------------------|------------------------------------|
| Max keys per node                | M − 1                              |
| Min keys (except root)           | ceil(M/2) − 1                      |
| Max children per internal node   | M                                  |
| Min children (except root)       | ceil(M/2)                          |
| Root min children (if internal)  | 2                                  |
| Keys in node                     | Must be in **ascending order**     |

---

### 🔁 B-Tree vs Minimum Degree (t)

| Metric               | In terms of M | In terms of t |
|----------------------|---------------|---------------|
| Max keys             | M − 1         | 2t − 1        |
| Max children         | M             | 2t            |
| Min keys (non-root)  | ceil(M/2) − 1 | t − 1         |
| Min children         | ceil(M/2)     | t             |
| Root min children    | 2             | 2             |

---

<img width="607" height="301" alt="image" src="https://github.com/user-attachments/assets/39c78a23-f0e4-4749-97dc-25ac705414c5" />

## insertion 
* alaways insertion happens at the leaf node
* To insert a new key,
* we go down from root to leaf.
* add upto m-1 no. of keys
* on mth key insrtion split the leaf node from the middle element


## deletion 
1. from leaf node 
**case 1.** if leaf node contaion **more than min no.**(ceil(M/2) − 1) of trees - delete **directly**
**case 2.** if leaf node contaion **min no.** - **borow** from adjacent leaf node
in here the closest parent node comes down and the largest or smallest node gets on the parent depending on weither the node is on right or left respectively
**case 2.** if **both** the adjacent leaf node also have min no. of keys then the parent node comes and **merges** with the adjacent node.

2. from internal node
* look for the attach leaf node
* **case 1.** - attached leaf node has more than min no. nodes
* from the right replace with the smallest value
* from the left take the largest value 
* **case 2.** - attached leaf node has min no. nodes
* merge the attached leaf node with the node
* root node comes if it is the closest i this carefully rearange acording to bonary tree
* if both adjacent root and leaf node has min no of keys same level of adjacent node merges
* **case 3.** root not deletion
* either one of in order predecer or in order succesor takes place of root

### 🌳 Comparison of Binary Tree, BST, and AVL Tree

| Feature                     | Binary Tree                      | Binary Search Tree (BST)                          | AVL Tree                                      |
|----------------------------|----------------------------------|--------------------------------------------------|-----------------------------------------------|
| **Structure**              | Each node has ≤ 2 children       | Binary tree with ordered keys                    | Self-balancing BST with strict balance factor |
| **Ordering Rule**          | No specific order                | Left < Root < Right                              | Same as BST                                   |
| **Balancing**              | Not balanced                     | Not guaranteed                                   | Always balanced (BF ∈ {−1, 0, +1})            |
| **Search Time**            | O(n)                             | O(log n) average, O(n) worst                     | O(log n) guaranteed                           |
| **Insert/Delete Time**     | O(n)                             | O(log n) average, O(n) worst                     | O(log n) guaranteed                           |
| **Rotations**              | Not applicable                   | Not applicable                                   | Required to maintain balance                  |
| **Space Complexity**       | O(n)                             | O(n)                                             | O(n)                                           |
| **Use Case**               | Simple hierarchical data         | Ordered data with moderate performance needs     | Real-time systems, fast and predictable access|

---

### 🔍 Key Insights

- **Binary Tree** is a general structure with no ordering or balancing — useful for hierarchical data but inefficient for search.
- **BST** improves search by ordering nodes, but can degrade to a linked list if unbalanced.
- **AVL Tree** maintains strict balance using rotations, ensuring consistently fast operations.

---

##### threaded binary tree

## 🧵 Threaded Binary Tree 

- Designed to optimize **inorder traversal** without recursion or stack.
- **Right NULL pointers** are replaced with links to the **inorder successor**.
- Each node stores:
  - **Left field** → left thread or child
  - **Right field** → right thread or child
  - **Middle field** → actual data
- Improves traversal speed and reduces memory overhead.

---
### single threaded 

<img width="560" height="202" alt="image" src="https://github.com/user-attachments/assets/b22d262b-9617-4f53-9442-90faeeb91131" />

---

### double threaded

<img width="600" height="250" alt="image" src="https://github.com/user-attachments/assets/f9b472d4-66bb-44cf-9162-7ad62f3cd9a7" />

---

### modified advanced
<img width="520" height="584" alt="image" src="https://github.com/user-attachments/assets/7c8cb033-c3c0-4da0-8b70-14420e48972c" />

###### huffman coding 
---

### 🗜️ Huffman Coding – Full Notes

#### 📌 What is Huffman Coding?
- A **lossless data compression algorithm**.
- Compresses data by assigning **variable-length codes** to characters based on frequency.
- Frequently occurring characters get **shorter codes**, reducing overall size.

#### 🧠 Key Properties
- No code is a **prefix** of another → ensures **unambiguous decoding**.
- Two main steps:
  1. **Build Huffman Tree** using character frequencies.
  2. **Traverse the tree** to assign binary codes to each character.

#### 📊 Example 1:  
- String: `"BCAADDDCCACACAC"`  
- Original size: 15 characters × 8 bits = **120 bits**  
- Huffman coding reduces size by using shorter codes for frequent characters.

#### 🧪 Example 2:  
- Message: `"ABBCDBCCDAABBBEEEBA"`  
- Character frequencies:
  - A: 4  
  - B: 7  
  - C: 3  
  - D: 3  
  - E: 4  
- Start building Huffman Tree by combining **lowest frequency characters** (C and D).

---
---

### 🧮 Huffman Algorithm – Steps

1. **Create a priority queue (Q)** of unique characters.
2. **Sort Q** in ascending order of frequency.
3. **Repeat until one node remains**:
   - Create a new node.
   - Extract two minimum-frequency nodes from Q.
   - Assign them as left and right children of the new node.
   - Set new node’s frequency = sum of both.
   - Insert new node back into Q.
4. **Return the root node** of the final Huffman Tree.

---

### 🌳 Role of Binary Tree in Huffman Coding

| Benefit              | Description |
|----------------------|-------------|
| **Efficient Encoding** | Frequent characters get shorter codes via tree structure |
| **Prefix Codes**       | No code is a prefix of another → ensures unambiguous decoding |
| **Optimal Compression**| Tree ensures minimal average code length |
| **Fast Traversal**     | Tree enables quick encoding and decoding |

---


###### non recursive post order traversal 
---

### 🔁 Non-Recursive Postorder Traversal – Concept

- **Postorder Traversal**: Left → Right → Root  
- Normally done using recursion or stack  
- This method uses **two stacks (S1 and S2)** to simulate postorder traversal iteratively

---

### 🧮 Algorithm Steps

1. **Initialize two stacks**: `S1` and `S2`
2. **Push root** to `S1`
3. **While `S1` is not empty**:
   - Pop from `S1`, push to `S2`
   - Push left child to `S1` (if exists)
   - Push right child to `S1` (if exists)
4. **Print contents of `S2`** → gives postorder traversal

---

### 🧑‍💻 C Code Snippet

```c
void postOrderIterative(struct Node* root) {
    if (root == NULL) return;
    struct StackNode *s1 = NULL, *s2 = NULL;
    push(&s1, root);

    while (!isEmpty(s1)) {
        struct Node *temp = pop(&s1);
        push(&s2, temp);
        if (temp->left) push(&s1, temp->left);
        if (temp->right) push(&s1, temp->right);
    }

    while (!isEmpty(s2)) {
        struct Node *temp = pop(&s2);
        printf("%d ", temp->data);
    }
}
```

---

### 🌳 Example Tree

```
        A
       / \
      B   C
     / \   \
    D   E   F
             \
              G
```

**Postorder Output**: `D E B G F C A`

---

### path length

<img width="893" height="451" alt="image" src="https://github.com/user-attachments/assets/49ef9b06-a4ed-4cc0-8175-a1d39eb17299" />



Let me know if you'd like this visualized or converted to Python or Java next!

