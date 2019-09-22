# Binary Subtree Sum Equals to K
Draft Java solution:
```
    public static class pair{
        int cnt;
        int sum;
        public pair(int cnt, int sum){
            this.cnt = cnt;
            this.sum = sum;
        }
    }

    public static pair subSumEqualsK(TreeNode root, int k){
        //post order approach
        return util(root, k);
    }

    private static pair util(TreeNode root, int k){
        if(root == null){
            return new pair(0, 0);
        }
        System.out.println("root.val: " + root.val);
        pair left = util(root.left, k);
        System.out.println("left.sum: " + left.sum);
        pair right = util(root.right, k);
        System.out.println("right.sum: " + right.sum);
        int curr = left.sum + right.sum + root.val;
        System.out.println(curr);
        int cnt = left.cnt + right.cnt;
        if(curr == k){
            System.out.println("A matching sum is found!");
            ++ cnt;
        }
        return new pair(cnt, curr);
    }
```

Note: use custom class `pair` to store intermediate computing result `curr`