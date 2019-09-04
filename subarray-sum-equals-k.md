# Subarray Sum Equals K
`O(n)` space + time approach (Map + prefix sum):
```
    public static int subarraySum(int[] nums, int k) {
        //O(n) space + time approach
        HashMap<Integer, Integer> map = new HashMap<>();    //key: subarray sum, value: number of sums
        int temp = 0;
        int result = 0;
        map.put(0, 1);
        for(int i = 0; i < nums.length; ++ i){
            temp += nums[i];
            if(map.containsKey(temp - k)){
                result += map.get(temp - k);
            }
            map.put(temp, map.getOrDefault(temp, 0) + 1);
        }
        return result;
    }
```