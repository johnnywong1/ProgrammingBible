# Linked List Cycle
Draft Java solution (dual pointer, check for rings):
```
public boolean hasCycle(ListNode head) {
    //dual pointer approach
    //pre-process input
    if(head == null || head.next == null || head.next.next == null){
        return false;
    }
    ListNode fast = head;
    ListNode slow = head;
    while(fast != null && slow != null){
        if(fast == slow){
            return true;
        }
        fast = fast.next.next;
        slow = slow.next;
    }        
    return false;
}
```
FAILED (passed 15 / 17 test cases)
Passing solution:
```
public boolean hasCycle(ListNode head){
    if(head == null || head.next == null){
        return false;
    }
    ListNode slow = head;
    ListNode fast = head.next;
    while(slow != fast){
        if(fast == null || fast.next == null){
            return false;
        }
        slow = slow.next;
        fast = fast.next.next;
    }
    return true;
}
```