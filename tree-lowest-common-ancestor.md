# Binary Search Tree: Lowest Common Ancestor

### Problem
You are given pointer to the root of the binary search tree and two values ***v1*** and ***v2***. You need to return the lowest common ancestor (LCA) of ***v1*** and ***v2*** in the binary search tree.

### Constraints
v1 != v2
v1 and v2 exist

### Function Description
Complete the function Lca in the editor below. It should return a pointer to the lowest common ancestor node of the two values given.

Lca has the following parameters:
* root: a pointer to the root node of a binary search tree
* v1: a node.data value
* v2: a node.data value

```
def lca(root, v1, v2):
    if(root.info is None):
        return None

    if(v1 < root.info and v2 < root.info):
        return lca(root.left, v1, v2)
    if(v1 > root.info and v2 > root.info):
        return lca(root.right, v1, v2)

    return root
```
