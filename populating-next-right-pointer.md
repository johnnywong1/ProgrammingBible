# Populating Next Right Pointer
Draft Java solution:
```
    public Node connect(Node root) {
        //perfect binary tree
        //level order traversal approach
        LinkedList<Node> queue = new LinkedList();
        queue.add(root);
        while(true){
            int cnt = queue.size();
            List<Node> temp = new ArrayList();
            if(cnt == 0){
                break;
            }
            while(cnt > 0){
                Node curr = queue.pop();
                temp.add(curr);
                if(curr.left != null){
                    temp.add(curr.left);
                }
                if(curr.right != null){
                    temp.add(curr.right);
                }
                -- cnt;
            }
            for(int i = 0; i < temp.size() - 1; ++ i){
                temp.get(i).next = temp.get(i + 1);
            }
            temp.clear();
        }
        return root;
    }
```
FAILED. Passing solution with `O(1)` space:
```
    public Node connect(Node root){
        util(root);
        return root;
    }

    private void util(Node root){
        //base case
        if(root == null){
            return;
        }
        //set left
        if(root.left != null){
            root.left.next = root.right;
        }
        if(root.right != null){
            root.right.next = (root.next == null) ? null : root.next.left;
        }
        //preorder
        util(root.left);
        util(root.right);
    }
```