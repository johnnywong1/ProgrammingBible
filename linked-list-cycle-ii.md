# Linked List Cycle II
Draft Java solution:
```
public ListNode detectCycle(ListNode head) {
    //return node where cycle starts (return index?)
    //dual pointer approach
    int result = 0;
    ListNode slow = head;
    ListNode fast = head.next;
    while(slow != fast){
        if(fast == null && fast.next == null){
            return null;    //no cycle in list
        }
        slow = slow.next;
        fast = fast.next.next;
        ++ result;
    }        
    return result;    //where cycle begins
}
```
FAILED. UNCLEAR PROBLEM DESCRIPTION
Correct solution:
```
/*
key: head to start + start to meeting point == size of loop
*/
public ListNode detectCycle(ListNode head){
    ListNode slow = head;
    ListNode fast = head;
    while(fast != null && fast.next != null){
        slow = slow.next;
        fast = fast.next.next;
        if(slow == fast){
            break;
        }
    }
    if(fast == null || fast.next == null){
        return null;
    }
    slow = head;
    while(slow != fast){
        slow = slow.next;
        fast = fast.next;
    }
    return fast;
}
```