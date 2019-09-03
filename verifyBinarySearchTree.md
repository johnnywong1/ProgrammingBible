# Verify Binary Search Tree
```
https://www.hackerrank.com/challenges/is-binary-search-tree/problem
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

