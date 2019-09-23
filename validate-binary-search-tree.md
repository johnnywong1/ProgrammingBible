# Validate Binary Search Tree
Draft Java solution:
```
    public boolean isValidBST(TreeNode root) {
        //range of node value approach
        return util(root, null, null);
    }

    private boolean util(TreeNode root, Integer low, Integer high){
        if(root == null){
            return true;
        }
        if(low != null && root.val <= low){
            return false;
        }
        if(high != null && root.val >= high){
            return false;
        }
        return util(root.left, low, root.val) && util(root.right, root.val, high);
    }
```
PASSED with 9 attempts.

Note: initialize `low` and `high` to `null` to bypass edge case testing; use `Integer` type for `low` and `high` to achieve so. 