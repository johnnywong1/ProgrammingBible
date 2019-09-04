# Add Two Numbers II
Java approach (reversing list first)
```
    public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        //natural digit order
        //reverse first?
        ListNode l1Reversed = reverse(l1);
        ListNode l2Reversed = reverse(l2);
        ListNode ptr1 = l1Reversed;
        ListNode ptr2 = l2Reversed;
        ListNode dummy = new ListNode(-1);
        ListNode ptr = dummy;
        int overflow = 0;
        while(ptr1 != null || ptr2 != null){
            int a = ptr1 == null ? 0 : ptr1.val;
            int b = ptr2 == null ? 0 : ptr2.val;
            int tempSum = a + b + overflow;
            overflow = tempSum / 10;
            ptr.next = new ListNode(tempSum % 10);
            ptr = ptr.next;
            if(ptr1 != null){
                ptr1 = ptr1.next;
            }
            if(ptr2 != null){
                ptr2 = ptr2.next;
            }
        }
        //final overflow check
        if(overflow == 1){
            ptr.next = new ListNode(1);
        }
        return reverse(dummy.next);
    }

    public static ListNode reverse(ListNode head){
        ListNode curr = head;
        ListNode prev = null;
        while(curr != null){
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
```