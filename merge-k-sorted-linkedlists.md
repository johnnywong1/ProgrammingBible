# Merge K Sorted LinkedLists
Draft Java solution:
```
    public ListNode mergeKLists(ListNode[] lists) {

        //D & C approach

        if(lists.length == 0){
            return null;
        }
        if(lists.length == 1){
            return lists[0];
        }


        ListNode result = new ListNode(Integer.MIN_VALUE);
        int i = 0;
        //merge list two-by-two approach
        for(i = 0; i < lists.length; i += 2){
            if(i + 1 < lists.length){
                ListNode temp = mergeTwoLists(lists[i], lists[i + 1]);
                result = mergeTwoLists(temp, result);
            }
        }

        if(lists.length % 2 == 1){
            result = mergeTwoLists(lists[lists.length - 1], result);
        }
        
        return result.next; //final result;
    }

    //borrowed from merge two sorted lists
    private ListNode mergeTwoLists(ListNode l1, ListNode l2) {
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
PASSED with 7 attempts
