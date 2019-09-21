# Merge Sorted LinkedLists
Draft Java solution:
```
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode result = new ListNode(-1);
        ListNode ptr = result;
        ListNode ptr1 = l1;
        ListNode ptr2 = l2;
        while(ptr1 != null && ptr2 != null){
            if(ptr1.val > ptr2.val){
                ptr.next = new ListNode(ptr2.val);
                ptr2 = ptr2.next;
            }else{
                ptr.next = new ListNode(ptr1.val);
                ptr1 = ptr1.next;
            }
            ptr = ptr.next;
        }

        //clean up
        if(ptr1 != null){
            ptr.next = ptr1;
        }

        if(ptr2 != null){
            ptr.next = ptr2;
        }

        return result.next;
    }
```
PASSED with 2 attempts.