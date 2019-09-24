# Path Sum II
Draft Java solution:
```
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        //return all sum routes, must be root-to-leaf
        List<List<Integer>> result = new ArrayList();
        List<Integer> temp = new ArrayList();
        util(temp, result, root, sum);
        return result;
    }

    private void util(List<Integer> temp, List<List<Integer>> result, TreeNode root, int sum){
        if(root == null){
            return;
        }
        temp.add(root.val);
        if(root.left == null && root.right == null){
            if(sum == root.val){
                result.add(new ArrayList(temp));
            }
        }
        util(temp, result, root.left, sum - root.val);
        util(temp, result, root.right, sum - root.val);
        temp.remove(temp.size() - 1);
    }
```
PASSED with 10 attempts. 

https://www.cnblogs.com/grandyang/p/4042156.html