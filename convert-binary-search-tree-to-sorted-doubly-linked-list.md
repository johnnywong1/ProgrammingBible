# Convert Binary Search Tree to Sorted Doubly Linked List
Draft Java solution:
```
    public Node treeToDoublyList(Node root) {
        //iterative inorder + stack approach
        Node head = null;
        Node prev = null;
        Stack<Node> stack = new Stack();
        stack.add(root);
        while(!stack.isEmpty() || curr != null){
            while(curr != null){
                stack.push(curr);
                curr = curr.left;
            }
            curr = stack.pop();
            prev = stack.peek();
            curr.right = prev;
            curr = curr.right;
            prev.right = ...
        }
    }
```
FAILED.

Passing solution:
```
    Node first = null;
    Node last = null;
    public Node treeToDoublyList(Node root){
        if(root == null){
            return null;
        }
        last.right = first;
        first.left = last;
        return first;
    }

    public void util(Node node){
        if(node != null){
            util(node.left);
            if(last != null){
                last.right = node;
                node.left = last;
            }else{
                first = node;
            }
            last = node;
            util(node.right);
        }
    }
```
Note: use global `first` and `last` to initialize them to `null` for the first recursion layer