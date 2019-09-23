# Convert Sorted Array to Binary Search Tree
Draft Java solution:
```
    public TreeNode sortedArrayToBST(int[] nums) {
        return util(nums, 0, nums.length - 1);
    }

    private TreeNode util(int[] nums, int left, int right){
        if(left > right){
            return null;
        }
        int mid = left + (right - left) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = util(nums, left, mid - 1);
        root.right = util(nums, mid + 1, right);
        return root;
    }
```
PASSED with 1 attempt