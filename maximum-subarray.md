# Maximum Subarray
Draft Java solution:
```
public int maxSubArray(int[] nums) {
    //greedy
    //boundary: 0
    int result = Integer.MIN_VALUE;
    int currSum = nums[0];
    ...   
}
```
FAILED
Correct `O(n)` solution:
```
public int maxSubArray(int[] nums){
    int result = nums[0];
    int currSum = nums[0];
    for(int i = 1; i < nums.length; ++ i){
        currSum = Math.max(currSum + nums[i], nums[i]);
        result = Math.max(result, currSum);
    }
    return result;
}
``` 