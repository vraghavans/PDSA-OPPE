# Q008 — Leaf Nodes in a Binary Search Tree

## Student Question

Binary Search Tree Operation

class Node:
    def __init_ (self, data):
        self.left = None # Contains reference to the left child node if it exists, otherwise None
        self.data = data # Stores data
        self.right = None # Contains reference to the right child node if it exists, otherwise None

Consider an implementation of a Binary Search Tree, where each node is created using the given class Node. 
Suppose it has a root variable that contains the reference to the root node of the binary search tree.
Write a function leaf_nodes(root) that accepts the reference of root node root of a non-empty binary search tree
and returns a list containing the data present in all the leaf nodes of the tree, sorted in ascending order.

Sample input 1
105 18 8 3 15 25 17

Note:- Binary search tree is created using the hidden suffix code for a given order of elements in the input, and the reference of the root node is passed to the function leaf_nodes as a
parameter. You need to work on a binary search tree using the reference of the root node.

### Student Function

Implement the following function:

```python
def leaf_nodes(root):
```

## Full Reference Code

```python
def leaf_nodes(root):
    leaf_values = []

    def in_order_traversal(node):
        if node:
            in_order_traversal(node.left)
            if node.left is None and node.right is None:
                leaf_values.append(node.data)
            in_order_traversal(node.right)

    in_order_traversal(root)
    return leaf_values
```

## Source / Occurrence Metadata

- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/BinarySearchTreeOperation.py`
- Occurrences currently confirmed: 1; final occurrence count must be updated after the complete OPPE1/OPPE2/OPPE3 repository scan.
- Deduplication note: checked against existing deduplicated questions; no duplicate found.
