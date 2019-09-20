# Merging K sorted Lists
https://leetcode.com/problems/merge-k-sorted-lists

## Solution
THis is considered a hard problem but its really easy if you use the right data structure  
Key is using a minheap, which is implemented in java using a priorityqueue  
Toss it all in there and take it out, which is sorted  
Linear runtime

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeKLists(ListNode[] lists) { 
        //minheap??? linear runtime
        PriorityQueue<Integer> mheap = new PriorityQueue<Integer>();
        for(ListNode node : lists){
            while(node!=null){
                mheap.add(node.val);
                node = node.next;
            }
        }
        
        ListNode dummy = new ListNode(0);
        ListNode head = dummy;
        while(!mheap.isEmpty()){
            ListNode temp = new ListNode(mheap.poll());
            head.next=temp;
            head = head.next;
        }
        
        
        return dummy.next;
    }
}
```
