# Union of Two Arrays (not on Leetcode)
Draft Java solution:
```
public List<Integer> findUnion(int[] nums1, int[] nums2){
    //Set approach
    List<Integer> result = new ArrayList();
    HashSet<Integer> set = new HashSet();
    for(Integer i : nums1){
        set.add(i);
    }
    for(Integer i : nums2){
        if(set.contains(i)){
            result.add(i);
        }
    }
    return result;
}
```
PASSED TESTS
