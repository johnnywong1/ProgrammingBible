# Merge Two Sorted Array
https://leetcode.com/problems/merge-sorted-array
Naive solution, `O(n)` space:
```
    public static void merge(int[] nums1, int m, int[] nums2, int n) {
        //modify nums1 in-place
        //O(n) memory approach
        List<Integer> temp = new ArrayList<>();
        int ptr1 = 0;
        int ptr2 = 0;
        while(ptr1 < m && ptr2 < n){
            if(nums1[ptr1] < nums2[ptr2]){
                temp.add(nums1[ptr1]);
                ++ ptr1;
            }else{
                temp.add(nums2[ptr2]);
                ++ ptr2;
            }
        }
        if(ptr1 < m){
            for(int i = ptr1; i < m; ++ i){
                temp.add(nums1[i]);
            }
        }
        if(ptr2 < n){
            for(int i = ptr2; i < n; ++ i){
                temp.add(nums2[i]);
            }
        }
        //rewrite nums1
        for(int i = 0; i < m + n; ++ i){
            nums1[i] = temp.get(i);
        }
    }
```
`O(1)` space:
```
    public static void merge(int[] nums1, int m, int[] nums2, int n) {
        //modify nums1 in-place
        //O(1) space approach
        int ptr1 = m - 1;
        int ptr2 = n - 1;
        int ptr = m + n - 1;
        while(ptr1 >= 0 && ptr2 >= 0){
            nums1[ptr --] = (nums1[ptr1] > nums2[ptr2]) ? nums1[ptr1 --] : nums2[ptr2 --];
        }
        System.arraycopy(nums2, 0, nums1, 0, ptr2 + 1);
    }
```
Use Java collections sort function

```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        for(int i=m,j=0;i<nums1.length;i++,j++){
            nums1[i]=nums2[j]; //fill the empty part of nums1 with nums2, out of order
        }
        Arrays.sort(nums1); //call sort
    }
}
```

