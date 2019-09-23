# Construct Binary Tree from Preorder and Inorder Traversal
Draft Java solution:
```
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        ...
    }
```
FAILED.

Passing solution (DFS):
```
public TreeNode buildTree(int[] preorder, int[] inorder){
    return util(preorder, inorder, 0, inorder.length - 1, 0, inorder.length - 1);
}

private TreeNode util(int[] preorder, int[] inorder, int s1, int e1, int s2, int e2){
    if(s1 > e1 || s2 > e2){
        return null;
    }
    TreeNode root = new TreeNode(preorder[s1]);
    int rootIndex = Integer.MIN_VALUE;
    for(int i = s2; i <= e2; ++ i){
        if(inorder[i] == root.val){
            rootIndex = i;
        }
    }
    //handle incomplete tree
    if(rootIndex == Integer.MIN_VALUE){
        return null;
    }
    int leftSubtreeSize = rootIndex - s2;
    int rightSubtreeSize = e2 - rootIndex;
    root.left = util(preorder, inorder, s1 + 1, s1 + leftSubtreeSize, s2, rootIndex - 1);
    root.right = util(preorder, inorder, e1 - rightSubtreeSize + 1, e1, rootIndex + 1, e2);
    return root;
}
``` 