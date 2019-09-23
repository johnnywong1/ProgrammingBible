# Lowest Common Ancestor of a Binary Tree
Draft Java solution:
```
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        //search in both left and right subtree, return to parent if matched
        if(root == null){
            return null;
        }
        if(root.val == q.val || root.val == p.val){
            return root;
        }
        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);
        if(left == null && right == null){
            return null;    //leaf level reached
        }
        if(left != null && right != null){
            return root;    //found LCA
        }
        if(left != null){
            return left;
        }else{
            return right;   //return the not-null
        }
    }
```
PASSED with 1 attempt

https://www.youtube.com/watch?v=13m9ZCB8gjw