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
### Iterative approach (with one stack)
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
### Iterative approach (with one stack)
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
### Iterative approach (with two stacks)
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


