# Path Sum
Draft Java solution:
```
    public boolean hasPathSum(TreeNode root, int sum) {
        //must be root-to-leaf
        return util(root, 0, sum);
    }

    private boolean util(TreeNode root, int currSum, int sum){
        if(root == null){
            return false;
        }
        if(currSum == sum){
            return true;
        }
        return util(root.left, currSum + root.val, sum) || util(root.right, currSum + root.val, sum);
    }
```
FAILED.

Passing solution:
```
    public boolean hasPathSum(TreeNode root, int sum){
        if(root == null){
            return false;
        }
        if(root.left == null && root.right == null){
            if(sum - root.val == 0){
                return true;
            }else{
                return false;
            }
        }
        return hasPathSum(root.left, sum - root.val) || hasPathSum(root.right, sum - root.val);
    }
```
PASSED with 2 attempt.

https://www.youtube.com/watch?v=Jg4E4KZstFE