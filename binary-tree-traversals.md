 # Binary Tree Traversals
## Inorder travesal: left -> root -> right
### Recursive approach
```
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList();
        inorder(result, root);
        return result;
    }

    private void inorder(List<Integer> result, TreeNode root){
        if(root == null){
            return;
        }else{
            inorder(result, root.left);
            result.add(root.val);
            inorder(result, root.right);
        }
    }
```
### Iterative approach (single stack)
```
    public List<Integer> inorderTraversal(TreeNode root){
        List<Integer> result = new ArrayList();
        Stack<TreeNode> stack = new Stack();
        TreeNode curr = root;
        
        while(curr != null || !stack.isEmpty()){
            while(curr != null){
                stack.push(curr);
                curr = curr.left;
            }
            curr = stack.pop();
            result.add(curr.val);
            curr = curr.right;
        }
        return result;
    }
```

## Preorder traversal: root -> left -> right
### Recursive approach
```
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList();
        preorder(result, root);
        return result;
    }

    private void preorder(List<Integer> result, TreeNode root){
        if(root == null){
            return;
        }else{
            result.add(root.val);
            preorder(result, root.left);
            preorder(result, root.right);
        }
    }
```
### Iterative approach (single stack)
```
    public List<Integer> preorderTraversal(TreeNode root){

        List<Integer> result = new ArrayList();

        if(root == null){
            return result;
        }

        Stack<TreeNode> stack = new Stack();
        stack.push(root);
        while(!stack.isEmpty()){
            TreeNode curr = stack.pop();
            result.add(curr.val);
            if(curr.right != null){
                stack.push(curr.right);
            }
            if(curr.left != null){
                stack.push(curr.left);
            }
        }
        return result;
    }
```

## Postorder traversal: left -> right -> root
### Recursive approach
```
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList();
        postorder(result, root);
        return result;
    }   

    private void postorder(List<Integer> result, TreeNode root){
        if(root == null){
            return;
        }else{
            postorder(result, root.left);
            postorder(result, root.right);
            result.add(root.val);
        }
    }
```
### Iterative approach (dual stack)
```
    public List<Integer> postorderTraversal(TreeNode root){
        List<Integer> result = new ArrayList();
        if(root == null){
            return result;
        }
        Stack<TreeNode> s1 = new Stack();
        Stack<TreeNode> s2 = new Stack();
        s1.push(root);
        while(!s1.isEmpty()){
            TreeNode curr = s1.pop();
            s2.push(curr);
            if(curr.left != null){
                s1.push(curr.left);
            }
            if(curr.right != null){
                s1.push(curr.right);
            }
        }
        while(!s2.isEmpty()){
            result.add(s2.pop().val);
        }
        return result;
    }
```

## Level order traversal: level by level
### Iterative approach (dual queue)
```
    public List<List<Integer>> levelOrder(TreeNode root) {
        //dual queue approach
        List<List<Integer>> result = new ArrayList();
        if(root == null){
            return result;
        }
        LinkedList<TreeNode> q1 = new LinkedList();
        LinkedList<TreeNode> q2 = new LinkedList();
        List<Integer> temp = new ArrayList();
        q1.add(root);
        while(!q1.isEmpty()){
            TreeNode curr = q1.pop();
            temp.add(curr.val);
            if(curr.left != null){
                q2.add(curr.left);
            }
            if(curr.right != null){
                q2.add(curr.right);
            }
            if(q1.isEmpty()){
                result.add(new ArrayList(temp));
                temp.clear();
                q1.clear();
                for(TreeNode node : q2){
                    q1.add(node);
                }
                q2.clear();
            }
        }
        return result;
    }
```
### Iterative approach (single queue - potentially bad logic)
```
    public List<List<Integer>> levelOrder(TreeNode root){
        List<List<Integer>> result = new ArrayList();
        if(root == null){
            return result;
        }
        LinkedList<TreeNode> queue = new LinkedList();
        queue.add(root);
        while(true){
            int cnt = queue.size();
            List<Integer> temp = new ArrayList();
            if(cnt == 0){
                break;
            }
            while(cnt > 0){
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
            result.add(new ArrayList(temp));
            temp.clear();
        }
        return result;
    }
```
