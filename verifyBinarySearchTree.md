# Verify Binary Search Tree
```
https://www.hackerrank.com/challenges/is-binary-search-tree/problem
```
For the purposes of this challenge, we define a binary tree to be a binary search tree with the following ordering requirements:
* The **data** value of every node in a node's left subtree is less than the data value of that node.
* Thev **data** alue of every node in a node's right subtree is greater than the data value of that node.
Given the root node of a binary tree, can you determine if it's also a binary search tree? 

Complete the function in your editor below, which has parameter: a pointer to the root of a binary tree. It must return a boolean denoting whether or not the binary tree is a binary search tree. You may have to write one or more helper functions to complete this challenge.

```
      3
  5       2
1   4    6

# Results in False
```


```
""" Node is defined as
class node:
  def __init__(self, data):
      self.data = data
      self.left = None
      self.right = None
"""
```


## Standard Recursion

```
MIN_VALUE = 0
MAX_VALUE = 10**4
def check_binary_search_tree_(root):
    return helperFn(root, MIN_VALUE, MAX_VALUE)

def helperFn(root, MIN, MAX):
    if root == None:
        return True
    elif (root.data >= MAX) or (root.data <= MIN):
        return False
    return helperFn(root.left, MIN, root.data) and helperFn(root.right, root.data, MAX)
```
## Voodoo InOrder Method
```
MIN_VALUE = 0
MAX_VALUE = 10**4
def check_binary_search_tree_(root):
    def inorder(tree):
        if tree is None: return []
        return inorder(tree.left) + [tree.data] + inorder(tree.right)
    def is_sorted(lst):
        return all((lst[i] < lst[i+1]) for i in range(len(lst)-1))
    return is_sorted(inorder(root))
```

