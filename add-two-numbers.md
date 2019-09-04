# Add Two Numbers
Java solution:
```
    public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        //in-place?
        ListNode dummy = new ListNode(-1);
        ListNode ptr = dummy;
        ListNode ptr1 = l1;
        ListNode ptr2 = l2;
        int overflow = 0;
        while(ptr1 != null && ptr2 != null){
            int tempSum = ptr1.val + ptr2.val + overflow;
            overflow = tempSum / 10;
            int temp = tempSum % 10;
            ptr.next = new ListNode(temp);
            //System.out.println(ptr.next.val);
            ptr1 = ptr1.next;
            ptr2 = ptr2.next;
            ptr = ptr.next;
        }
        while(ptr1 != null){
            int tempSum = ptr1.val + overflow;
            overflow = tempSum / 10;
            int temp = tempSum % 10;
            ptr.next = new ListNode(temp);
            ptr1 = ptr1.next;
            ptr = ptr.next;
        }
        while(ptr2 != null){
            int tempSum = ptr2.val + overflow;
            overflow = tempSum / 10;
            int temp = tempSum % 10;
            ptr.next = new ListNode(temp);
            ptr2 = ptr2.next;
            ptr = ptr.next;
        }
        if(overflow == 1){
            ptr.next = new ListNode(1);
        }
        return dummy.next;
    }
```