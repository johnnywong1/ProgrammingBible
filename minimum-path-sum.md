# Minimum Path Sum
```
    public int minPathSum(int[][] grid) {
        //Dynamic programming approach
        int[][] dp = new int[grid.length][grid[0].length];  //dp[i][j] minimum cost from top left to [i][j]

        //init
        int temp = grid[0][0];
        dp[0][0] = grid[0][0];
        for(int i = 1; i < grid[0].length; ++ i){
            temp += grid[0][i];
            dp[0][i] = temp;
        }
        temp = grid[0][0];
        for(int j = 1; j < grid.length; ++ j){
            temp += grid[j][0];
            dp[j][0] = temp;
        }

        //fill up dp mem
        for(int i = 1; i < grid.length; ++ i){
            for(int j = 1; j < grid[0].length; ++ j){
                dp[i][j] = Math.min(dp[i - 1][j] + grid[i][j], dp[i][j - 1] + grid[i][j]);
            }
        }

        return dp[grid.length - 1][grid[0].length - 1];
    }
```
PASSED with 2 attempts