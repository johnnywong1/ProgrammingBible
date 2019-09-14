# Merge Two Sorted Lists
https://leetcode.com/problems/merge-two-sorted-lists/submissions/

## Solution
Lots of conditionals,check value so that the resulting list is also sorted


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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode temp = new ListNode(-1);
        ListNode ans = temp;
        while(l1!=null || l2!=null){
            if(l1==null){
                while(l2!=null){
                temp.next = l2;
                temp=temp.next;
                l2=l2.next;
                }
            }
            else if(l2==null){
                while(l1!=null){
                temp.next = l1;
                temp=temp.next;
                l1=l1.next;
                }
            }
            else{
                if(l1.val<l2.val){
                    temp.next = l1;
                    temp=temp.next;
                    l1=l1.next;
                } else{
                    temp.next = l2;
                    temp=temp.next;
                    l2=l2.next;
                }
            }
        }
        return ans.next;
    }
}
```
