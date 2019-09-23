# Lowest Common Ancestor of a Binary Search Tree
Draft Java solution:
```
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root.val >= Math.min(p.val, q.val) && root.val <= Math.max(p.val, q.val)){
            return root;
        }else if(root.val > Math.max(p.val, q.val)){
            return lowestCommonAncestor(root.left, p, q);
        }else{
            return lowestCommonAncestor(root.right, p, q);
        }
    }
```
PASSED with 1 attempt. 