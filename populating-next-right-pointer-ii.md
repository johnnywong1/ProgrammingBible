# Populating Next Right Pointer in Each Node II
Passing Java Solution (iterative, move with `next` pointer):
```
public Node connect(Node root){
    Node head = null;
    Node last = null;
    Node curr = root;
    while(curr != null){
        while(curr != null){
            if(curr.left != null){
                if(last == null){
                    head = curr.left;
                }else{
                    last.next = curr.left;
                }
                last = curr.left;
            }
            if(curr.right != null){
                if(last == null){
                    head = curr.right;
                }else{
                    last.next = curr.right;
                }
                last = curr.right;
            }
            curr = curr.next;
        }
        curr = head;    //next tree level
        head = null;
        last = null;
    }
    return root;
}
```