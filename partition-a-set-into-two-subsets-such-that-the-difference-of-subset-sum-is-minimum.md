# Partition a Set into Two Subsets such that the Difference of Subset Sum is Minimum
Draft Java solution:
```
public int partition(Set<Integer> s){
    //return minimum subset sum difference

}
```
FAILED. Passing solution for `Partition Equal Subset Sum`:
```
    public boolean canPartition(int[] nums) {
        //dynamic programming approach
        int sum = 0;
        for(Integer i : nums){
            sum += i;
        }
        if(sum % 2 != 0){
            return false;
        }
        boolean[][] dp = new boolean[nums.length + 1][sum + 1];  //dp[i][j] = j can be summed by taking elements from first i elements of nums
        //init
        for(int i = 0; i <= nums.length; ++ i){
            dp[i][0] = true;
        }
        for(int i = 1; i <= nums.length; ++ i){
            for(int j = 0; j <= sum; ++ j){
                //check
                if(nums[i - 1] > j){
                    //not including
                    dp[i][j] = dp[i - 1][j];
                }else{
                    dp[i][j] = dp[i - 1][j] || dp[i - 1][j - nums[i - 1]];
                }
            }
        }   
        return dp[nums.length][sum / 2];
    }
```
Note: check `nums[i - 1]` to avoid `IndexOutOfBound`