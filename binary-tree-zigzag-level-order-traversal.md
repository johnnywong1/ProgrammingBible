# Binary Tree Zigzag Level Order Traversal
Draft Java solution:
```
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        //one queue attempt
        List<List<Integer>> result = new ArrayList();
        if(root == null){
            return result;
        }
        LinkedList<TreeNode> queue = new LinkedList();
        queue.add(root);
        boolean leftToRight = true;
        while(true){
            int cnt = queue.size();
            List<Integer> temp = new ArrayList();
            if(cnt == 0){
                break;  //touched leaf
            }
            while(cnt != 0){
                TreeNode curr = queue.pop();
                temp.add(curr.val);
                if(curr.left != null){
                    queue.add(curr.left);
                }
                if(curr.right != null){
                    queue.add(curr.right);
                }
                -- cnt;
            }
            if(!leftToRight){
                Collections.reverse(temp);
                result.add(new ArrayList(temp));
            }else{
                result.add(new ArrayList(temp));
            }
            temp.clear();
            leftToRight = !leftToRight;
        }
        return result;
    }
```
PASSED with 2 attempts. 