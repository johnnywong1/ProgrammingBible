#Populate Next Right Pointers in Each Node


```
class Solution {
    public Node connect(Node root) {
        //if root is null then stop
				if (root == null) {
            return root;
        }
				//if the root.left exists, then set the left node next equal to the right node
				//we don't have to check for the right because it is given that our tree is perfect binary
        if (root.left != null) {
            root.left.next = root.right;
						//if the current node has a next pointer, you can set the next pointer to bridge between subtrees
            if (root.next != null) {
								//get set the right child's next pointer equal to the left of the next of root
                root.right.next = root.next.left;
            }
        }
				//recurse
        connect(root.left);
        connect(root.right);
        return root;
    }
}
```
