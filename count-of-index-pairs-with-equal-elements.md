# Count of Index Pairs with Equal Elements in an Array
Draft Java solution:
```
public static int count(int[] nums){
    //hash map approach
    int result = 0;
    if(nums.length == 0 || nums.length == 1){
        return result;
    }
    Map<Integer, Integer> map = new HashMap();  //key: nums[i], value: count
    for(Integer i : nums){
        map.put(i, map.getOrDefault(i, 0) + 1);
    }
    for(Integer i : map.keySet()){
        int count = map.get(i);
        result += (count * (count - 1)) / 2;
    }
    return result;
}
```
PASSED custom test cases (with edge cases)