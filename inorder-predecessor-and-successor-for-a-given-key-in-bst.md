# Inorder Prodecessor and Successor for a Given Key in BST

## Inorder successor for a given key
Draft Java solution:
```
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        //inorder traversal approach
        List<TreeNode> nodes = new ArrayList();
        util(root, nodes);
        for(int i = 0; i < nodes.size(); ++ i){
            if(i < nodes.size() - 1 && nodes.get(i).val == p.val){
                return nodes.get(i + 1);
            }
        }
        return null;
    }

    private void util(TreeNode root, List<TreeNode> nodes){
        if(root == null){
            return;
        }else{
            util(root.left, nodes);
            nodes.add(root);
            util(root.right, nodes);
        }
    }
```
PASSED with 2 attemps.

More efficient solution (iterative inorder traversal with single stack):
```
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p){
        Stack<TreeNode> stack = new Stack();
        List<TreeNode> temp = new ArrayList();
        TreeNode curr = root;
        while(!stack.isEmpty() || curr != null){
            while(curr != null){
                stack.push(curr);
                curr = curr.left;
            }
            curr = stack.pop();
            if(temp.size() >= 1 && temp.get(temp.size() - 1).val == p.val){
                return curr;
            }
            temp.add(curr);
            curr = curr.right;
        }
        return null;    //no successor found in tree
    }
```
Further optimization: use single `TreeNode` to keep track of `temp.get(temp.size() - 1)`

Same method for finding predecessor