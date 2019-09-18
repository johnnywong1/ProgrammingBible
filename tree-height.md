# Tree: Height of a Binary Tree

### Function Description
Complete the getHeight or height function in the editor. It must return the height of a binary tree as an integer.

getHeight or height has the following parameter(s):
* root: a reference to the root of a binary tree
** Note: The Height of binary tree with single node is taken as zero

`
def height(root):
    if(root.left is None and root.right is None):
        return 0
    else:
        left = 1; right = 1
        if(root.left is not None):
            left = left + height(root.left)
        if(root.right is not None):
            right = right + height(root.right)
        return max(left, right)
`
